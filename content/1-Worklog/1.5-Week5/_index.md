---
title: "Week 5 Worklog"
date: 2026-05-04
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Design an optimized DynamoDB Single-Table Schema covering all Budget Tracker Access Patterns.
* Provision S3 Bucket and implement Presigned URL mechanism for secure receipt uploads.
* Integrate AWS SDK DynamoDB into C# Lambda and optimize queries to minimize RCU/WCU consumption.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Design DynamoDB Single-Table Schema: define Partition Key (`PK`) and Sort Key (`SK`) for USER, TRANSACTION, and BUDGET entities. Align schema with Database Engineer to ensure Access Patterns (monthly transactions, per-category budget checks) avoid **Hot Partition** and minimize RCU/WCU consumption. | 06/01/2026 | 06/03/2026 | [DynamoDB Core Components](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html) |
| Thu - Fri | Provision S3 Bucket with security baseline: Block Public Access, Server-Side Encryption (SSE-S3), Bucket Policy scoped to Lambda execution role. Implement Presigned URL (15-min TTL) in C# Lambda — enables clients to upload receipts directly to S3 without proxying through Lambda, reducing invocation cost and avoiding binary data handling. | 06/04/2026 | 06/05/2026 | [Amazon S3 Presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) |
| Sat - Sun | Integrate `AWSSDK.DynamoDBv2` into C# Lambda: use `DynamoDBContext` with `QueryAsync` (not `ScanAsync`) to query by PK — preventing costly Full Table Scans. Configure S3 CORS policy to allow Frontend domain to issue direct PUT requests. | 06/06/2026 | 06/07/2026 | [AWS SDK for .NET - DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DotNetSDKHighLevel.html) |

### Week 5 Achievements:

* Complete Single-Table Schema supporting all Access Patterns with minimized RCU/WCU costs.
* S3 Presigned URL operational: clients upload receipts directly, Lambda never handles binary payloads.
* C# Lambda connecting DynamoDB via `QueryAsync`, avoiding Hot Partition and Full Table Scan pitfalls.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
DynamoDB Single-Table Design mandates **Access-Pattern-First** thinking over Entity-First: instead of separate User and Transaction tables, schema is driven by real query shapes. For example: `PK=USER#userId` + `SK=TRANSACTION#2026-06` retrieves all June transactions in a single targeted Query — no Scan required. Offloading receipt uploads to S3 Presigned URLs eliminates Lambda multipart-form handling, prevents Lambda timeout on large files, and reduces per-GB invocation costs.

#### Analytical (BA/SA Perspective)
The DynamoDB Hot Partition risk is an invisible threat: if many users share the same Partition Key (e.g., an admin account), throughput is bottlenecked at a single partition. Designing PK distribution around `userId` from the outset guarantees **horizontal scalability** — as the user base grows, DynamoDB automatically distributes load uniformly. This is a long-horizon architectural decision: schema migration in DynamoDB post-launch is operationally expensive and disruptive, making early correctness essential.

### Next Steps:
Configure API Gateway REST API with Cognito JWT Authorizer and implement full business logic across all Lambda functions.
