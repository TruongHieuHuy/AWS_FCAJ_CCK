---
title: "Week 9 Worklog"
date: 2026-05-04
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

* Complete 100% sign-off for Lab 15 (Docker Containerization) & Lab 16 (Amazon ECS, Blue/Green Deployment).
* Build Event-Driven asynchronous notification architecture with Amazon SQS and SNS, enforcing Idempotency patterns.
* Configure EventBridge Cron Rules for automated monthly reports and advance personal Workshop project deliverables.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Complete sign-off for **Lab 15** (Docker Containerization) and **Lab 16** (Amazon ECS, Blue/Green Deployment). Fix inter-lab resource link breaks. Configure **Amazon SQS Queue** and **Amazon SNS Topic** budget alert pipelines. | 06/29/2026 | 07/01/2026 | [Amazon SQS Developer Guide](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html) |
| Thu - Fri | Deploy **Idempotency pattern** in `NotificationFunction`: record SQS `MessageId` in DynamoDB with 24h TTL prior to dispatching email to prevent duplicates. Configure **EventBridge Cron Rule** (`cron(0 8 1 * ? *)`) to trigger `MonthlySummaryFunction`. | 07/02/2026 | 07/03/2026 | [Amazon EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html) |
| Sat - Sun | Synthesize group project architecture workflow diagrams. Code and write personal Workshop Web report. Complete Workshop Module 8 (Asynchronous Processing). | 07/04/2026 | 07/05/2026 | [AWS SNS Developer Guide](https://docs.aws.amazon.com/sns/latest/dg/welcome.html) |

### Week 9 Achievements:

* Achieved 100% completion and sign-off for the entire 16-lab AWS curriculum.
* Operational Event-Driven notification pipeline: budget alerts deliver emails via SQS → SNS reliably with Idempotency duplicate protection.
* EventBridge Cron Rule automates monthly summary reports; Module 8 published alongside personal Web report milestones.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Signing off Labs 15 & 16 for Docker & Amazon ECS Blue/Green Deployments rounds out containerization capabilities. In Serverless architectures, SQS at-least-once delivery requires Idempotency handling via DynamoDB (MessageId + TTL) to prevent duplicate email dispatches.

#### Analytical (BA/SA Perspective)
Completing all 16 AWS Labs marks a pivotal achievement in the internship program. Asynchronous notification pipelines serve as critical resilience patterns, eliminating background email processing latency from user-facing transaction entry flows.

### Next Steps:
Achieve 100% project sign-off for both Group and Personal projects; audit and synchronize all documentation (Proposal, Blog, Workshop); study AWS Well-Architected Framework.
