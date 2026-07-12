---
title: "Worklog"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

This is the complete 12-week internship worklog from my time in the **First Cloud AI Journey (FCAJ)** program, built around the team project **Budget Tracker** — a personal finance management application on the AWS Serverless stack.

The 12-week timeline is structured across 5 progressive phases:

**Phase 1 — Environment Setup & System Design (Weeks 1–3)**

**Week 1:** [Kickoff & Root Cause Analysis](1.1-week1/) — Studied FCAJ orientation, provisioned AWS account with security baseline (MFA, IAM Least Privilege), resolved account lockout via Root Cause Analysis.

**Week 2:** [Onboarding & Mitigation Strategy](1.2-week2/) — Unblocked progress with a backup AWS account, completed 5/5 Onboarding tasks (EC2, Lambda, RDS Aurora, AWS Budgets, Amazon Bedrock), activated Cloud Credits.

**Week 3:** [Architecture Design & Project Proposal](1.3-week3/) — Ratified Serverless Stack (API Gateway → Lambda C# → DynamoDB → S3), authored Proposal with AWS Pricing Calculator cost estimates and role-based Work Breakdown Structure.

---

**Phase 2 — Infrastructure & Backend Core (Weeks 4–6)**

**Week 4:** [Network Infrastructure & Cognito Auth](1.4-week4/) — Provisioned VPC with Public/Private Subnet isolation, configured Amazon Cognito User Pool, implemented C# JWT middleware, and aligned API Contract with Frontend.

**Week 5:** [DynamoDB Single-Table Design & S3 Presigned URL](1.5-week5/) — Designed Access-Pattern-First schema to prevent Hot Partition, integrated AWS SDK DynamoDB with `QueryAsync`, deployed S3 Presigned URLs for direct client-side receipt uploads.

**Week 6:** [API Gateway & Lambda Business Logic](1.6-week6/) — Configured Cognito JWT Authorizer at API Gateway perimeter, Payload Mapping Template extracting `sub` from JWT claims, deployed TransactionFunction/BudgetFunction/ReportFunction with GSI, delivered OpenAPI/Swagger spec.

---

**Phase 3 — Integration & AI/Security (Weeks 7–8)**

**Week 7:** [Frontend Integration & Cold Start Optimization](1.7-week7/) — Resolved CORS failures (API Gateway + Lambda response headers), fixed JWT header format, optimized C# Lambda Cold Start from 3.5s to <1s via `ReadyToRun` compilation and `System.Text.Json` migration.

**Week 8:** [Gemini AI Integration & Edge Security](1.8-week8/) — Integrated `gemini-2.5-flash` with Structured Output enforcement for auto-categorization, deployed AI Chatbot with guardrail System Prompt, configured CloudFront CDN + WAFv2 Rate Limiting and Managed Rules (SQLi, XSS, Bad Bot).

---

**Phase 4 — Resilience & Observability (Weeks 9–10)**

**Week 9:** [Async SNS/SQS Pipeline & EventBridge](1.9-week9/) — Built Event-Driven Notification Pipeline (SQS buffer → SNS fan-out), implemented Idempotency Pattern with DynamoDB MessageId TTL, configured Dead Letter Queue and EventBridge Cron scheduler for monthly summaries.

**Week 10:** [Final Review & Well-Architected Assessment](1.10-week10/) — Identified and resolved document drift (Single Source of Truth enforcement), assessed architecture against AWS Well-Architected Framework (Security & Cost Optimization Pillars), produced improvement backlog for Weeks 11–12.

---

**Phase 5 — Automation & Handover (Weeks 11–12)**

**Week 11:** [Infrastructure as Code & CI/CD Pipeline](1.11-week11/) — Authored AWS SAM `template.yaml` defining the full infrastructure stack, configured GitHub Actions pipeline with OIDC authentication (zero long-lived credentials), automated test → build → deploy on every push.

**Week 12:** [UAT, Cost Audit & Project Handover](1.12-week12/) — Executed end-to-end User Acceptance Testing, audited AWS Cost Explorer (identified and eliminated idle NAT Gateway costs), deleted CloudFormation Stack, composed final internship report and presentation slides for the evaluation board.
