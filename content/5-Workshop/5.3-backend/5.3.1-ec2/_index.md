---
title: "Launch EC2 Instance"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.3.1. </b> "
---

<div class="lms">

# Launch the backend EC2 instance

Create an EC2 instance to run the Node.js backend of the LMS system.

**Open the EC2 service → Launch an instance.**
![Navigate to the EC2 service](/images/Screenshot%202026-07-09%20225726.png)

**Set the name `LMS-BACKEND-EC2`, choose the Amazon Linux 2023 AMI, `t3.micro` type.**
![Set the name and choose the AMI, instance type](/images/Screenshot%202026-07-09%20225738.png)

**View the Amazon Linux 2023 AMI details (64-bit x86).**
![Amazon Linux 2023 AMI details](/images/Screenshot%202026-07-09%20225743.png)

**Choose the key pair `Khanh`, place the instance in VPC `LMS-VPC`, public subnet, and enable auto-assign public IP.**
![Choose the key pair and configure networking](/images/Screenshot%202026-07-09%20225800.png)

**Attach the existing security group `EC2-SG` and configure an 8 GiB gp3 volume.**
![Choose EC2-SG and configure storage](/images/Screenshot%202026-07-09%20225809.png)

**The instance launches successfully (Running) and has a public IP.**
![EC2 LMS-BACKEND-EC2 running](/images/Screenshot%202026-07-09%20225827.png)

</div>
