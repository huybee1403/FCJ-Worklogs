---
title: "Target Group & Load Balancer"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.5.1. </b> "
---

<div class="lms">

# Create a Target Group and Application Load Balancer

Create a load balancer that distributes traffic to the backend.

**Create a Target group of type Instances, named `backend-tg`.**
![Create target group backend-tg](/images/Screenshot%202026-07-09%20231910.png)

**Configure the HTTP protocol, port `8080`, in the `LMS-VPC` VPC.**
![Configure protocol and port for the target group](/images/Screenshot%202026-07-09%20231930.png)

**Configure the health check with the HTTP protocol, path `/`.**
![Configure the health check](/images/Screenshot%202026-07-09%20231940.png)

**Proceed to the register targets step.**
![Move on to register targets](/images/Screenshot%202026-07-09%20231945.png)

**Select the `LMS-BACKEND-EC2` instance, port 8080.**
![Select the instance to register](/images/Screenshot%202026-07-09%20232017.png)

**The instance is added to the targets list.**
![Instance added as a target](/images/Screenshot%202026-07-09%20232026.png)

**Review and create the target group.**
![Review and create the target group](/images/Screenshot%202026-07-09%20232036.png)

**The `backend-tg` target group has been created (healthy status).**
![Target group created successfully](/images/Screenshot%202026-07-09%20232113.png)

**Start creating the Load Balancer — choose the Application Load Balancer type.**
![Compare and choose the Load Balancer type](/images/Screenshot%202026-07-09%20232130.png)

**Name it `LMS-BACKEND-ALB`, Internet-facing scheme, IPv4.**
![Basic configuration of the ALB](/images/Screenshot%202026-07-09%20232144.png)

**Network mapping: select 2 public subnets (us-east-1a and us-east-1b).**
![Configure network mapping for the ALB](/images/Screenshot%202026-07-09%20232202.png)

**Attach the `ALB-SG` security group and create an HTTP:80 listener.**
![Configure security group and listener](/images/Screenshot%202026-07-09%20232214.png)

**Set the listener's default action to forward to `backend-tg`.**
![Configure forward to the target group](/images/Screenshot%202026-07-09%20232225.png)

**Review the entire configuration (1).**
![Review the ALB configuration (1)](/images/Screenshot%202026-07-09%20232232.png)

**Review and click Create load balancer (2).**
![Review the ALB configuration (2)](/images/Screenshot%202026-07-09%20232236.png)

**The `LMS-BACKEND-ALB` ALB is now Active.**
![ALB is up and running](/images/Screenshot%202026-07-09%20232242.png)

</div>
