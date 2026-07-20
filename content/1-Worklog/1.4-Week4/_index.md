---
title: "Week 4 Worklog"
date: 2026-05-04
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Consult FCAJ Mentors to resolve IAM, CloudShell, and Bedrock Model Access policy issues.
* Participate in AWS Student Builder Group; analyze open-source "Hera" repo & Voice Agents on Bedrock AgentCore.
* Provision baseline VPC networking, configure Amazon Cognito User Pool, and develop C# Lambda CRUD endpoints.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Consult Mentors to resolve IAM permissions, CloudShell, and Bedrock issues. Participate in AWS Student Builder Group; analyze "Hera" open-source architecture and Voice Agents on Bedrock AgentCore. | 05/25/2026 | 05/27/2026 | [Amazon Bedrock AgentCore](https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html) |
| Thu - Fri | Deploy VPC network infrastructure: `/16` CIDR, Public/Private Subnet isolation, Internet Gateway, and Security Groups. Configure Amazon Cognito User Pool and author C# JWT authentication middleware. | 05/28/2026 | 05/29/2026 | [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| Sat - Sun | Develop C# Lambda CRUD functions for Transactions (`POST`, `GET`, `PUT`, `DELETE`). Establish API Contract (JSON Schema) with Frontend Engineer for parallel development. | 05/30/2026 | 05/31/2026 | [API Gateway REST API Reference](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html) |

### Week 4 Achievements:

* Resolved system IAM/CloudShell permission errors with expert guidance from Mentors.
* Learned Voice Agent architectural patterns from the "Hera" repository for advanced roadmap features.
* Successfully established production-ready VPC networking, Cognito Auth, and C# CRUD Lambdas.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
VPC Public/Private Subnet separation embodies **Defense in Depth**: Lambda functions reside in Private Subnets without public IPs, routing traffic exclusively through API Gateway. Adjusting IAM Trust Policies for Bedrock AgentCore with Mentors clarified governance rules for AI Agents.

#### Analytical (BA/SA Perspective)
Agreeing on an **API Contract (JSON Schema) before writing code** unblocks Frontend and Backend engineers to work concurrently without friction. Active participation in the Student Builder Group expands team awareness regarding emerging Voice AI agent trends.

### Next Steps:
Pass Lab 2 & execute Lab 3 troubleshooting (VPC/EC2); design DynamoDB Single-Table Schema and S3 Presigned URLs for the project.
