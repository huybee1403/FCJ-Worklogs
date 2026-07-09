---
title: "DNS & SSL Certificate"
date: 2026-07-01
weight: 1
chapter: false
pre: " <b> 5.4.1. </b> "
---

<div class="lms">

# Configure DNS (CloudFlare) and SSL Certificate (ACM)

Point the domain to the ALB and issue an HTTPS certificate for the API.

**In CloudFlare, create a CNAME record `api.fixing404.win` pointing to the ALB's DNS name.**
![Create a CNAME record in CloudFlare](/images/Screenshot%202026-07-09%20230654.png)

**Open AWS Certificate Manager (ACM).**
![Navigate to ACM](/images/Screenshot%202026-07-09%20230713.png)

**Select "Request a public certificate".**
![Request a public certificate](/images/Screenshot%202026-07-09%20230901.png)

**Enter the domain name `api.fixing404.win` and choose the DNS validation method.**
![Enter the domain and choose DNS validation](/images/Screenshot%202026-07-09%20230927.png)

**Choose the RSA 2048 key algorithm.**
![Choose the RSA 2048 key algorithm](/images/Screenshot%202026-07-09%20230934.png)

**Submit the request.**
![Submit the certificate request](/images/Screenshot%202026-07-09%20230938.png)

**After adding the validation CNAME record in CloudFlare, the certificate moves to the Issued state.**
![Certificate has been Issued](/images/Screenshot%202026-07-09%20230949.png)

</div>
