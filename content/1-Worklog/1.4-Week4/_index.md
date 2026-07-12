---
title: "Week 4 Worklog"
date: 2026-05-04
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Provision base networking infrastructure (VPC, Subnets, Security Groups, NAT Gateway).
* Configure Amazon Cognito User Pool and integrate JWT validation into C# Lambda.
* Develop basic CRUD Lambda endpoints with mock data to verify API routing.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Provision networking layer: create VPC with `/16` CIDR, segment Public Subnets (API Gateway/ALB) from Private Subnets (Lambda/Database), configure Internet Gateway, Route Tables, and NAT Gateway. Enforce Security Group Least Privilege — open only required ports, deny all others by default. | 05/25/2026 | 05/27/2026 | [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| Thu - Fri | Configure Amazon Cognito User Pool: set password policy, enable optional MFA, create App Client without client secret (SPA pattern). Implement C# JWT middleware: validate token signature against Cognito JWKS endpoint; extract `sub` (User ID) from claims for resource-level authorization. | 05/28/2026 | 05/29/2026 | [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html) |
| Sat - Sun | Develop C# Lambda CRUD handlers for Transactions using mock in-memory data: `POST /transactions`, `GET /transactions`, `PUT /transactions/{id}`, `DELETE /transactions/{id}`. Align JSON Schema (API Contract) with Frontend Engineer to enable parallel development tracks. | 05/30/2026 | 05/31/2026 | [API Gateway REST API Reference](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html) |

### Week 4 Achievements:

* Production-ready VPC with full network isolation between application tiers.
* Cognito User Pool operational; C# Lambda successfully validates JWT tokens.
* API Contract (JSON Schema) agreed upon by both Frontend and Backend — unlocking parallel development.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
The Public/Private Subnet separation implements **Defense in Depth**: Lambda functions in Private Subnets carry no public IPs — all inbound traffic must traverse API Gateway. Security Group configuration enforces Least Privilege: internal subnet-to-subnet traffic only, no public port 22/3389 exposure. JWT validation using Cognito's JWKS endpoint ensures standards-compliant OAuth 2.0 signature verification without storing client secrets server-side.

#### Analytical (BA/SA Perspective)
Ratifying the **API Contract before writing business logic** is the single highest-impact decision this week. By locking JSON Schema per endpoint upfront, Frontend and Backend can iterate independently — directly compressing **Time-to-Integration**. Integration bugs discovered late in a sprint typically cost 3-5× more to resolve than unit-level defects, making early contract alignment a measurable risk reduction strategy.

### Next Steps:
Design DynamoDB Single-Table Schema and implement real database connectivity from C# Lambda functions.
