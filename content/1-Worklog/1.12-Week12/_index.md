---
title: "Week 12 Worklog"
date: 2026-05-04
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

* Execute comprehensive User Acceptance Testing (UAT) and audit AWS Billing costs.
* Perform Resource Cleanup releasing 100% of billable AWS Cloud resources per Workshop Module 12.
* Compile final internship report.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Tue | Execute **User Acceptance Testing (UAT)**: test end-to-end user journeys — Cognito Auth, transaction entry with AI auto-categorization, budget email alerts, monthly reports. Audit **AWS Cost Explorer** and Billing Dashboard to identify non-essential resource costs. | 07/20/2026 | 07/21/2026 | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| Wed | Execute **Resource Cleanup** per Module 12: delete CloudFormation Stack (auto-deleting SAM resources), empty S3 Buckets, revoke Cognito App Clients, disable CloudFront Distributions prior to deletion. Confirm 0% billable resources remain. | 07/22/2026 | 07/22/2026 | [AWS Resource Cleanup Guide](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) |
| Thu - Fri | Author **Final Internship Report**: summarize 12-week roadmap (Setup → AWS Labs 1-16 → Architecture → Backend → AI/Security → Automation → Handover), quantifying concrete metrics. | 07/23/2026 | 07/25/2026 | — |

### Week 12 Achievements:

* UAT complete — all user flows meet spec requirements with zero critical bugs.
* Resource Cleanup complete — zero billable resources remain on AWS Cloud post-internship.
* Final Internship Report compiled.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Resource Cleanup is a critical operational discipline: deleting CloudFormation Stacks in dependency order (Consumer before Provider). Emptying S3 buckets and disabling CloudFront distributions beforehand avoids dependency lockouts. AWS Cost Explorer enables effective detection of cost anomalies.

#### Analytical (BA/SA Perspective)
The final internship report constitutes an engineer's **first professional portfolio**. Quantifying achievements (70% Cold Start reduction, 100% of 16 AWS Labs completed, automated CI/CD) proves real-world capability. The final defense provides an avenue for **Technical Storytelling**, communicating solution value effectively.

### Next Steps:
Successfully conclude the AWS FCAJ internship program. Prepare for the AWS Certified Solutions Architect Associate (SAA-C03) exam and continue open-source community contributions.
