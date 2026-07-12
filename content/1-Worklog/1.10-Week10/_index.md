---
title: "Week 10 Worklog"
date: 2026-05-04
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

* Final system review and documentation synchronization (Proposal, Blog, Workshop).
* Study AWS Well-Architected Framework to self-assess and improve architecture.
* Finalize and update personal Worklog.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Tue | Execute Final Review across all project deliverables: identify critical inconsistency between Proposal, Blog, and Workshop — each document describes the architecture from a different perspective, violating the **Single Source of Truth** principle. Convene Sync-up Meeting with full team to lock down the canonical architecture, unify terminology, and standardize diagrams. | 07/06/2026 | 07/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |
| Wed - Thu | Refactor the entire documentation system: update Proposal with ratified architecture, synchronize Blog and Workshop to share one authoritative Architecture Diagram and Technology Stack. Enforce Single Source of Truth: all future architecture changes must originate at one canonical location and propagate outward. | 07/08/2026 | 07/09/2026 | [Documentation Best Practices](https://www.writethedocs.org/guide/docs-as-code/) |
| Fri | Finalize and package individual project: verify deployment, validate Web UI flows, update personal Worklog through Week 10. | 07/10/2026 | 07/10/2026 | — |
| Sat - Sun | Study **AWS Well-Architected Framework**: assess Budget Tracker against two pillars — **Security Pillar** (IAM Least Privilege per function, S3 encryption, Cognito MFA) and **Cost Optimization Pillar** (Lambda memory right-sizing, DynamoDB on-demand vs. provisioned, SQS vs. polling). Produce improvement backlog for Weeks 11-12. | 07/11/2026 | 07/12/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |

### Week 10 Achievements:

* Full documentation suite (Proposal, Blog, Workshop) synchronized to a single canonical architecture.
* Individual project finalized with stable deployment.
* Well-Architected assessment completed; concrete improvement items identified for Weeks 11-12.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
Assessing the project against the AWS Well-Architected Security Pillar surfaced actionable improvements: Lambda Execution Roles are over-permissioned (all functions sharing one broad role, violating Least Privilege), S3 Versioning is disabled, and CloudTrail is not enabled for API call auditing. The Cost Optimization Pillar highlighted that Lambda's default 256MB memory allocation may not be optimal — Lambda Power Tuning can identify the cost/performance sweet spot, a concrete optimization to apply in Week 11.

#### Analytical (BA/SA Perspective)
The late-stage documentation inconsistency discovery was a **project management near-miss**: had it gone undetected, the submitted report and demo slides would contradict the live system — critically undermining credibility before the evaluation board. The immediate Sync-up + Refactoring response demonstrates **documentation as a first-class deliverable**: documentation deserves the same rigor, review, and maintenance discipline as production code.

### Next Steps:
Deploy Infrastructure as Code (IaC) with AWS SAM Template and set up automated CI/CD Pipeline via GitHub Actions.
