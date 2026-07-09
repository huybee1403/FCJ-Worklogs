---
title: "Create Security Groups"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 5.2.2. </b> "
---

<div class="lms">

# Create the Security Groups

Create 3 security groups corresponding to 3 layers: load balancing, the application server, and the database.

**`ALB-SG`: open HTTP (80) and HTTPS (443) ports from the Internet.**
![Security group ALB-SG](/images/Screenshot%202026-07-09%20225627.png)

**`DocumentDB-SG`: open port `27017` (the DocumentDB/MongoDB port) for the data layer.**
![Security group DocumentDB-SG](/images/Screenshot%202026-07-09%20225635.png)

**`EC2-SG`: open the necessary ports — SSH (22), HTTP (80), HTTPS (443) and the application (8080).**
![Security group EC2-SG](/images/Screenshot%202026-07-09%20225643.png)

</div>
