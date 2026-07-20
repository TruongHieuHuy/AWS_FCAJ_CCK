---
title: "Week 1 Worklog"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Understand the overall AWS FCAJ program structure and the Cloud Journey learning roadmap.
* Define project objectives and scope for the group project (Serverless Budget Tracker).
* Initialize AWS account, identify and perform Root Cause Analysis (RCA) on account lockout issue.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Study FCAJ orientation materials; map out the AWS Cloud Journey roadmap (Foundation → Serverless → Production). Survey personal finance management needs and define group project scope. | 05/04/2026 | 05/06/2026 | [AWS Cloud Journey Roadmap](https://cloudjourney.awsstudygroup.com/) |
| Thu - Fri | Learn core cloud computing concepts (IaaS/PaaS/SaaS) and the Shared Responsibility Model. Create AWS account with standard security configurations: enable MFA for root, create IAM Admin User, configure AWS CLI. | 05/07/2026 | 05/08/2026 | [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Sat - Sun | Discover account locked post-creation. Perform Root Cause Analysis: inspect email notifications from AWS, review billing settings and IAM policies. Prepare verification documentation for AWS Support Case. | 05/09/2026 | 05/10/2026 | [AWS Support Case Guide](https://docs.aws.amazon.com/awssupport/latest/user/case-management.html) |

### Week 1 Achievements:

* Mastered the learning roadmap and operating guidelines of the FCAJ program.
* Acquired deep understanding of the Shared Responsibility Model between AWS and users.
* Defined group project problem scope and submitted identity verification Support Case to resolve account lockout.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
The immediate account lockout highlights AWS automated fraud detection mechanisms targeting suspicious signals (new IP, unverified billing info). RCA required evaluating IAM Trust Policies, CloudTrail logs, and identity credentials. Key takeaway: enforce root MFA and configure IAM Admin Users with Least Privilege from day one.

#### Analytical (BA/SA Perspective)
From a project risk management standpoint: account issues in week 1 present a critical blocker for the 12-week timeline. Submitting a Support Case immediately demonstrates proactive risk mitigation. This underlines the necessity of contingency planning for development environments before initiating cloud projects.

### Next Steps:
Resolve account lockout completely; complete 5 Onboarding tasks to activate Cloud Credits and finalize group task allocations.
