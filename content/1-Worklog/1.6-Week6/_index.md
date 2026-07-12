---
title: "Week 6 Worklog"
date: 2026-05-04
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Configure API Gateway REST API with Cognito JWT Authorizer and Payload Mapping Templates.
* Implement full business logic for the three core Lambda functions.
* Author OpenAPI/Swagger specification for Frontend handover.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Configure API Gateway REST API: define Resources and Methods per endpoint, attach Cognito JWT Authorizer to reject unauthenticated requests at the Gateway boundary (zero Lambda invocation cost). Configure **Payload Mapping Template** (VTL) to extract `sub` from JWT claims and inject into downstream Lambda request body. | 06/08/2026 | 06/10/2026 | [API Gateway Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html) |
| Thu - Fri | Implement C# business logic for three Lambda functions: **TransactionFunction** (DynamoDB CRUD with budget threshold validation on write); **BudgetFunction** (compute and update remaining budget per spending category); **ReportFunction** (aggregate monthly spending statistics via `QueryAsync` with GSI). | 06/11/2026 | 06/12/2026 | [AWS Lambda Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html) |
| Sat - Sun | Execute end-to-end integration tests: validate full flow Authentication → API Gateway → Lambda → DynamoDB via Postman. Author OpenAPI (Swagger YAML) specification documenting request/response schemas, error codes, and authentication headers for Frontend handover. | 06/13/2026 | 06/14/2026 | [OpenAPI Specification](https://swagger.io/specification/) |

### Week 6 Achievements:

* API Gateway with Cognito Authorizer active: unauthorized requests rejected at perimeter with zero Lambda compute spend.
* Three core Lambda functions (Transaction, Budget, Report) fully implemented and integration-tested.
* OpenAPI/Swagger spec delivered to Frontend Engineer, unblocking parallel integration work.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Positioning the Cognito Authorizer at API Gateway rather than inside Lambda code is a key architectural decision: **rejecting unauthenticated requests at the perimeter** eliminates Lambda invocations and their associated Cold Start cost for unauthorized traffic. The Payload Mapping Template uses Velocity Template Language (VTL) to extract `context.authorizer.claims.sub` and inject it into the request body — ensuring Lambda never parses JWT tokens directly, enforcing Separation of Concerns. ReportFunction leverages a GSI (Global Secondary Index) instead of Scan to aggregate monthly spending with predictable, bounded cost.

#### Analytical (BA/SA Perspective)
The OpenAPI/Swagger document is not a technical artifact — it is the **operational contract** between Backend and Frontend teams for the duration of integration. Precisely defining HTTP status codes (200/400/401/403/500), error response schemas, and authentication header requirements enables Frontend Engineers to implement error-handling states autonomously, without escalating to Backend — measurably reducing cross-team communication overhead and increasing parallel development velocity.

### Next Steps:
Execute Frontend-Backend integration: debug CORS policy, resolve JWT parsing issues, and optimize Lambda Cold Start via ReadyToRun compilation.
