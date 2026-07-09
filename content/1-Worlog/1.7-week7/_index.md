---
title: "Week 7 Worklog"
date: 2026-06-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 7 Objectives
> **Master AWS Identity and Access Management (IAM)** by understanding **Users, Groups, Roles, Policies**, and the **Principle of Least Privilege**. Gain hands-on experience configuring fine-grained permissions for AWS services, enabling **Multi-Factor Authentication (MFA)**, and implementing a layered security strategy for your AWS account.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 04-01** (*Introduction to AWS IAM*) and **Module 04-02** (*Users, Groups & Policies*). Take notes on the differences between **identity-based policies** and **resource-based policies**. | 01/06/2026 | 01/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 04-03** (*IAM Roles & Instance Profiles*) and **Module 04-04** (*AWS Organizations & Service Control Policies (SCPs)*). Learn how an **Amazon EC2** instance can use an **IAM Role** to access the **Amazon S3 API** without storing access keys. | 02/06/2026 | 02/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **AWS IAM Lab – Part 1:**<br>• Create a new **IAM User** and add it to the `Developers` group.<br>• Write a custom **IAM Policy** in JSON that grants **read-only access to Amazon S3**.<br>• Enable **MFA** for the IAM user using **Google Authenticator**. | 03/06/2026 | 03/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **AWS IAM Lab – Part 2:**<br>• Create an **IAM Role** for **Amazon EC2** with permissions to write to **Amazon S3** and read from **Amazon DynamoDB**.<br>• Attach the role to an EC2 instance and verify the assigned permissions using the **AWS CLI** (`aws sts get-caller-identity`).<br>• Use **IAM Access Analyzer** to identify and review excessive permissions. | 04/06/2026 | 04/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Explore **AWS Security Hub** and **Amazon GuardDuty** for security monitoring and threat detection.<br>• Review the **IAM Credential Report** and remediate any identified security risks.<br>• Write and publish the **Week 7 Worklog** on the website. | 05/06/2026 | 05/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **An AWS IAM permission model** implemented according to the **Principle of Least Privilege**, including **Users, Groups, Roles, and custom IAM Policies**.
> * [x] **MFA enabled** for all critical IAM users to strengthen account security.
> * [x] **Amazon EC2** successfully using an **IAM Role** to access **Amazon S3** and **Amazon DynamoDB** without storing access keys.
> * [x] **IAM Access Analyzer** confirms that no unintended external access has been detected.
> * [x] **Week 7 Worklog report** fully completed and successfully published on this website.