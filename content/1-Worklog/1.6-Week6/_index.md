---
title: "Week 6 Worklog"
date: 2026-05-04
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Complete Lab 3 sign-off (VPC Security/NAT/VPN) and execute >50% of Lab 4 (Windows Server 2025/Linux, AMI, EBS Snapshots).
* Configure API Gateway REST API with Cognito JWT Authorizer and Payload Mapping Templates (VTL).
* Implement C# business logic for 3 core Lambda functions (`TransactionFunction`, `BudgetFunction`, `ReportFunction`) and publish OpenAPI specs.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Resolve network traffic issues and complete **Lab 3** sign-off (VPC Firewall, NAT Gateway, Site-to-Site VPN). Initiate **Lab 4**: deploy isolated VPC, run Windows Server 2025 and Amazon Linux EC2s (>50% completed). | 06/08/2026 | 06/10/2026 | [Amazon EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) |
| Thu - Fri | Practice EC2 lifecycle management in Lab 4 (EBS Snapshots, Custom AMIs). Configure API Gateway REST API: define `/transactions`, `/budgets`, `/reports` Resources & Methods. Attach Cognito JWT Authorizer. | 06/11/2026 | 06/12/2026 | [API Gateway Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html) |
| Sat - Sun | Implement C# business logic for three core Lambdas: `TransactionFunction`, `BudgetFunction`, `ReportFunction`. Use VTL Payload Mapping Template to inject JWT `sub` User ID. Draft OpenAPI/Swagger docs for Frontend handover. | 06/13/2026 | 06/14/2026 | [AWS Lambda Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html) |

### Week 6 Achievements:

* Successfully signed off Lab 3 and completed over 50% of Lab 4 exercises.
* Operationalized API Gateway REST API with Cognito Authorizer, enforcing perimeter access control.
* Delivered 3 core C# Lambda functions and handed over OpenAPI specifications to Frontend developers.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Enforcing Cognito Authorization at API Gateway rather than within Lambda code **rejects unauthorized requests at the edge** — conserving Lambda execution budgets. Mastering EC2 AMI and EBS Snapshot management in Lab 4 deepens knowledge of server backup and disaster recovery.

#### Analytical (BA/SA Perspective)
OpenAPI/Swagger documentation serves as the **Single Source of Truth** between Backend and Frontend engineers. Defining HTTP status codes and payload contracts enables independent Frontend development without communication bottlenecks.

### Next Steps:
Achieve sign-off for Labs 4 through 9; initiate Lab 10 CloudFormation; integrate Frontend-Backend, debug CORS/JWT, and optimize C# Lambda Cold Starts.
