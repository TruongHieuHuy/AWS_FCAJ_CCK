---
title: "Week 12 Worklog"
date: 2026-05-04
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:

* Execute comprehensive User Acceptance Testing (UAT) and audit AWS Billing costs.
* Perform Resource Cleanup following Workshop Module 12.
* Compile the final internship report and design presentation slides for the evaluation board.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Tue | Execute **User Acceptance Testing (UAT)**: validate all real-user flows end-to-end — Cognito sign-up/login, transaction entry with AI auto-categorization, budget alert via email, monthly report generation. Audit **AWS Cost Explorer** and Billing Dashboard: identify unnecessary cost drivers (idle NAT Gateway charges, unlimited CloudWatch Log Group retention). | 07/20/2026 | 07/21/2026 | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| Wed | Execute **Resource Cleanup** per Module 12: delete CloudFormation Stack (auto-removes all SAM-managed resources), empty and delete S3 Buckets, revoke Cognito App Clients, disable CloudFront Distribution before deletion. Confirm zero billable resources remain after cleanup. | 07/22/2026 | 07/22/2026 | [AWS Resource Cleanup Guide](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) |
| Thu - Fri | Author **Final Internship Report**: summarize 12-week progression (Setup → Architecture → Backend → AI/Security → Automation → Handover), quantify outcomes (number of Lambda functions, test coverage %, Cold Start improvement, cost reduction figures). Design **Presentation Slides** with architecture diagrams, live demo screenshots, and real-world engineering lessons. | 07/23/2026 | 07/25/2026 | — |

### Week 12 Achievements:

* UAT complete — all user flows validated against spec, zero critical bugs.
* Resource Cleanup finalized — zero billable resources remain post-internship.
* Final internship report and presentation slides ready for defense.
* Complete 12-Module Workshop documentation published and available as reference material.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Resource Cleanup is a critical but often overlooked engineering discipline: deleting a CloudFormation Stack must follow correct dependency order (consumer before provider) to avoid dependency errors. Several resources require manual pre-deletion steps — S3 Buckets must be emptied before Stack deletion, CloudFront Distributions must be disabled before removal. AWS Cost Explorer analysis during UAT revealed a **cost anomaly**: NAT Gateway charges ~$0.045/hour regardless of traffic — for dev/test environments, replacing NAT Gateway with VPC Endpoints is a concrete cost optimization opportunity worth ~$32/month at idle.

#### Analytical (BA/SA Perspective)
The final internship report is not an academic exercise — it is the **first professional portfolio artifact** of an engineer's career. Quantifying outcomes with specific metrics (e.g., "Cold Start reduced 70% from 3.5s to 800ms", "Pay-per-use Lambda model vs. always-on EC2 reduces baseline compute cost by ~90% at low traffic") carries far more weight than generic descriptions. The defense presentation is a live **Technical Storytelling** exercise: translating complex architectural decisions into a clear, compelling narrative for a mixed technical and non-technical audience — a foundational skill for any Solution Architect.

### Next Steps:
Complete the FCAJ internship program. Continue along the AWS Certification path (AWS Solutions Architect Associate) and contribute back to the community through open-source documentation.
