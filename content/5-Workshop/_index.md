---
title: "Workshop"
date: 2026-07-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

<div class="lms">

# WORKSHOP — Deploying an LMS System on AWS

This workshop provides a step-by-step guide to building the **LMS-Management-System** (an online learning management system) on AWS using a highly available architecture: users access it through **CloudFlare** and **AWS Amplify** (the interface), the backend runs on **EC2** behind an **Application Load Balancer** + **Auto Scaling Group**, data is stored in **Amazon DocumentDB** (Multi-AZ), and everything is monitored with **CloudWatch**, **CloudTrail**, with alerts delivered via **Amazon SNS**.

### 📚 Workshop content

* **5.1** — [Introduction](5.1-introduction/)
* **5.2** — [Network Infrastructure](5.2-network-infrastructure/)
* **5.3** — [Backend Deployment](5.3-backend/)
* **5.4** — [Domain & Frontend Configuration](5.4-domain-frontend/)
* **5.5** — [Load Balancing & Auto Scaling](5.5-loadbalancing-autoscaling/)
* **5.6** — [System Monitoring](5.6-monitoring/)
* **5.7** — [Resource Cleanup](5.7-cleanup/)

</div>
