---
title: "Week 3 Worklog"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Design and ratify the Serverless architecture for the Budget Tracker system.
* Initialize Git repository and scaffold the C# .NET 8 Backend project structure.
* Draft a complete Project Proposal including architecture, cost estimates, and team WBS.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Facilitate team architecture workshop: ratify Serverless Stack (API Gateway + Lambda + DynamoDB), produce data flow diagram, and draft UI wireframes. | 05/18/2026 | 05/20/2026 | [AWS Serverless Architecture Patterns](https://aws.amazon.com/architecture/serverless/) |
| Thu - Fri | Initialize Git monorepo (backend/frontend/infra). Scaffold C# .NET 8 Web API project with dependency injection, `appsettings.json` environment config, and Lambda-compatible `.gitignore`. Establish branch strategy (main/develop/feature). | 05/21/2026 | 05/22/2026 | [.NET on AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html) |
| Sat - Sun | Author Project Proposal: system Architecture Diagram, operational cost estimation via AWS Pricing Calculator (Lambda invocations, DynamoDB RCU/WCU, API Gateway calls, Gemini API tokens), and detailed Work Breakdown Structure (WBS) by role. | 05/23/2026 | 05/24/2026 | [AWS Pricing Calculator](https://calculator.aws/pricing/2/home) |

### Week 3 Achievements:

* Team-approved Serverless Stack architecture: API Gateway → Lambda (C#) → DynamoDB → S3.
* Repository initialized with standardized directory structure ready for parallel Frontend/Backend development.
* Completed Project Proposal with quantified cost estimates and role-based WBS.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Selecting a Serverless architecture (API Gateway + Lambda + DynamoDB) is simultaneously a technical and business decision: Lambda's **Pay-per-use** model eliminates idle server costs entirely — optimal for a personal finance app with irregular traffic patterns. A critical technical note: configuring `PublishReadyToRun=true` in the `.csproj` file from Day 1 is essential to pre-compile C# binaries and minimize Lambda Cold Start latency before the first production invocation.

#### Analytical (BA/SA Perspective)
The Project Proposal functions as a team **contract** — not merely a technical document. Modeling cost scenarios with AWS Pricing Calculator (100 users/day × 10 transactions/user) enables the team to make informed architectural trade-offs with quantified financial context. The role-based WBS (Backend Engineer, Frontend Engineer, Database Engineer) prevents responsibility overlap and establishes an objective framework for progress tracking throughout the 12-week delivery cycle.

### Next Steps:
Provision networking infrastructure (VPC, Subnets, Security Groups) and configure Amazon Cognito User Pool for the authentication flow.
