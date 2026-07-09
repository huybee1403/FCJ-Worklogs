---
title: "Resource Cleanup"
date: 2026-07-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

<div class="lms">

After finishing, delete the resources to avoid incurring costs.

{{% notice warning %}}
Be sure to **delete resources in the correct dependency order** (ASG → ALB/Target group → EC2 → DocumentDB → VPC) to avoid errors. DocumentDB has *Deletion protection* enabled, so you must disable protection before deleting it.
{{% /notice %}}

**Delete AWS Amplify — the deployed frontend application.**
![Amplify application overview](/images/Screenshot%202026-07-09%20233448.png)

**Delete ACM — the SSL certificate in use.**
![ACM certificate overview](/images/Screenshot%202026-07-09%20233547.png)

**Delete DocumentDB — the active (Healthy) cluster.**
![DocumentDB cluster overview](/images/Screenshot%202026-07-09%20233627.png)

**Delete the running Auto Scaling Group.**
![Auto Scaling Group overview](/images/Screenshot%202026-07-09%20233709.png)

**Delete the Active Application Load Balancer.**
![Application Load Balancer overview](/images/Screenshot%202026-07-09%20233727.png)

**Select all EC2 → Instance state → Terminate (delete) instance.**
![Selecting instances to terminate](/images/Screenshot%202026-07-09%20233854.png)

**Confirm terminating all instances.**
![Confirm instance termination](/images/Screenshot%202026-07-09%20233859.png)

**Go to VPC → Actions → Delete VPC.**
![Selecting delete VPC](/images/Screenshot%202026-07-09%20234028.png)

**Type "delete" to confirm deleting the VPC along with its dependent resources (Internet Gateway, Route Table, Security Group, etc.).**
![Confirm VPC deletion](/images/Screenshot%202026-07-09%20234544.png)

---

## Conclusion

Through this workshop, the **LMS-Management-System** has been fully deployed on AWS with all layers in place: networking (VPC), security (Security Group, ACM), compute (EC2 + Auto Scaling), load balancing (ALB), database (DocumentDB Multi-AZ), frontend (Amplify), monitoring (CloudWatch, CloudTrail), and alerting (SNS). The architecture ensures **high availability**, **automatic scaling under load**, and **ease of monitoring**, making it suitable for a real-world online learning platform.

</div>
