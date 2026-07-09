---
title: "Week 9 Worklog"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 9 Objectives
> **Build serverless applications on AWS** using **AWS Lambda, Amazon API Gateway, and Amazon SQS**. Understand **event-driven architecture**, develop Lambda functions in **Python** or **Node.js**, create RESTful APIs without managing servers, and integrate **Amazon SQS** for asynchronous message processing.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 05-06** (*Introduction to AWS Lambda*) and **Module 05-07** (*Lambda Triggers & Execution Model*). Take notes on the lifecycle of a Lambda invocation, including **Cold Starts** and **Warm Starts**. | 15/06/2026 | 15/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 05-08** (*Amazon API Gateway*) and **Module 05-09** (*Amazon SQS & Event-Driven Architecture*). Learn how **Amazon API Gateway** integrates with **AWS Lambda** using **Lambda Proxy Integration**. | 16/06/2026 | 16/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **AWS Lambda Lab:**<br>• Develop a **Python Lambda function** that returns a JSON response.<br>• Configure an **Amazon S3 Event** trigger so that uploading an image automatically invokes a Lambda function to resize it.<br>• Use **Amazon CloudWatch Logs** to debug and monitor function execution. | 17/06/2026 | 17/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **Amazon API Gateway + AWS Lambda Lab:**<br>• Create a REST API with three endpoints: **GET /items**, **POST /items**, and **DELETE /items/{id}**.<br>• Integrate **AWS Lambda** for business logic and **Amazon DynamoDB** for data storage.<br>• Test the API using **Postman** and deploy it to the **`production`** stage. | 18/06/2026 | 18/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | **Amazon SQS Lab:**<br>• Create an **Amazon SQS Standard Queue** and a **Dead Letter Queue (DLQ)**.<br>• Implement a **Lambda producer** to send messages and a **Lambda consumer** to process them.<br>• Test error handling and retry mechanisms.<br>• Write and publish the **Week 9 Worklog** on the website. | 19/06/2026 | 19/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **A complete serverless API** built with **Amazon API Gateway**, **AWS Lambda**, and **Amazon DynamoDB**, successfully tested using **Postman**.
> * [x] **An Amazon S3-triggered Lambda function** that automatically processes uploaded images and stores the output in a destination bucket.
> * [x] **An asynchronous Amazon SQS pipeline** with a properly configured **Dead Letter Queue (DLQ)** for handling failed messages.
> * [x] **Week 9 Worklog report** fully completed and successfully published on this website.