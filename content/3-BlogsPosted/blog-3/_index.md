---
title: "Blog 3"
date: 2026-04-20
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Proactive Monitoring for Amazon Redshift Serverless Using AWS Lambda and Slack Alerts

---

> [!IMPORTANT]
> ### 🎯 Article Objective
> This article demonstrates how to build a **proactive monitoring solution** for **Amazon Redshift Serverless** using **AWS Lambda**. The solution automatically detects performance anomalies and sends **real-time alerts to Slack**, enabling operations teams to respond quickly, optimize performance, and control costs without continuously monitoring dashboards.
>
> * **Original article:** [AWS Study Group](https://awsstudygroup.com/2026/05/14/giam-sat-chu-dong-cho-amazon-redshift-serverless-bang-aws-lambda-va-canh-bao-slack/?fbclid=IwY2xjawS0WyVleHRuA2FlbQIxMABicmlkETBXUWJOcmRwd1dmbGluRG8zc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHjQNB21aCPpxAiaELPOoVMVWuMuwbuL5UeWGcAGbi2tfUpmErSiw8GN2KJlQ_aem_A_72VJwE6sRyKIvDmsfpLg)

---

## 1. Introduction

**Amazon Redshift Serverless** simplifies analytics data warehouse deployments by eliminating the need to provision and manage infrastructure, allowing teams to focus on analyzing data instead of operating the underlying platform.

However, even in a serverless environment, issues such as:

- Queued queries.
- Long-running queries.
- Unexpected spikes in compute capacity (RPUs).
- Resource utilization exceeding acceptable thresholds.

can still impact performance and increase operational costs if they are not detected early.

Although Amazon Redshift Serverless provides built-in monitoring dashboards, delivering alerts directly to **Slack** enables operations teams to respond more quickly without constantly monitoring dashboards.

---

## 2. Solution: Proactive Monitoring with AWS Lambda

This solution uses several AWS services to automatically collect performance metrics from Amazon Redshift Serverless, evaluate them against user-defined thresholds, and notify the operations team whenever anomalies are detected.

The primary AWS services involved include:

- **Amazon EventBridge** to trigger scheduled monitoring tasks.
- **AWS Lambda** to collect and evaluate performance metrics.
- **Amazon CloudWatch** to retrieve system metrics.
- **Amazon Redshift Data API** to query workload information.
- **Amazon SNS** to publish notifications.
- **Amazon Q Developer in Chat Applications** to deliver alerts to Slack.
- **Amazon CloudWatch Logs** to store execution logs for troubleshooting and auditing.

---

## 3. Overall Architecture

![Amazon Redshift Serverless Monitoring Architecture](/images/733471444_2463215147523527_6193328843618823246_n.jpg)

### End-to-End Workflow

| Step | Component | Description |
| :---: | :--- | :--- |
| **1** | **Amazon EventBridge → AWS Lambda** | EventBridge invokes the Lambda function on a configurable schedule (by default, every 15 minutes during business hours). |
| **2** | **AWS Lambda → CloudWatch & Amazon Redshift Data API** | Lambda collects metrics including queued queries, running queries, RPUs, storage utilization, table count, database connections, and slow-running queries. |
| **3** | **AWS Lambda** | The collected metrics are evaluated against user-defined performance thresholds. |
| **4** | **AWS Lambda → Amazon SNS** | When a threshold is exceeded, Lambda publishes a notification to an Amazon SNS topic. |
| **5** | **Amazon SNS → Amazon Q Developer in Chat Applications → Slack** | Amazon Q Developer in Chat Applications forwards the notification to the designated Slack channel. |
| **6** | **AWS Lambda → Amazon CloudWatch Logs** | Lambda execution logs are stored in CloudWatch Logs for monitoring, troubleshooting, and auditing purposes. |

*This architecture provides continuous monitoring for Amazon Redshift Serverless, enabling early detection of performance anomalies and delivering actionable alerts directly to Slack before issues affect users or downstream analytics workloads.*

---

## 4. Benefits of the Solution

> [!TIP]
> ### 🚀 Proactive Monitoring and Operational Excellence
>
> This architecture provides several operational benefits:
>
> 1. **Early Detection of Performance Issues** – Continuously monitors key performance metrics and immediately alerts the operations team when predefined thresholds are exceeded.
>
> 2. **Automated Monitoring Workflow** – Eliminates the need for continuous dashboard monitoring by using Amazon EventBridge and AWS Lambda to perform scheduled health checks automatically.
>
> 3. **Real-Time Slack Notifications** – Delivers alerts directly to Slack, allowing engineering teams to respond more quickly to emerging issues.
>
> 4. **Cost-Effective Serverless Architecture** – Built entirely with managed serverless services such as AWS Lambda, Amazon EventBridge, and Amazon SNS, removing the need to provision or manage infrastructure.
>
> 5. **Comprehensive Observability** – Stores Lambda execution logs in Amazon CloudWatch Logs, providing complete visibility for monitoring, troubleshooting, and operational auditing.
```
