---
title: "Week 7 Worklog"
date: 2026-05-04
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Resolve CORS and JWT parsing errors surfaced during Frontend-Backend integration.
* Optimize Lambda Cold Start from ~3.5s to sub-1s using ReadyToRun compilation.
* Complete Workshop Module 5 and Module 6 documentation.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Coordinate with Frontend Engineer: debug API call flow from ReactJS to API Gateway. Identify and resolve **CORS** failures: enable CORS on each API Gateway Method (OPTIONS preflight), append `Access-Control-Allow-Origin` and `Access-Control-Allow-Headers` to all Lambda responses. Debug JWT payload issue: verify `Authorization: Bearer <token>` header format and ensure Cognito Authorizer is configured to read the correct header key. | 06/15/2026 | 06/17/2026 | [API Gateway CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html) |
| Thu - Fri | Optimize C# Lambda Cold Start: enable `PublishReadyToRun=true` in `.csproj` to pre-compile IL to native code; prune NuGet package dependencies; migrate from `Newtonsoft.Json` to `System.Text.Json` (lightweight serializer). Benchmark results via Lambda CloudWatch Logs (Init Duration metric). | 06/18/2026 | 06/19/2026 | [Lambda Cold Start Optimization](https://docs.aws.amazon.com/lambda/latest/dg/snapstart.html) |
| Sat - Sun | Author Workshop documentation: **Module 5** (DynamoDB Single-Table Design — theory, lab walkthrough, Access Pattern explanations) and **Module 6** (C# Serverless Web API — scaffold, Lambda handler, DynamoDB SDK integration). | 06/20/2026 | 06/21/2026 | [AWS Workshop Studio](https://studio.us-east-1.prod.workshops.aws/) |

### Week 7 Achievements:

* Resolved all CORS and JWT parsing errors — Frontend API connectivity 100% operational.
* C# Lambda Cold Start reduced from ~3.5s to ~800ms via ReadyToRun + serializer optimization (~70% improvement).
* Completed Module 5 & 6 Workshop guides with full lab steps and technical explanations.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
CORS is not a feature — it is a **browser security enforcement mechanism** that must be configured at two layers: API Gateway (OPTIONS method + CORS response headers) and inside every Lambda response object, including error responses. C# Lambda Cold Start is a well-known JIT-compiled runtime issue: ReadyToRun pre-compiles managed IL to native instructions, eliminating JIT compilation overhead at invocation time. Combined with dependency pruning (fewer packages = smaller deployment package = faster cold-load), Init Duration dropped from 3.5s to <1s.

#### Analytical (BA/SA Perspective)
From a User Experience perspective: a 3.5s Lambda Cold Start on the first API call after an idle period is **unacceptable for a financial application** — users interpret slow responses as system failures. Reducing to sub-1s meets the **Perceived Performance** threshold (Google Research: bounce rate increases 32% when load time exceeds 3s). This is a textbook case of a technical optimization with a direct, measurable impact on a Business Metric: User Retention.

### Next Steps:
Integrate Google Gemini API for AI auto-categorization and deploy Edge Security with CloudFront + AWS WAFv2.
