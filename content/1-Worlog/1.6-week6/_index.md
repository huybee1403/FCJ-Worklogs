---
title: "Week 6 Worklog"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 6 Objectives
> **Master AWS database services – Amazon RDS and Amazon DynamoDB** by understanding the differences between **relational databases (Amazon RDS)** and **NoSQL databases (Amazon DynamoDB)**. Gain hands-on experience creating and connecting to an **Amazon RDS for MySQL** instance, designing **DynamoDB** tables, and integrating both services with an application running on **Amazon EC2**.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 03-05** (*Introduction to Amazon RDS*) and **Module 03-06** (*Amazon RDS Multi-AZ Deployments & Read Replicas*). Create comparison notes for the database engines **MySQL**, **PostgreSQL**, and **Amazon Aurora**. | 25/05/2026 | 25/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 03-07** (*Introduction to Amazon DynamoDB*) and **Module 03-08** (*DynamoDB Partitions & Indexes*). Learn how to design efficient **Partition Keys** and **Sort Keys**. | 26/05/2026 | 26/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **Amazon RDS Lab:**<br>• Launch an **Amazon RDS for MySQL** instance (**db.t3.micro** – Free Tier eligible) in a **Private Subnet**.<br>• Configure the **Security Group** to allow connections from EC2 on **port 3306**.<br>• Connect from the EC2 instance using the **MySQL CLI**, then create a sample database and table. | 27/05/2026 | 27/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **Amazon DynamoDB Lab:**<br>• Create a **DynamoDB table** with **Partition Key:** `userId` and **Sort Key:** `timestamp`.<br>• Perform **PutItem**, **GetItem**, and **Query** operations using the **AWS CLI**.<br>• Create a **Global Secondary Index (GSI)** to improve query performance. | 28/05/2026 | 28/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Integrate **Amazon RDS** and **Amazon DynamoDB** with a web application running on **Amazon EC2**.<br>• Compare the use cases of relational and NoSQL databases through a practical exercise.<br>• Write and publish the **Week 6 Worklog** on the website. | 29/05/2026 | 29/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **An Amazon RDS for MySQL instance** successfully deployed in a **Private Subnet** and accessible from an **Amazon EC2** instance.
> * [x] **An Amazon DynamoDB table** with a **Global Secondary Index (GSI)** successfully created, with CRUD operations performed using the **AWS CLI**.
> * [x] **A three-tier architecture** (**Web on Amazon EC2 → Amazon RDS / Amazon DynamoDB**) successfully deployed and operating reliably.
> * [x] **Week 6 Worklog report** fully completed and successfully published on this website.