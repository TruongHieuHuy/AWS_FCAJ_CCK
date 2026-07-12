---
title: "Week 9 Worklog"
date: 2026-05-04
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

* Build an Event-Driven asynchronous notification pipeline with Amazon SQS and SNS.
* Implement Idempotency mechanism to prevent duplicate email delivery.
* Configure EventBridge Cron Rule for automated monthly spending report delivery.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Design and deploy Async Notification Pipeline: when `BudgetFunction` detects an over-budget condition, publish message to **Amazon SQS Queue** (Dead Letter Queue configured with maxReceiveCount=3). `NotificationFunction` Lambda consumes SQS messages and triggers email via **Amazon SNS Topic**. SQS Queue acts as buffer, decoupling `BudgetFunction` from email-sending latency. | 06/29/2026 | 07/01/2026 | [Amazon SQS Developer Guide](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html) |
| Thu - Fri | Implement **Idempotency pattern** in `NotificationFunction`: persist SQS `MessageId` to DynamoDB with 24h TTL before sending each email; check for duplicate MessageId before processing — prevents double-send when SQS re-delivers a message under its at-least-once delivery guarantee. Configure **EventBridge Cron Rule** (`cron(0 8 1 * ? *)`) to trigger `MonthlySummaryFunction` at 8 AM UTC on the 1st of each month. | 07/02/2026 | 07/03/2026 | [Amazon EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html) |
| Sat - Sun | Author and complete Workshop **Module 8** (Asynchronous Processing & Notifications): document SNS/SQS architecture, Idempotency lab steps, Dead Letter Queue configuration, and EventBridge Scheduler setup. | 07/04/2026 | 07/05/2026 | [AWS SNS Developer Guide](https://docs.aws.amazon.com/sns/latest/dg/welcome.html) |

### Week 9 Achievements:

* Event-Driven notification pipeline fully operational: budget alerts trigger email successfully via SQS → SNS.
* Idempotency mechanism prevents duplicate emails even when SQS re-delivers messages.
* EventBridge Cron Rule triggers `MonthlySummaryFunction` on schedule.
* Workshop Module 8 complete.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
SQS **at-least-once delivery guarantee** is the correct semantic for notification systems, but introduces duplicate message risk: if Lambda times out after sending an email but before deleting the message from the Queue, SQS will re-deliver — triggering a second email. The Idempotency pattern (DynamoDB MessageId store with TTL) completely eliminates this race condition. Dead Letter Queue with `maxReceiveCount=3` ensures messages don't loop indefinitely when Lambda consistently fails — after 3 retries, messages are routed to DLQ for post-mortem analysis. EventBridge cron expression `cron(0 8 1 * ? *)` operates in UTC — Vietnam timezone offset (+7h) must be accounted for in configuration.

#### Analytical (BA/SA Perspective)
The Async Notification architecture is fundamentally a **resilience design pattern**: decoupling `BudgetFunction` (latency-sensitive, user-facing) from email delivery (latency-tolerant, background) guarantees that email service degradation never propagates to the user-facing transaction entry experience. This exemplifies **Pay-as-you-go Resilience**: SQS pricing is purely message-count based with zero idle cost — making it the financially optimal choice for an application with irregular, bursty notification traffic.

### Next Steps:
Write Unit Tests covering all Lambda functions and configure CloudWatch Dashboard and Alarm monitoring.
