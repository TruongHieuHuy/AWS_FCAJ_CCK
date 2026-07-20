---
title: "Week 7 Worklog"
date: 2026-05-04
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Complete sign-off for Labs 4 through 9 (IAM, EC2-RDS, Auto Scaling, ALB, Budgets, CloudWatch) and start Lab 10 IaC.
* Resolve CORS and JWT parsing errors during Frontend React integration with API Gateway.
* Optimize C# Lambda Cold Start from ~3.5s to ~800ms (`PublishReadyToRun=true`); complete Workshop Modules 5 & 6.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Complete sign-off for **Labs 4 through 9** (IAM Governance, EC2-RDS Multi-AZ, Auto Scaling, ALB, Budgets, CloudWatch, AWS Support). Apply peripheral error bypass strategies to maintain momentum. Debug Frontend CORS and JWT parsing. | 06/15/2026 | 06/17/2026 | [AWS Auto Scaling User Guide](https://docs.aws.amazon.com/autoscaling/) |
| Thu - Fri | Draft Reference Architecture on draw.io & initiate **Lab 10** (IaC with CloudFormation). Optimize C# Lambda Cold Start: enable `PublishReadyToRun=true` in `.csproj`, switch to `System.Text.Json` serializer. Measure Init Duration in CloudWatch Logs. | 06/18/2026 | 06/19/2026 | [Lambda Cold Start Optimization](https://docs.aws.amazon.com/lambda/latest/dg/snapstart.html) |
| Sat - Sun | Author and publish Workshop documentation: **Module 5** (DynamoDB Single-Table Design) and **Module 6** (C# Serverless Web API). | 06/20/2026 | 06/21/2026 | [AWS Workshop Studio](https://studio.us-east-1.prod.workshops.aws/) |

### Week 7 Achievements:

* Completed consecutive sign-offs for AWS Labs 4 through 9 and launched Lab 10 CloudFormation.
* Resolved CORS & JWT parsing issues 100%, enabling seamless React Frontend calls to API Gateway.
* Reduced C# Lambda Cold Start latency from ~3.5s to ~800ms (~70% improvement); published Modules 5 & 6.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
HA infrastructure principles (High Availability) acquired from Auto Scaling & ALB labs inform fault-tolerant design. Enabling `PublishReadyToRun=true` pre-compiles IL code to native instructions, removing JIT compilation overhead during initial Lambda invocation.

#### Analytical (BA/SA Perspective)
Cutting Cold Start latency from 3.5s to <1s directly improves **Perceived Performance** for users on financial management interfaces. Flexibly applying lab bypass strategies protected overall schedule milestones without being derailed by third-party environment glitches.

### Next Steps:
Accelerate AWS Labs completion (through Lab 14); integrate Google Gemini AI (auto-categorization & Financial Chatbot), configure Edge Security (CloudFront/WAFv2), and launch personal Workshop project.
