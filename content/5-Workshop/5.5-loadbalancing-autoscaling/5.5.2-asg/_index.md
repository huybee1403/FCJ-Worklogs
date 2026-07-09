---
title: "Auto Scaling Group"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 5.5.2. </b> "
---

<div class="lms">

# Create an Auto Scaling Group

Automatically increase/decrease the number of EC2 instances based on load, keeping the system always available.

**Create the `LMS-ASG-TLP` Auto Scaling group, choose the `LMS-TPL` launch template.**
![Create the Auto Scaling group and choose the launch template](/images/Screenshot%202026-07-09%20232313.png)

**Review the launch template details (AMI, t3.micro, key pair, security group).**
![Launch template details](/images/Screenshot%202026-07-09%20232319.png)

**Choose the `LMS-VPC` VPC.**
![Choose the VPC for the ASG](/images/Screenshot%202026-07-09%20232345.png)

**Select 2 public subnets, "Balanced best effort" distribution.**
![Choose subnets for the ASG](/images/Screenshot%202026-07-09%20232351.png)

**Attach the ASG to the existing ALB — choose the `backend-tg` target group.**
![Attach the ASG to the ALB's target group](/images/Screenshot%202026-07-09%20232400.png)

**Enable the ELB health check.**
![Configure the health check (1)](/images/Screenshot%202026-07-09%20232411.png)

**Set the startup grace period to 300 seconds.**
![Configure the health check (2)](/images/Screenshot%202026-07-09%20232415.png)

**Configure capacity: Desired 2, Min 2, Max 4.**
![Configure the number of instances](/images/Screenshot%202026-07-09%20232429.png)

**Choose "No scaling policies" (or add a policy as needed).**
![Configure the scaling policy](/images/Screenshot%202026-07-09%20232433.png)

**Enable group metrics collection (CloudWatch group metrics).**
![Enable metrics collection for CloudWatch](/images/Screenshot%202026-07-09%20232441.png)

**Add notifications via SNS to the admin email (all Launch/Terminate events...).**
![Configure SNS notifications](/images/Screenshot%202026-07-09%20232459.png)

**Skip tags (optional).**
![Add tags step](/images/Screenshot%202026-07-09%20232513.png)

**Review everything and create the Auto Scaling group.**
![Review and create the ASG](/images/Screenshot%202026-07-09%20232522.png)

</div>
