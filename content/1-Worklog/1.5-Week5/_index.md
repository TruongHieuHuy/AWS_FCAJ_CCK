---
title: "Week 5 Worklog"
date: 2026-05-04
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Resolve IAM errors, achieve Lab 2 sign-off, and perform EC2/VPC network troubleshooting in Lab 3.
* Design an optimal DynamoDB Single-Table Schema for all Budget Tracker access patterns.
* Configure S3 Buckets and implement S3 Presigned URLs for secure receipt image uploads.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Fix IAM policy issues and achieve **Lab 2** sign-off (VPC & Networking). Standardize AWS architectural diagrams via draw.io. Design DynamoDB Single-Table Schema: define `PK` and `SK` for USER, TRANSACTION, BUDGET. | 06/01/2026 | 06/03/2026 | [DynamoDB Core Components](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html) |
| Thu - Fri | Execute **Lab 3**: troubleshoot Security Groups, Route Tables, and VPC connectivity issues on EC2 instances. Provision S3 Buckets with SSE-S3 encryption and Block Public Access. | 06/04/2026 | 06/05/2026 | [Amazon S3 Presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) |
| Sat - Sun | Implement S3 Presigned URLs (15-min TTL) in C# Lambda for direct client receipt uploads. Integrate `AWSSDK.DynamoDBv2` using `QueryAsync` over `ScanAsync`. Complete Workshop Module 4. | 06/06/2026 | 06/07/2026 | [AWS SDK for .NET - DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DotNetSDKHighLevel.html) |

### Week 5 Achievements:

* Successfully signed off Lab 2 and gained practical VPC network troubleshooting skills in Lab 3.
* Completed Single-Table Schema on DynamoDB, optimizing RCU/WCU consumption for all access patterns.
* Operationalized S3 Presigned URLs: clients upload receipt files directly without incurring Lambda binary processing costs.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
VPC network troubleshooting skills from Lab 3 (identifying missing `0.0.0.0/0` route in EC2 subnet route table) directly inform cloud infrastructure operations. For DynamoDB, Single-Table design requires an **Access-Pattern-First** mindset: assigning `SK=TXN#<timestamp>#<id>` allows efficient range queries without Full Table Scans.

#### Analytical (BA/SA Perspective)
Offloading receipt uploads via S3 Presigned URLs instead of proxying binary streams through Lambda functions significantly reduces compute latency and invocation costs. Completing Lab 2 VPC requirements reinforces team confidence in building isolated cloud storage architectures.

### Next Steps:
Sign off Lab 3 & deploy Lab 4 (Windows/Linux EC2 lifecycle); configure API Gateway REST API, Cognito JWT Authorizer, and 3 core Lambda functions.
