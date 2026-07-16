---
title: "Workshop"
date: 2026-07-05
weight: 5
chapter: false
pre: " <b> 5. </b> "
---


### Overview

**Budget Tracker Website:** [https://d3ja9nvtyjzo9o.cloudfront.net/](https://d3ja9nvtyjzo9o.cloudfront.net/)

**Demo Video:** [https://drive.google.com/file/d/1_q4sdSqufmfxGnCE7WsOOij97Xxfb1hk/view?usp=sharing](https://drive.google.com/file/d/1_q4sdSqufmfxGnCE7WsOOij97Xxfb1hk/view?usp=sharing)

Welcome to the Workshop documentation for deploying the **Budget Tracker** personal finance management application. In this series of practical exercises, we will step-by-step build a complete system applying **AWS Serverless** and **Event-driven Architecture**.

The application aims to provide a flexible personal expense management solution, integrating automated transaction categorization using artificial intelligence (Google Gemini) and a multi-channel notification system, while keeping operational costs optimized at the lowest level thanks to the power of cloud computing.

### Objectives Achieved

After completing the 12 practical Modules of this course, you will be able to:
- Set up and manage secure user identities via **Amazon Cognito**.
- Build an API layer with **Amazon API Gateway** and serverless processing functions with **AWS Lambda**.
- Manage a high-performance NoSQL database with **Amazon DynamoDB** (applying the Single-Table Design model).
- Host and distribute a static React application globally via **Amazon S3** and **Amazon CloudFront**.
- Process asynchronous business flows using **Amazon SNS** and **Amazon SQS**.
- Deploy Infrastructure as Code (IaC) automatically through **AWS SAM** and **GitHub Actions**.

### Team Assignment — 4 Members, 1 Shared Account

| Member | Area | Workshop Sections |
|---|---|---|
| Chung | IAM + Route 53 + WAFv2 (Infrastructure Foundation) | [5.3](5.3-Infrastructure-IAM/) |
| Khiem | DynamoDB + Secrets Manager + S3 (Database & Data layer) + Cognito Auth & Edge | [5.4](5.4-Database-Storage/), [5.7](5.7-Edge-Security/) |
| Huy | API Gateway + Lambda Core (Transaction/Budget/Report) + Notifications (SNS/SQS/EventBridge) | [5.5](5.5-Backend-API/), [5.8](5.8-Notifications/) |
| Cong | React Frontend + Cognito login flow + Gemini AI integration | [5.6](5.6-Frontend-Auth-AI/) |

(Modules 1, 2, 9, 10, 11, 12 — Introduction, Prerequisites, Testing, Monitoring, Deployment, Cleanup — were done together by the whole team.)

### Content Structure

The workshop is divided into 12 sequential lessons (Modules), covering the entire software development lifecycle:

1. [Module 1 - Overview & Architecture](5.1-Introduction/)
2. [Module 2 - Environment Requirements & Shared Setup](5.2-Prerequisites/)
3. [Module 3 - Infrastructure Foundation & IAM Permissions](5.3-Infrastructure-IAM/)
4. [Module 4 - Data Layer (DynamoDB & S3)](5.4-Database-Storage/)
5. [Module 5 - Core Backend Layer (Lambda & API Gateway)](5.5-Backend-API/)
6. [Module 6 - Frontend, Auth & AI Integration](5.6-Frontend-Auth-AI/)
7. [Module 7 - Edge Security & Global Distribution](5.7-Edge-Security/)
8. [Module 8 - Asynchronous Processing & Notifications](5.8-Notifications/)
9. [Module 9 - End-to-End Testing Strategy](5.9-Testing/)
10. [Module 10 - System Monitoring & Operations](5.10-Monitoring/)
11. [Module 11 - Automated Deployment with IaC & CI/CD](5.11-Deployment/)
12. [Module 12 - Resource Cleanup](5.12-Cleanup/)

Let's begin the journey of conquering Serverless architecture with **Module 1: Overview & Architecture**!