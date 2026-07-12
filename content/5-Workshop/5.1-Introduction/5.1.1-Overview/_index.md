---
title: "5.1.1 Overview & Project Goals"
weight: 1
chapter: false
---


### 1. Executive Summary

The **Budget Tracker** workshop provides a detailed roadmap to deploy a personal finance management application using an **AWS Serverless** architecture.

The project simulates a real-world scenario: a personal finance management application with features such as secure login, transaction recording, automated transaction categorization using AI, and a multi-channel notification system. Through practical exercises, we will get acquainted with setting up cloud infrastructure, developing the Backend (API Gateway + Lambda), Frontend (React on S3 + CloudFront), deployment automation (CI/CD), and system operations monitoring.

The workshop's outcome is the ability to confidently build and operate a complete Serverless application. You will master the principles of auto-scaling and the pay-as-you-go billing model, helping to optimize operational costs to the maximum.

### 2. Learning Objectives

Upon completing this course, you will master the following core technical competencies:

- **Cloud-Native Architecture:** Deep understanding of AWS Serverless architecture and Event-driven programming principles.
- **Backend Services:** 
  - Deploy **Amazon API Gateway** to manage and route REST APIs.
  - Build **AWS Lambda** functions (FaaS) to handle business logic independently.
- **Security & Authorization:** Use **Amazon Cognito** to manage user identities and issue JWTs (ID token, Access token).
- **Database:** Manage non-relational data with **Amazon DynamoDB**, applying a Single-Table Design strategy to optimize query performance.
- **Frontend Hosting:** Deploy a static React application to **Amazon S3** combined with the **Amazon CloudFront** content delivery network (CDN).
- **DevOps & Automation:** Set up a CI/CD pipeline with **GitHub Actions** and **AWS SAM** (Serverless Application Model).
- **System Monitoring:** Collect metrics, logs, and set up proactive alerts via **Amazon CloudWatch**.

### 3. Prerequisite Knowledge

To effectively follow along and practice in the Workshop, you need to be equipped with the following foundation:

- **Web Programming:** Basics of HTML, CSS, JavaScript, and the React framework.
- **Backend Programming:** Experience with a Backend language (like C# .NET or Node.js) and a clear understanding of REST API design.
- **Tools:** Proficiency in source code management with Git/GitHub.
- **Cloud Platform:** Basic understanding of the AWS ecosystem and how to interact via the Command Line Interface (AWS CLI).
