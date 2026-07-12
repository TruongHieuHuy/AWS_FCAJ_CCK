---
title: "Week 2 Worklog"
date: 2026-05-04
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Resolve AWS account permission lockout using a Mitigation Strategy.
* Complete all 5 Onboarding tasks to activate FCAJ Cloud Credits.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Tue | Draft bilingual technical report and submit AWS Support Case requesting account permission audit. Monitor and respond to identity verification emails from the AWS Trust & Safety team. | 05/11/2026 | 05/12/2026 | [AWS Support Center](https://support.console.aws.amazon.com/) |
| Wed - Thu | Receive AWS response. Consult FCAJ mentors and coordinate with team to isolate the system error. Deploy Mitigation Strategy: provision a new AWS account to eliminate the project blocker. | 05/13/2026 | 05/14/2026 | [AWS Account Management](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html) |
| Sat | Execute Onboarding sequence: **Task 1** — Provision and terminate EC2 instance; **Task 3** — Configure AWS Budgets cost-threshold alerts; **Task 4** — Deploy Lambda hello-world function; **Task 5** — Provision Amazon RDS Aurora cluster. Identify missing IAM permissions for Bedrock (Task 2); file Support Case requesting Model Access for Anthropic Claude 3 Haiku. | 05/16/2026 | 05/16/2026 | [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| Sun | Receive Model Access approval from AWS. Complete **Task 2**: experiment with Amazon Bedrock — design prompts and test inference with Anthropic Claude 3 Haiku model. | 05/17/2026 | 05/17/2026 | [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |

### Week 2 Achievements:

* Eliminated environment blocker by provisioning a backup AWS account as contingency.
* Completed 5/5 Onboarding tasks and successfully activated FCAJ Cloud Credits.
* Mastered EC2, Lambda, and RDS Aurora provisioning flows; understood Bedrock Model Access governance.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
The IAM Trust Relationship lockout is a real-world scenario: AWS applies automated protection when detecting anomalies during account registration. Processing Onboarding Task 4 (Lambda) reinforced the IAM Least Privilege principle — the Lambda execution role must be scoped to `AWSLambdaBasicExecutionRole` only. Notably, Amazon Bedrock's manual Model Access requirement is a deliberate AI governance mechanism, not a system bug — understanding this distinction is critical for production deployments.

#### Analytical (BA/SA Perspective)
The decision to execute a Mitigation Strategy (new account) rather than waiting on the Support Case demonstrates **time-to-value optimization** — preserving project momentum over pursuing an ideal solution. Sharing the Bedrock Model Access resolution with fellow FCAJ members is a concrete knowledge transfer action that reduces duplicated troubleshooting effort across the team — a measurable contribution to overall program delivery speed.

### Next Steps:
Convene team architecture workshop for Budget Tracker; draft wireframes and compose the Project Proposal.
