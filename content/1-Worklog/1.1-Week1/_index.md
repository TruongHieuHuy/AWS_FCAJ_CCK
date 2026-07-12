---
title: "Week 1 Worklog"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Research FCAJ program orientation and map the AWS Cloud Journey learning path.
* Provision personal AWS account with security best practices.
* Perform Root Cause Analysis (RCA) on newly created account lock.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Research FCAJ orientation materials; map the AWS Cloud Journey learning roadmap by phase (Foundation → Serverless → Production). | 05/04/2026 | 05/06/2026 | [AWS Cloud Journey Roadmap](https://cloudjourney.awsstudygroup.com/) |
| Thu - Fri | Study IaaS/PaaS/SaaS service models and the Shared Responsibility Model. Provision AWS account with security baseline: enable root MFA, create IAM Admin User, configure AWS CLI with access key. | 05/07/2026 | 05/08/2026 | [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Sat - Sun | Discover account locked post-creation. Execute Root Cause Analysis: review AWS notification emails, audit billing configuration and IAM policies. Compile identity verification documents for AWS Support Case submission. | 05/09/2026 | 05/10/2026 | [AWS Support Case Guide](https://docs.aws.amazon.com/awssupport/latest/user/case-management.html) |

### Week 1 Achievements:

* Mastered the FCAJ learning roadmap and program operational guidelines.
* Understood the Shared Responsibility Model and clear demarcation of AWS vs. user security responsibilities.
* Identified the account lock root cause and prepared complete verification documentation for Support Case.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
The immediate account lockout revealed AWS's automated fraud detection mechanisms that flag anomalies such as new IP addresses and missing billing info. The RCA process required analyzing IAM Trust Policies and reviewing any available CloudTrail logs. Key engineering takeaway: always enforce MFA on root accounts and provision a scoped IAM Admin User following IAM Least Privilege principles at initialization to prevent lockout scenarios.

#### Analytical (BA/SA Perspective)
From a project risk management perspective, a Day-1 account lockout creates a critical blocker for the entire 12-week delivery schedule. The decision to file a Support Case immediately rather than waiting passively demonstrates proactive risk mitigation. This incident underscores the necessity of a contingency plan for development environments — including a backup account strategy — before commencing any Cloud-native project.

### Next Steps:
Resolve account lockout; complete 5 Onboarding tasks to activate Cloud Credits and begin hands-on Lab practice.
