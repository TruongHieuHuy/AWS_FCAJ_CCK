---
title: "Week 3 Worklog"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Establish resource management and cost optimization governance (AWS Budgets, CloudWatch).
* Attend AWS Community Day 2026 conference and produce an in-depth harvest report on GenAI.
* Design Serverless Stack architecture for Budget Tracker, scaffold C# Backend repo, and author Project Proposal.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Master cost management (AWS Budgets, CloudWatch Metrics/Alarms); resolve CloudShell environment issues. Hold architecture alignment meeting for Serverless Stack (API Gateway + C# Lambda + DynamoDB). | 05/18/2026 | 05/20/2026 | [AWS Serverless Architecture Patterns](https://aws.amazon.com/architecture/serverless/) |
| Thu - Fri | Attend AWS Community Day 2026; write report on GenAI & Multi-Agent Systems. Scaffold C# .NET 8 Web API monorepo with dependency injection and proper `.gitignore`. | 05/21/2026 | 05/22/2026 | [.NET on AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html) |
| Sat - Sun | Author Project Proposal: Architecture Diagram, cost estimation using AWS Pricing Calculator (Lambda invocations, DynamoDB RCU/WCU, API Gateway, Gemini API), WBS task breakdown. | 05/23/2026 | 05/24/2026 | [AWS Pricing Calculator](https://calculator.aws/pricing/2/home) |

### Week 3 Achievements:

* Mastered AWS Budgets & CloudWatch cost governance to prevent unexpected cloud expenses.
* Completed AWS Community Day 2026 summary report covering GenAI & Multi-Agent Systems.
* Approved Project Proposal and Serverless Architecture diagram across all team members.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Choosing a Serverless Stack (API Gateway + Lambda + DynamoDB) aligns technical efficiency with cost control: Lambda's **Pay-per-use** model eliminates idle server billing. Combining early cost governance via AWS Budgets ensures the development environment stays strictly within granted credits.

#### Analytical (BA/SA Perspective)
The Proposal functions as a binding project **contract**. Estimating costs using the AWS Pricing Calculator across realistic usage scenarios builds cost awareness early. Insights gained from AWS Community Day 2026 enrich the application roadmap with modern AI capabilities.

### Next Steps:
Consult Mentor on IAM/CloudShell issues; analyze open-source "Hera" repo & Bedrock AgentCore; provision VPC network infrastructure and Cognito Auth.
