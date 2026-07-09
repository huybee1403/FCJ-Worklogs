---
title: "Week 3 Worklog"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 3 Objectives
> **Master the concepts in Module 02 on Amazon EC2**: understand EC2 instance types, Amazon Machine Images (AMIs), Security Groups, and gain hands-on experience launching virtual servers in the cloud; successfully connect via SSH and deploy a simple static web application.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 02-01** (*Introduction to Amazon EC2*) and **Module 02-02** (*EC2 Instance Types & Pricing*). Take notes on the **t2**, **t3**, and **m5** instance families and their common use cases. | 04/05/2026 | 04/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 02-03** (*AMI & Launch Templates*) and **Module 02-04** (*Security Groups & Key Pairs*). Learn the differences between **public and private keys** and how to securely configure network ports. | 05/05/2026 | 05/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **EC2 Lab – Part 1:**<br>• Launch an EC2 instance (**Amazon Linux 2**, **t2.micro** – Free Tier eligible).<br>• Create and download a **Key Pair (.pem)**.<br>• Configure a **Security Group** to allow ports **22 (SSH)** and **80 (HTTP)**. | 06/05/2026 | 06/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **EC2 Lab – Part 2:**<br>• Connect to the EC2 instance via **SSH** from your local computer.<br>• Install the **Apache HTTP Server (httpd)**.<br>• Deploy a simple HTML page and access it through the instance's **Public IP address**. | 07/05/2026 | 07/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Learn about **Elastic IP** (static public IP) and **Amazon EBS Volumes** (block storage).<br>• Attach an EBS volume to the EC2 instance, mount it, and store data.<br>• Write and publish the **Week 3 Worklog** on the website. | 08/05/2026 | 08/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **An EC2 instance** successfully running within the AWS Free Tier, configured with an appropriate Security Group.
> * [x] **Successful SSH connection** established from a local computer to the EC2 instance.
> * [x] **Apache HTTP Server** installed and a sample HTML page accessible through the instance's **Public IP address**.
> * [x] **Amazon EBS Volume** successfully attached, mounted, and used for data storage.
> * [x] **Week 3 Worklog report** fully completed and successfully published on this website.