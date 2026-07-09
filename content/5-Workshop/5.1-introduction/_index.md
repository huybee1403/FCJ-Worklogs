---
title: "Introduction"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

<div class="lms">

# Introduction

A workshop on building the **LMS-Management-System** — a complete online learning management system on AWS using a **High Availability** architecture. Users access it through **CloudFlare** and a web interface hosted on **AWS Amplify**; the Node.js backend runs on **EC2** behind an **Application Load Balancer** combined with an **Auto Scaling Group** spread across 2 availability zones; data is stored in **Amazon DocumentDB** (Multi-AZ); and the system is monitored with **CloudWatch**, **CloudTrail**, with alerts delivered via **Amazon SNS**.

### 🧾 Project information used in this workshop

| Item | Value |
|---|---|
| Region | US East (N. Virginia) — `us-east-1` |
| VPC | `LMS-VPC` — `10.0.0.0/16` (2 AZ, 2 public + 2 private subnets) |
| Backend | Node.js running on EC2, port `8080`, managed with PM2 |
| Source code | `github.com/huybee1403/LMS_System_MongoDB` |
| Database | Amazon DocumentDB 5.0 (`db.t3.medium`, Multi-AZ) |
| Domain | `fixing404.win` (API: `api.fixing404.win`) |

{{% notice note %}}
**Prerequisites:** An AWS account, a domain managed with CloudFlare, an EC2 key pair (here `Khanh.pem`), and the LMS source code on GitHub (frontend + backend as a monorepo).
{{% /notice %}}

![Overall architecture of the LMS system on AWS](/images/742208320_1712520913220808_2976852082227510005_n.png)

</div>
