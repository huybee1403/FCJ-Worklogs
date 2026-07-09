---
title: "Create VPC"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.2.1. </b> "
---

<div class="lms">

# Create the VPC and Network Infrastructure

Create a virtual private cloud as the foundation for the entire system, comprising 2 availability zones to ensure high availability.

**Open the VPC service → click Create VPC.**
![VPC service overview page](/images/Screenshot%202026-07-09%20225444.png)

**Select "VPC and more", name it `LMS-VPC`, and set the IPv4 CIDR block to `10.0.0.0/16`.**
![Configuring the name and CIDR for the VPC](/images/Screenshot%202026-07-09%20225512.png)

**Select 2 Availability Zones, 2 public subnets and 2 private subnets, NAT gateway = None.**
![Configuring the number of availability zones and subnets](/images/Screenshot%202026-07-09%20225520.png)

**Enable the VPC endpoint for S3 (Gateway) and enable DNS hostnames / DNS resolution, then Create VPC.**
![Configuring the VPC endpoint and DNS](/images/Screenshot%202026-07-09%20225524.png)

**The VPC is created successfully (status Available).**
![The LMS-VPC has been created](/images/Screenshot%202026-07-09%20225533.png)

**Go to the Subnets section to edit the public subnets.**
![List of the VPC's 4 subnets](/images/Screenshot%202026-07-09%20225541.png)

**Enable "Enable auto-assign public IPv4 address" for the public subnets (so EC2 instances receive a public IP).**
![Enabling auto-assign public IP for the public subnets](/images/Screenshot%202026-07-09%20225547.png)

</div>
