---
title: "Blog 2"
date: 2026-04-20
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Securely Connect AWS DevOps Agent to Private Services in Your Amazon VPC

---

> [!IMPORTANT]
> ### 🎯 Article Objective
> This article explains how to configure a **Private Connection** that enables **AWS DevOps Agent** to securely access internal services running inside your Amazon VPC without exposing them to the public internet. This approach removes security barriers when integrating custom MCP servers, self-hosted observability platforms, and enterprise source code management systems.
>
> * **Original article:** [AWS Study Group](https://awsstudygroup.com/2026/04/20/ket-noi-an-toan-aws-devops-agent-voi-cac-dich-vu-rieng-tu-trong-vpc-cua-ban/)

---

## 1. Introducing AWS DevOps Agent

**AWS DevOps Agent** is an always-available operational assistant designed to:

* Resolve and **proactively prevent system issues** before they impact your workloads.
* **Optimize application reliability and performance** in real time.
* Execute **Site Reliability Engineering (SRE)** tasks across AWS, multi-cloud, and on-premises environments.
* Integrate with existing observability tools to correlate telemetry, source code, and deployment history, significantly **reducing Mean Time to Repair (MTTR)**.

Many organizations extend **AWS DevOps Agent** with custom **Model Context Protocol (MCP)** tools, allowing the agent to securely access internal resources such as:

* Private package repositories.
* Self-hosted observability platforms such as Grafana and Splunk.
* Internal documentation APIs.
* Enterprise source code management platforms such as **GitHub Enterprise** and **GitLab**.

The challenge is that these services typically run inside an **Amazon VPC** without public internet access, preventing AWS DevOps Agent from reaching them by default.

---

## 2. Solution: Private Connection

A **Private Connection** enables AWS DevOps Agent to securely connect its **Agent Space** to services running inside your VPC or private network **without exposing those services to the public internet**.

Private Connections support any integration that requires access to private endpoints, including:

* Custom **MCP Servers**.
* Self-hosted **Grafana** or **Splunk** instances.
* Internal source code management systems.

### How It Works

AWS DevOps Agent uses **Amazon VPC Lattice** to establish a secure, private communication path. Amazon VPC Lattice is an application networking service that enables you to connect, secure, and monitor communication between applications across multiple VPCs, AWS accounts, and compute environments **without managing the underlying networking infrastructure**.

When you create a Private Connection, the following sequence occurs:

1. You specify the **VPC**, **subnets**, and optionally the **security groups** that have network connectivity to the target service.
2. AWS DevOps Agent creates a **service-managed Resource Gateway** and provisions **Elastic Network Interfaces (ENIs)** within the selected subnets.
3. The agent uses the Resource Gateway to **route traffic** to the target service using either its private IP address or DNS name through a private networking path.

> The Resource Gateway is fully managed by AWS DevOps Agent and appears as a **read-only resource** in your AWS account. You do not need to configure or maintain it. The provisioned ENIs **do not accept inbound traffic from the public internet**, and you retain full control over traffic by using your own security groups.

---

## 3. Overall Architecture

![AWS DevOps Agent Private Connection Architecture](/images/devops_agent_private_connection.png)

### End-to-End Workflow

| Step | Component | Description |
| :---: | :--- | :--- |
| **1** | **AWS DevOps Agent → Amazon VPC Lattice** | The agent initiates a request and routes it through Amazon VPC Lattice. |
| **2** | **Amazon VPC Lattice → Resource Gateway** | Amazon VPC Lattice forwards the request to the service-managed Resource Gateway deployed inside the customer VPC. |
| **3** | **Resource Gateway → ENIs (via IP/DNS)** | The Resource Gateway routes traffic to the ENIs within the Resource Gateway subnets using private IP addresses or DNS names. |
| **4** | **ENIs → Application (VPC or On-Premises)** | The ENIs forward the request to the target application running inside the VPC or connected private network, protected by security groups. |

*From the perspective of the destination service, requests originate from the **private IP addresses of the ENIs** within your VPC, ensuring that traffic never traverses the public internet.*

---

## 4. Security Layers

> [!TIP]
> ### 🔐 Defense in Depth
>
> The Private Connection architecture provides **five layers of security**:
>
> 1. **No Public Internet Exposure** – All communication between AWS DevOps Agent and the destination service remains entirely within the **AWS private network**. Your services never require public IP addresses or an Internet Gateway.
>
> 2. **Service-Managed Read-Only Resource Gateway** – The Resource Gateway is read-only within your AWS account and **can only be used by AWS DevOps Agent**. No other AWS service or IAM principal can route traffic through it. All actions are fully recorded in **AWS CloudTrail**.
>
> 3. **Customer-Controlled Security Groups** – Traffic from AWS DevOps Agent follows the **outbound rules** of the security groups attached to the Resource Gateway ENIs and the **inbound rules** of your destination service, giving you complete network access control.
>
> 4. **Least-Privilege Service-Linked Role** – AWS DevOps Agent operates using a tightly scoped service-linked role that can access only resources tagged with `AWSAIDevOpsManaged`. It **cannot access any other resources** in your AWS account.
>
> 5. **DNS Support** – Target services can be referenced using DNS names. Note that these DNS names must be **publicly resolvable**.
```
