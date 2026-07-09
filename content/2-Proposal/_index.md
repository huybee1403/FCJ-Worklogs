---
title: "Proposal"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

<style>
.lms h1{font-size:2.1rem;margin-bottom:.2rem;color:#1c252e}
.lms h2{font-size:1.15rem;font-weight:500;color:#566c88;margin-top:.2rem;border:0;padding:0}
.lms h3{margin-top:2.2rem;padding:.45rem 0 .45rem .9rem;border-left:5px solid #ff9900;color:#233a57;font-size:1.35rem;background:linear-gradient(90deg,rgba(255,153,0,.09),transparent 70%);border-radius:0 6px 6px 0}
.lms p em:only-child{display:inline-block;margin:1rem 0 .35rem;color:#233a57;font-style:normal;font-weight:700;font-size:1.02rem;border-bottom:2px solid #ff9900;padding-bottom:2px}
.lms table{width:100%;border-collapse:collapse;margin:1.1rem 0;font-size:.95rem;box-shadow:0 1px 4px rgba(28,37,46,.1);border-radius:8px;overflow:hidden}
.lms thead th{background:#233a57;color:#fff;font-weight:600;text-align:left;padding:.6rem .8rem}
.lms tbody td{padding:.55rem .8rem;border-top:1px solid #e6ebf2}
.lms tbody tr:nth-child(even){background:#f7f9fc}
.lms tbody tr:last-child{background:rgba(255,153,0,.13);font-weight:600}
.lms img{border-radius:10px;box-shadow:0 4px 14px rgba(28,37,46,.15);border:1px solid #e6ebf2;margin:1.2rem auto;display:block;max-width:100%}
.lms blockquote{border-left:4px solid #ff9900;background:#fff8ef;border-radius:0 8px 8px 0;padding:.7rem 1rem;color:#4a3b23;margin:1.2rem 0}
.lms ul li::marker{color:#ff9900}
.lms ol li::marker{color:#ff9900;font-weight:700}
</style>

<div class="lms">

# LMS-Management-System
## AWS-powered Online Learning Management System with High Availability Infrastructure Architecture

### 1. Executive Summary
LMS-Management-System is an online Learning Management System built to provide a centralized platform for course organization, user management, content delivery, and learning progress tracking. The system is deployed on AWS following a High Availability infrastructure model, leveraging an Application Load Balancer combined with an Auto Scaling Group distributed across two Availability Zones to ensure uninterrupted service even if an entire zone encounters an outage. The web frontend is hosted on AWS Amplify and resolved via CloudFlare, while application data is securely stored in Amazon DocumentDB with Multi-AZ replication. The entire infrastructure is continuously monitored using CloudWatch, CloudTrail, and alerted via Amazon SNS, ensuring stable operations and seamless scalability.

### 2. Problem Statement
*Current Challenges*

Contemporary online teaching and learning processes are often fragmented across multiple disconnected tools (emails, shared drives, chat applications), making it difficult to efficiently manage courses, materials, and track student progress. Commercial LMS platforms typically demand high licensing fees, offer limited customization, and restrict data ownership. Furthermore, self-hosted systems deployed on single servers are highly vulnerable to service disruptions during traffic spikes or hardware failures.

*The Solution*

The proposed system implements a standard three-tier web architecture on AWS. The frontend interface is a web application hosted by AWS Amplify, with domain resolution and security protection handled through CloudFlare, utilizing SSL/TLS certificates issued by AWS Certificate Manager. User traffic flows through the Internet Gateway to an Application Load Balancer (ALB), which dynamically distributes requests to EC2 instances managed under an Auto Scaling Group across two Availability Zones. Application data is persisted within Amazon DocumentDB instances isolated inside private subnets with Multi-AZ replication enabled. Amazon CloudWatch aggregates system metrics and logs to trigger Amazon SNS email alerts during anomalies, while AWS CloudTrail logs all account activities for security and compliance auditing. Similar to widely adopted LMS solutions like Moodle or Canvas, this platform facilitates course creation, student enrollment, and resource management, yet remains lightweight, data-independent, and optimized for the team's specific deployment scale.

*Benefits and Return on Investment (ROI)*

This solution offers a centralized, data-independent learning platform capable of scaling dynamically based on real-time demand. By adopting Auto Scaling and a Multi-AZ architecture, the system guarantees high availability while minimizing costs through a pay-as-you-go pricing model, bypassing heavy upfront capital investments for software licenses or physical hardware. Consolidating materials, courses, and student records significantly cuts down manual administrative overhead, establishing a robust foundation to incorporate advanced capabilities such as online examinations, learning analytics, or AI integrations. The estimated payback period spans between 6 to 12 months, driven by reduced licensing costs and operational efficiencies.

### 3. Solution Architecture
The system employs a High Availability infrastructure design wrapped within an Amazon VPC. Users gain access via CloudFlare and the Internet Gateway, where incoming traffic is routed by an Application Load Balancer to EC2 backend instances inside an Auto Scaling Group situated across public subnets in two distinct Availability Zones. The data layer features Amazon DocumentDB deployed across private subnets with Multi-AZ replication to ensure fault tolerance and data durability. The web presentation layer is hosted on AWS Amplify, securely wrapped with SSL/TLS protection from AWS Certificate Manager. CloudWatch, CloudTrail, and SNS oversee the monitoring, logging, and alerting layers.

![LMS Management System Architecture](/images/742208320_1712520913220808_2976852082227510005_n.png)

*AWS Services Utilized*
- *CloudFlare*: DNS resolution and edge layer security/protection for the domain.
- *AWS Amplify*: Hosting and content delivery for the web application (frontend user interface).
- *AWS Certificate Manager*: Automated SSL/TLS certificate provisioning and management.
- *Internet Gateway*: Edge gateway routing traffic between the public Internet and the VPC.
- *Application Load Balancer (ALB)*: Secure HTTPS traffic routing and distribution to EC2 instances.
- *Auto Scaling Group*: Automated horizontal scaling of EC2 instances across 2 Availability Zones based on demand.
- *Amazon EC2*: Compute instances running the core LMS backend application (positioned in public subnets).
- *Amazon DocumentDB*: Fully managed document database cluster (private subnets) with Multi-AZ replication.
- *Amazon CloudWatch*: Infrastructure metric tracking, log aggregation, and alarm dispatching.
- *AWS CloudTrail*: Management event tracking for comprehensive account auditing and compliance.
- *Amazon SNS*: Notification broker for dispatching critical system alerts to administrator emails.

*Component Design*
- *Resolution & Security Layer*: CloudFlare manages incoming DNS queries, while Certificate Manager provides SSL/TLS certificates to mandate secure HTTPS connections (Port 443).
- *Presentation Layer*: AWS Amplify acts as the hosting engine for user-facing and instructor-facing web layouts.
- *Compute & Load Balancing Layer*: The ALB catches incoming requests and proxies them downstream to active EC2 instances within the Auto Scaling Group across two public subnets, ensuring seamless scaling and fault resilience.
- *Data Layer*: Amazon DocumentDB operates within private subnets to store course structures, profile records, and learning paths under a robust Multi-AZ configuration.
- *Monitoring & Alerting Layer*: EC2 telemetry and software logs are shipped to CloudWatch; if any predetermined thresholds are breached, CloudWatch Alarms are tripped, firing email dispatches via SNS to system admins. CloudTrail records all active API operations.

### 4. Technical Implementation
*Phases of Deployment*

The project lifecycle is structured across 4 key phases:
1. *Architecture Research & Design*: Evaluating target AWS components (VPC, ALB, Auto Scaling, DocumentDB, Amplify) and mapping out the infrastructure blueprint (1 month prior to the internship).
2. *Financial Evaluation & Feasibility Study*: Employing the AWS Pricing Calculator to model operational costs and validate capacity constraints (Month 1).
3. *Architectural Optimization for Cost & Performance*: Refining EC2 instance sizing, tweaking Auto Scaling rules, and tuning DocumentDB cluster settings to balance performance against financial boundaries (Month 2).
4. *Development, Testing, & Full Deployment*: Developing the core LMS software codebases (frontend and backend), structuring infrastructure as code using AWS CDK/CloudFormation, executing load tests, and pushing the system live (Months 2–3).

*Technical Prerequisites*
- *Network Layer*: An Amazon VPC configured with public and private subnets mapped over two Availability Zones, integrated with an Internet Gateway, optimized route tables, and strict Security Groups.
- *Application Layer*: Core backend compute running on EC2 instances (e.g., t3.small/t3.medium) encapsulated inside an Auto Scaling Group sitting behind the ALB. The web application frontend is mapped to AWS Amplify.
- *Data Layer*: An Amazon DocumentDB cluster operating in a Multi-AZ topology to guarantee high availability and automated backup schedules.
- *Security & Observability*: Validated SSL/TLS encryption through Certificate Manager, active monitoring via CloudWatch, transaction logging through CloudTrail, and event notification handling via SNS. Infrastructure deployment is mandated via AWS CDK/CloudFormation to maintain Infrastructure as Code (IaC) standards.

### 5. Roadmap & Key Milestones
- *Pre-internship (Month 0)*: 1 month dedicated to researching AWS service deep-dives and creating structural infrastructure drafts.
- *Internship Phase (Months 1–3)*:
    - Month 1: Getting acclimated with AWS, configuring the base VPC, and setting up core networking blocks.
    - Month 2: Architecture refining, cost optimization adjustments, and core application development.
    - Month 3: Rigorous system testing, continuous deployment workflows, and final production launch.
- *Post-deployment Operations*: Continuous operational oversight, infrastructure cost management, and progressive feature updates spanning a 1-year timeline.

### 6. Budget Estimation
Detailed financial estimates can be audited directly on the [AWS Pricing Calculator](https://calculator.aws/#/) (please map your shared architectural link here).  
Alternatively, download the [Budget Estimation Report PDF](../attachments/budget_estimation.pdf).

*Infrastructure Costs (High Availability Configuration — Multi-AZ)*

Projections are calculated based on benchmark rates in the **US East (N. Virginia — us-east-1)** region, running continuously 24/7 (730 hours/month).

| Service | Assumed Configuration | Unit Price Reference | Cost/Month (USD) |
|---|---|---|---|
| Amazon EC2 | 2 × `t3.medium` (2 AZs, On-Demand) | $0.0416/hour | 60.74 |
| Application Load Balancer | 1 ALB + minimal traffic bandwidth (~1 LCU) | $0.0225/hour + LCU | 22.27 |
| Amazon DocumentDB | 2 × `db.t3.medium` (Multi-AZ) + 10 GB Storage | $0.078/hour + $0.10/GB | 114.88 |
| Amazon DocumentDB I/O | ~10 Million I/O Requests | $0.20/Million | 2.00 |
| AWS Amplify | Hosting + build execution + low data transfer | Pay-per-use | 3.00 |
| Amazon CloudWatch | Standard metrics, logs, and basic alarms | Pay-per-use | 4.00 |
| AWS CloudTrail | 1 active trail (management events) | Free Tier eligible | 0.00 |
| Amazon SNS | Automated Email Alerts (< 1,000 dispatches) | Free Tier eligible | 0.00 |
| Data Transfer Out | ~10 GB/month (well within the 100 GB Free Tier) | $0.09/GB (post free tier) | 0.00 |
| CloudFlare / Certificate Manager | DNS Infrastructure (Free Plan) + SSL Certificates | Free | 0.00 |
| **Total Allocation** | | | **≈ 206.89/month** |

{{% notice info %}}
💰 **Total Estimated Cost:** ≈ **206.89 USD/month** — ≈ **2,482.68 USD/12 months**.
{{% /notice %}}

*Cost-Optimized Strategy (Staging / Development Environments)*

Should full high availability configurations be unnecessary during initial development, expenses can be scaled back by utilizing `t3.small` instances and a single-node database layer:

| Service | Configuration Specifications | Cost/Month (USD) |
|---|---|---|
| Amazon EC2 | 2 × `t3.small` | 30.37 |
| Application Load Balancer | 1 ALB | 22.27 |
| Amazon DocumentDB | 1 × `db.t3.medium` (Single-AZ) + 10 GB Storage | 57.94 |
| Shared Ecosystem Services | Amplify, CloudWatch, SNS, etc. (Identical to above) | ~7.00 |
| **Total Allocation** | | **≈ 117.58/month** |

> *Note:* These metrics represent a **baseline financial estimation**; core AWS pricing remains subject to periodic variance across separate regions and timeline updates. It is highly recommended to run the [AWS Pricing Calculator](https://calculator.aws/#/) based on your final deployment footprint (exact instance sizing, definitive cluster counts, storage allocations, traffic flows) to reflect exact figures, subsequently updating this index and your repository links. The overarching cost drivers are localized inside **Amazon DocumentDB** and **Amazon EC2** due to un-interrupted 24/7 provisioning — these can be further optimized using Savings Plans/Reserved Instances or scheduling resources to spin down outside peak operating hours.

### 7. Risk Assessment
*Risk Matrix*
- Single Availability Zone Outage: High Impact, Low Probability.
- Unanticipated User Traffic Spikes: Medium Impact, Medium Probability.
- Financial Budget Overruns: Medium Impact, Medium Probability.
- Security Vulnerabilities (Malicious Intrusions): High Impact, Low Probability.

*Mitigation Strategies*
- High Availability: Multi-AZ layout deployments paired alongside DocumentDB Multi-AZ topologies to enforce seamless automated failover.
- Elastic Scaling: Leveraging Auto Scaling Groups to handle compute adjustments dynamically alongside traffic changes.
- Budget Controls: Implementing strict expense guardrails via AWS Budgets alongside optimizing instance generation choices.
- Security Controls: Enforcing network isolation by housing DocumentDB within private subnets, restricting traffic access via defined Security Groups, mandating system-wide HTTPS, and tracking operations using CloudTrail.

*Disaster Recovery Plans*
- Enforcing regular automated Amazon DocumentDB snapshots to maintain clean rollback recovery state.
- Maintaining infrastructure as code architectures using CloudFormation/CDK to guarantee rapid system environment rebuilding following critical failures.

### 8. Anticipated Outcomes
*Technical Advances*: Delivery of a fully centralized, highly available, dynamically scalable, and extensively audited LMS environment, replacing obsolete isolated tracking approaches.
*Long-Term Strategy*: Setting a reliable system foundation perfectly suited to scale into cutting-edge academic modules (automated grading tools, advanced tracking frameworks, custom machine learning integrations) and easily reproducible across the team's upcoming enterprise training scopes.

</div>