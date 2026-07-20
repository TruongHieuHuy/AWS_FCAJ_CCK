---
title: "Week 8 Worklog"
date: 2026-05-04
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Experience corporate enterprise environment; accelerate AWS Labs progress through Lab 14.
* Integrate Google Gemini API (`gemini-2.5-flash`) for auto-categorization (Structured Output) & financial advice AI Chatbot.
* Establish Edge Security (CloudFront CDN + AWS WAFv2); participate in AWS FCAJ Community Day and launch personal Workshop project.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | On-site corporate enterprise internship experience. Integrate Gemini REST API (`gemini-2.5-flash`) into C# `AiFunction` Lambda: call API via `HttpClient`, configure **Structured Output** (JSON Schema enforcement) for automatic transaction classification. | 06/22/2026 | 06/24/2026 | [Gemini API Documentation](https://ai.google.dev/gemini-api/docs) |
| Thu - Fri | Accelerate AWS Labs progress through **Lab 14**. Draft group project Workflow diagrams (HLA/LLA) and receive Mentor feedback. Deploy React AI Financial Chatbot with **System Prompt Guardrails** restricting advice scope. | 06/25/2026 | 06/26/2026 | [Gemini System Instructions](https://ai.google.dev/gemini-api/docs/system-instructions) |
| Sat - Sun | Attend AWS FCAJ Community Day event. Configure **CloudFront CDN** + **AWS WAFv2** (Rate Limiting 1000 req/5min, SQLi/XSS protection). Launch personal project (Workshop report Web), clone template source code. Complete Module 7. | 06/27/2026 | 06/28/2026 | [AWS WAFv2 Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Week 8 Achievements:

* Completed advanced AWS Labs exercises through Lab 14.
* `AiFunction` accurately classifies transactions using Structured Output enforcement; AI Chatbot operates safely within guardrails.
* Perimeter security (CloudFront + WAFv2) operationalized; personal Workshop Web report repository initialized.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Gemini Structured Output (JSON Schema enforcement) resolves non-deterministic LLM output: forcing the model to return valid JSON schemas ready for direct DynamoDB persistence. CloudFront CDN + WAFv2 Rate Limiting safeguards APIs against DDoS attacks and automated scraping.

#### Analytical (BA/SA Perspective)
Direct corporate internship experience aligns engineering practices with industry standards. AI auto-categorization eliminates manual expense entry friction. System Prompt guardrails represent vital risk management measures against unverified financial advice liability.

### Next Steps:
Complete and achieve sign-off for Lab 15 (Docker) & Lab 16 (Amazon ECS Blue/Green); build Event-Driven SQS/SNS architecture and monthly report automation.
