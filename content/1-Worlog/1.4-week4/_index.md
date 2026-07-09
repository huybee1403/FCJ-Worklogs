---
title: "Week 4 Worklog"
date: 2026-05-11
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 4 Objectives
> **Master AWS networking with Amazon VPC** by understanding virtual network architecture, including **Public and Private Subnets, Route Tables, Internet Gateways, and NAT Gateways**. Design and deploy a complete **multi-tier VPC architecture** using the AWS Management Console.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 02-05** (*Introduction to Amazon VPC*) and **Module 02-06** (*Subnets, Route Tables, and Internet Gateways*). Draw a **two-tier VPC architecture** consisting of a **Public Subnet** and a **Private Subnet**. | 11/05/2026 | 11/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 02-07** (*NAT Gateway & Security*) and **Module 02-08** (*VPC Peering & Endpoints*). Learn the differences between **Security Groups** and **Network ACLs**. | 12/05/2026 | 12/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **Amazon VPC Lab – Part 1:**<br>• Create a custom **VPC** with the CIDR block **10.0.0.0/16**.<br>• Create a **Public Subnet** (**10.0.1.0/24**) and a **Private Subnet** (**10.0.2.0/24**).<br>• Attach an **Internet Gateway** and configure the **Route Table** for the Public Subnet. | 13/05/2026 | 13/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **Amazon VPC Lab – Part 2:**<br>• Create a **NAT Gateway** to provide internet access for resources in the Private Subnet.<br>• Deploy one **EC2 instance** in the Public Subnet (web server) and another in the Private Subnet (backend server).<br>• Verify communication between the two tiers using **Security Groups**. | 14/05/2026 | 14/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Learn the fundamentals of **Application Load Balancer (ALB)**.<br>• Create an **ALB** to distribute incoming traffic across two EC2 instances.<br>• Write and publish the **Week 4 Worklog** on the website. | 15/05/2026 | 15/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **A fully functional Amazon VPC architecture** with **Public and Private Subnets**, an **Internet Gateway**, and a **NAT Gateway**.
> * [x] **A draw.io network architecture diagram** illustrating the traffic flow from **Internet → Application Load Balancer → Public EC2 → Private EC2**.
> * [x] **An Application Load Balancer (ALB)** successfully distributing traffic across two EC2 instances.
> * [x] **Week 4 Worklog report** fully completed and successfully published on this website.