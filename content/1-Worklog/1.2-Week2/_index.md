---
title: "Week 2 Worklog"
date: 2026-05-04
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Resolve AWS account permission lockout completely using a Mitigation Strategy.
* Complete all 5 Onboarding tasks to receive $100 AWS Cloud Credits for the FCAJ program.
* Finalize group role assignments and project workflow for the Serverless Budget Tracker.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Tue | Draft bilingual technical support report and submit AWS Support Case. Consult FCAJ Mentors to investigate root cause. | 05/11/2026 | 05/12/2026 | [AWS Support Center](https://support.console.aws.amazon.com/) |
| Wed - Thu | Receive AWS support feedback. Implement Mitigation Strategy: provision new AWS account to remove environment blocker. Hold group meeting to finalize task assignments for Budget Tracker. | 05/13/2026 | 05/14/2026 | [AWS Account Management](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html) |
| Fri - Sat | Execute Onboarding tasks: **Task 1** — EC2 provisioning & termination; **Task 3** — AWS Budgets threshold alerts; **Task 4** — AWS Lambda hello-world; **Task 5** — Amazon RDS Aurora. Submit Support Case requesting Model Access for Anthropic Claude 3 Haiku (Task 2). | 05/15/2026 | 05/16/2026 | [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| Sun | Receive Model Access approval from AWS. Complete **Task 2**: Amazon Bedrock prompt design & Claude 3 Haiku model inference. Claim $100 AWS Cloud Credits. | 05/17/2026 | 05/17/2026 | [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |

### Week 2 Achievements:

* Successfully unblocked development environment by executing backup account mitigation strategy.
* Completed 5/5 Onboarding tasks 100% and activated $100 FCAJ Cloud Credits.
* Established team workflow and task distribution for the Budget Tracker project.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Navigating IAM Trust Relationship lockouts provided valuable real-world troubleshooting experience. Onboarding Task 4 reinforced the Least Privilege principle by attaching `AWSLambdaBasicExecutionRole`. Crucially, Amazon Bedrock requires explicit Model Access request — a core governance pattern for AI service management on AWS.

#### Analytical (BA/SA Perspective)
Executing a Mitigation Strategy (new account creation) instead of passively waiting for support reflects a **time-to-value optimization** mindset — prioritizing project momentum. Establishing clear role allocation across the team sets a strong foundation for architecture design next week.

### Next Steps:
Implement AWS Budgets & CloudWatch cost governance; attend AWS Community Day 2026; design Serverless Architecture and author Project Proposal.
