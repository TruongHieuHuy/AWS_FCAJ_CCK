---
title: "Week 8 Worklog"
date: 2026-05-04
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Integrate Google Gemini API (`gemini-2.5-flash`) for automated financial transaction categorization.
* Deploy AI Financial Chatbot with strict operational guardrails.
* Configure Edge Security: CloudFront CDN + AWS WAFv2 protecting against DDoS and injection attacks.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Integrate Gemini REST API (`gemini-2.5-flash`) into `AiFunction` C# Lambda via `HttpClient`. Design prompt engineering for **auto-categorization**: pass transaction description → Gemini classifies into category (Food, Transport, Shopping...) and returns result as **Structured Output** (JSON schema enforcement) to guarantee a parseable, type-safe response on every invocation. | 06/22/2026 | 06/24/2026 | [Gemini API Documentation](https://ai.google.dev/gemini-api/docs) |
| Thu - Fri | Deploy AI Financial Chatbot in React Frontend: design **System Prompt** with explicit guardrails — AI is restricted to personal budget management queries and must refuse out-of-scope requests (stocks, crypto) to mitigate legal risk from unlicensed financial advice. | 06/25/2026 | 06/26/2026 | [Gemini System Instructions](https://ai.google.dev/gemini-api/docs/system-instructions) |
| Sat - Sun | Configure Edge Security with Database Engineer: provision **CloudFront Distribution** as CDN in front of S3 and API Gateway; attach **AWS WAFv2 Web ACL** with ruleset: Rate Limit (1000 req/5min/IP), AWS Managed Rules (SQLi, XSS, Bad Bot protection). Complete Workshop Module 7 (Edge Security). | 06/27/2026 | 06/28/2026 | [AWS WAFv2 Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Week 8 Achievements:

* AiFunction auto-categorizes transactions with high accuracy via Structured Output constraint.
* AI Chatbot operates within guardrails — off-topic prompts successfully blocked at System Prompt level.
* CloudFront + WAFv2 deployed and tested: Rate Limiting and SQL Injection protection verified operational.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Gemini Structured Output (JSON Schema enforcement) solves the **non-deterministic LLM output problem**: without schema constraints, the model may return unstructured free text that breaks Lambda's JSON parser at runtime. By passing the desired JSON schema in the API call, Gemini is contractually bound to always return the correct format — completely eliminating the need for regex/string parsing at the application layer. WAFv2 Rate Limiting at 1000 req/5min/IP is calibrated for a personal-use application: permissive enough to not impact normal UX while effectively blocking automated credential stuffing and scraping attacks.

#### Analytical (BA/SA Perspective)
AI auto-categorization eliminates the **highest-friction point** in financial entry behavior: requiring users to manually select a category causes >60% to skip recording transactions altogether. Reducing the entry flow from 4 steps to 1 natural-language input directly decreases **User Friction** and increases **Daily Active Usage**. System Prompt guardrails are non-negotiable from a compliance perspective: providing unlicensed investment advice through an AI system creates actionable legal liability for the developer — guardrails are a risk management requirement, not an optional feature.

### Next Steps:
Build asynchronous SQS/SNS processing architecture for budget threshold alerts and automated monthly reporting.
