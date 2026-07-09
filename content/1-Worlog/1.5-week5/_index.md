---
title: "Week 5 Worklog"
date: 2026-05-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 5 Objectives
> **Master Amazon S3, AWS's object storage service**, by understanding **Storage Classes, Bucket Policies, Versioning, and Static Website Hosting**. Gain hands-on experience uploading and downloading data using both the **AWS Management Console** and **AWS CLI**, and integrate **Amazon S3** with **Amazon CloudFront** to accelerate content delivery.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 03-01** (*Introduction to Amazon S3*) and **Module 03-02** (*Amazon S3 Storage Classes*). Create comparison notes on the **cost** and **latency** of **S3 Standard**, **S3 Standard-Infrequent Access (Standard-IA)**, and **S3 Glacier**. | 18/05/2026 | 18/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 03-03** (*Amazon S3 Security: Bucket Policies & ACLs*) and **Module 03-04** (*Amazon S3 Versioning & Lifecycle Management*). Learn how to write **Bucket Policy** JSON documents to control access permissions. | 19/05/2026 | 19/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **Amazon S3 Lab – Part 1:**<br>• Create an **S3 bucket** with **Versioning** enabled.<br>• Upload files using both the **AWS Management Console** and **AWS CLI** (`aws s3 cp`, `aws s3 sync`).<br>• Configure a **Bucket Policy** to allow public read access. | 20/05/2026 | 20/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **Amazon S3 Lab – Part 2:**<br>• Enable **Static Website Hosting** and deploy a sample **HTML/CSS** website.<br>• Create an **Amazon CloudFront distribution** with the S3 bucket as the origin.<br>• Verify website accessibility and performance using the **CloudFront URL**. | 21/05/2026 | 21/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Configure an **S3 Lifecycle Policy** to automatically transition objects to **S3 Glacier** after **30 days**.<br>• Review and clean up AWS resources after completing the lab.<br>• Write and publish the **Week 5 Worklog** on the website. | 22/05/2026 | 22/05/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **An Amazon S3 bucket** successfully configured with **Versioning**, **Lifecycle Policies**, and **Bucket Policies**.
> * [x] **A static website** successfully deployed on **Amazon S3** and delivered through **Amazon CloudFront**, accessible from a web browser.
> * [x] **AWS CLI proficiency**, including effective use of the commands `aws s3 cp`, `aws s3 sync`, and `aws s3 ls`.
> * [x] **Week 5 Worklog report** fully completed and successfully published on this website.