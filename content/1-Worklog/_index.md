---
title: "Worklog"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

This is the complete 12-week internship worklog from my participation in the **First Cloud AI Journey (FCAJ)** program, integrating both the **16 AWS Labs hands-on curriculum** and the **Group Project (Serverless Budget Tracker) & Personal Workshop progression**.

The 12-week timeline is structured across 5 progressive phases:

**Phase 1 — Environment Setup, Onboarding & System Design (Weeks 1–3)**

**Week 1:** [Kickoff, Root Cause Analysis & Project Proposal](1.1-Week1/) — Studied FCAJ orientation & Cloud Journey roadmap; provisioned AWS account, resolved account lockout via Root Cause Analysis; surveyed financial domain and defined group project scope.

**Week 2:** [Onboarding Tasks & Mitigation Strategy](1.2-Week2/) — Unblocked progress with a backup AWS account; completed 5/5 Onboarding tasks (EC2, Lambda, RDS Aurora, AWS Budgets, Bedrock Claude 3 Haiku Model Access); activated $100 AWS Cloud Credits; finalized team roles.

**Week 3:** [AWS Budgets/CloudWatch & Architecture Design](1.3-Week3/) — Built AWS Budgets & CloudWatch cost governance framework; attended AWS Community Day 2026 (GenAI & Multi-Agent); ratified Serverless Stack (API Gateway → C# Lambda → DynamoDB → S3); authored Proposal with AWS Pricing Calculator.

---

**Phase 2 — VPC Networking, DynamoDB & Backend Core (Weeks 4–6)**

**Week 4:** [VPC Network, Cognito Auth & Bedrock AgentCore](1.4-Week4/) — Consulted Mentors to resolve IAM/CloudShell issues; joined AWS Student Builder Group & analyzed "Hera" repo (Bedrock AgentCore Voice Agents); provisioned VPC Subnets, Cognito User Pool Auth & developed C# Lambda CRUD APIs.

**Week 5:** [Lab 2-3 VPC Troubleshooting, DynamoDB & S3 Presigned URL](1.5-Week5/) — Signed off Lab 2 (AWS Networking & VPC); executed EC2 network troubleshooting in Lab 3; designed DynamoDB Single-Table Schema (`PK`/`SK`); deployed S3 Presigned URLs for direct receipt uploads.

**Week 6:** [Lab 3-4 EC2 Lifecycle, API Gateway & Business Logic](1.6-Week6/) — Signed off Lab 3 (VPC Security/NAT/VPN); completed >50% of Lab 4 (Windows Server 2025/Linux, Custom AMI, EBS Snapshots); configured API Gateway REST API with Cognito JWT Authorizer (VTL mapping) & 3 core C# Lambdas; delivered OpenAPI specs.

---

**Phase 3 — AWS Labs Sign-offs & AI/Edge Security (Weeks 7–8)**

**Week 7:** [Labs 4-9 Sign-off, Cold Start Optimization & Modules 5-6](1.7-Week7/) — Signed off consecutive AWS Labs 4 through 9 (IAM Governance, EC2-RDS Multi-AZ, Auto Scaling, ALB, CloudWatch, AWS Support); launched Lab 10 CloudFormation IaC; resolved UI CORS/JWT issues; optimized C# Lambda Cold Starts (`ReadyToRun`, 3.5s ➔ ~800ms); published Workshop Modules 5-6.

**Week 8:** [Advanced AWS Labs 10-14, Gemini AI & Edge Security](1.8-Week8/) — Corporate enterprise internship experience; completed AWS Labs through Lab 14; attended AWS FCAJ Community Day; integrated Google Gemini 2.5 Flash (Structured Outputs auto-categorization & Financial Chatbot with Guardrails); configured CloudFront CDN + AWS WAFv2; launched personal Workshop Web report project.

---

**Phase 4 — 100% AWS Labs Completion, Event-Driven & Document Alignment (Weeks 9–10)**

**Week 9:** [100% Sign-off Labs 15-16 ECS/Docker & Event-Driven Async Pipeline](1.9-Week9/) — Signed off 100% of Lab 15 (Docker) & Lab 16 (Amazon ECS Blue/Green Deployment); completed 16 AWS Labs curriculum; constructed async notification pipeline (SQS + SNS) with Idempotency pattern (DynamoDB TTL 24h) & EventBridge Cron scheduler.

**Week 10:** [Final Review, Single Source of Truth & Well-Architected Framework](1.10-Week10/) — Achieved 100% sign-off for Group and Personal projects; resolved documentation drift by refactoring Proposal, Blog, and Workshop per Single Source of Truth standards; studied AWS Well-Architected Framework.

---

**Phase 5 — Infrastructure as Code, CI/CD Pipeline & Handover (Weeks 11–12)**

**Week 11:** [Infrastructure as Code (AWS SAM) & GitHub Actions OIDC](1.11-Week11/) — Authored AWS SAM `template.yaml` defining full serverless infrastructure from Lab 10 experience; constructed automated CI/CD Pipeline via GitHub Actions with OIDC authentication (zero long-lived credentials); published Workshop Module 11.

**Week 12:** [UAT, Cost Audit, Resource Cleanup & Final Report](1.12-Week12/) — Executed end-to-end User Acceptance Testing (UAT); audited AWS Cost Explorer; performed Resource Cleanup (Module 12) releasing 100% billable resources on AWS Cloud; compiled Final Internship Report.
