---
title: "Week 10 Worklog"
date: 2026-06-22
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

> [!IMPORTANT]
> ### 🎯 Week 10 Objectives
> **Build a complete CI/CD pipeline on AWS** by automating the entire software delivery process—from code commits to production deployment—using **AWS CodeCommit**, **AWS CodeBuild**, and **AWS CodePipeline**. Apply **DevOps** best practices to shorten release cycles and improve application reliability.

### 📅 Detailed Implementation Plan

| Day | Task Details | Start Date | Completion Date | Reference |
| :---: | :--- | :---: | :---: | :---: |
| **Monday** | Watch **Module 05-10** (*Introduction to DevOps on AWS*) and **Module 05-11** (*AWS CodeCommit & AWS CodeBuild*). Learn the **GitFlow** workflow and how it integrates with **AWS Developer Tools**. | 22/06/2026 | 22/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Tuesday** | Watch **Module 05-12** (*AWS CodeDeploy & AWS CodePipeline*). Take notes on the differences between **In-Place Deployment** and **Blue/Green Deployment** in **AWS CodeDeploy**. | 23/06/2026 | 23/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Wednesday** | **CI/CD Lab – Part 1:**<br>• Create an **AWS CodeCommit** repository, clone it locally, and push the source code.<br>• Write a `buildspec.yml` file for **AWS CodeBuild** to install dependencies, run tests, and build deployment artifacts.<br>• Connect **AWS CodeBuild** to **AWS CodeCommit** and successfully complete the first build. | 24/06/2026 | 24/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Thursday** | **CI/CD Lab – Part 2:**<br>• Create an **AWS CodePipeline** with three stages: **Source → Build → Deploy**.<br>• Configure **AWS CodeDeploy** to perform a **Blue/Green deployment** to an **Amazon EC2 Auto Scaling Group**.<br>• Trigger the pipeline automatically whenever a new commit is pushed to the `main` branch. | 25/06/2026 | 25/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| **Friday** | Integrate **GitHub Actions** as an alternative CI/CD solution.<br>• Compare the advantages and disadvantages of **AWS-native CI/CD services** versus **GitHub Actions**.<br>• Review the complete CI/CD architecture built during the week.<br>• Write and publish the **Week 10 Worklog** on the website. | 26/06/2026 | 26/06/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |

> [!TIP]
> ### 🏆 Deliverables
> * [x] **A complete CI/CD pipeline** that automatically builds, tests, and deploys the application whenever a new commit is pushed to the `main` branch.
> * [x] **Blue/Green deployment** successfully implemented with **zero downtime** and automatic rollback in case of deployment failure.
> * [x] **A `buildspec.yml` configuration** that runs unit tests and prevents deployments when tests fail, ensuring code quality.
> * [x] **Week 10 Worklog report** fully completed and successfully published on this website.