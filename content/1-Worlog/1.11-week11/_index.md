---
title: "Week 11 Worklog"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 11 Objectives
> **Build the Capstone Project** by designing and deploying a complete web application on AWS that integrates the knowledge acquired throughout the bootcamp, including **Amazon VPC, Amazon EC2, Amazon RDS, Amazon S3, AWS IAM, Amazon CloudWatch, and CI/CD**. Prepare the system architecture documentation and presentation slides for the final project demonstration.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Design and draft the architecture for the Capstone Project.<br>• Define the project requirements, including the use of at least **five AWS services**.<br>• Create a detailed architecture diagram in **draw.io**, including data flow and IAM permission design. | 29/06/2026 | 29/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Build the core infrastructure using **AWS CloudFormation**:<br>• Deploy a **multi-AZ Amazon VPC**, **Public and Private Subnets**, an **Application Load Balancer (ALB)**, and an **Amazon EC2 Auto Scaling Group**.<br>• Create a **Multi-AZ Amazon RDS** database in a Private Subnet with automated backups enabled. | 30/06/2026 | 30/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | Develop the application backend:<br>• Deploy APIs using **AWS Lambda** and **Amazon API Gateway** integrated with **Amazon DynamoDB**.<br>• Configure **Amazon S3** and **Amazon CloudFront** for hosting the static frontend.<br>• Integrate **Amazon Cognito** for user authentication (login and registration). | 01/07/2026 | 01/07/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | Complete operations and security configuration:<br>• Create a comprehensive **Amazon CloudWatch Dashboard** for system monitoring.<br>• Configure **AWS WAF (Web Application Firewall)** to protect the API Gateway.<br>• Set up a **CI/CD pipeline** to automatically deploy the application whenever new code is pushed. | 02/07/2026 | 02/07/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Perform end-to-end system testing:<br>• Conduct load testing using **Apache JMeter** to verify that the Auto Scaling Group responds correctly under load.<br>• Perform a disaster recovery drill by deleting the **Amazon RDS** instance and restoring it from a snapshot.<br>• Write and publish the **Week 11 Worklog** on the website. | 03/07/2026 | 03/07/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **A complete Capstone architecture diagram** created in **draw.io**, illustrating all AWS services and their interactions.
> * [x] **A fully functional web application** running on AWS, including a **static frontend (Amazon S3 + Amazon CloudFront)**, **serverless backend (AWS Lambda + Amazon API Gateway)**, and **databases (Amazon RDS + Amazon DynamoDB)**.
> * [x] **A fully automated CI/CD pipeline**, **Amazon CloudWatch** monitoring, and **AWS WAF** protecting the entire application.
> * [x] **Load testing results** confirming that the Auto Scaling Group functions correctly and the system can handle **at least 100 requests per second**.
> * [x] **Week 11 Worklog report** fully completed and successfully published on this website.