---
title: "Week 8 Worklog"
date: 2026-06-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 8 Objectives
> **Master AWS monitoring and automation services** by using **Amazon CloudWatch, EC2 Auto Scaling, and AWS CloudFormation**. Configure real-time monitoring and alerting, automatically scale EC2 instances based on workload, and create reusable infrastructure using **Infrastructure as Code (IaC)** with CloudFormation templates.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 05-01** (*Introduction to Amazon CloudWatch*) and **Module 05-02** (*CloudWatch Metrics, Alarms & Dashboards*). Take notes on important metric namespaces for **Amazon EC2**, **Amazon RDS**, and **Amazon S3**. | 08/06/2026 | 08/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 05-03** (*Amazon EC2 Auto Scaling*) and **Module 05-04** (*Advanced Elastic Load Balancing*). Learn the differences between **Target Tracking**, **Step Scaling**, and **Scheduled Scaling** policies. | 09/06/2026 | 09/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **Amazon CloudWatch Lab:**<br>• Create a **CloudWatch Dashboard** to monitor **CPU Utilization** and **Network In/Out** metrics for an EC2 instance.<br>• Configure a **CloudWatch Alarm** to send email notifications through **Amazon SNS** when CPU usage exceeds **70%**.<br>• Enable the **CloudWatch Logs Agent** to collect logs from the Apache web server. | 10/06/2026 | 10/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **Amazon EC2 Auto Scaling Lab:**<br>• Create a **Launch Template** for an EC2 web server.<br>• Create an **Auto Scaling Group (ASG)** with **minimum: 1**, **desired: 2**, and **maximum: 4** instances.<br>• Attach an **Application Load Balancer (ALB)** to the ASG and verify scale-out behavior using the `stress` tool. | 11/06/2026 | 11/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Watch **Module 05-05** (*AWS CloudFormation – Infrastructure as Code*).<br>• Write a **CloudFormation YAML template** to automatically provision a **VPC**, **Subnets**, and an **Amazon EC2** instance.<br>• Deploy the stack and verify that all resources are created correctly.<br>• Write and publish the **Week 8 Worklog** on the website. | 12/06/2026 | 12/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **An Amazon CloudWatch Dashboard** providing real-time monitoring of an EC2 instance with at least **four metrics** and **one Amazon SNS email alarm**.
> * [x] **An Amazon EC2 Auto Scaling Group** successfully scaling out when CPU utilization exceeds the configured threshold, verified through **CloudWatch metrics**.
> * [x] **An AWS CloudFormation stack** successfully provisioning the complete **VPC and Amazon EC2 infrastructure** with a single deployment.
> * [x] **Week 8 Worklog report** fully completed and successfully published on this website.