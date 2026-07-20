---
title: "Week 11 Worklog"
date: 2026-05-04
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Apply IaC expertise from Lab 10: Author `template.yaml` (AWS SAM) packaging all project infrastructure as IaC.
* Set up an automated CI/CD Pipeline for build, test, and deploy via GitHub Actions using secure OIDC (OpenID Connect) authentication.
* Complete Workshop Module 11 (Deployment Automation) documentation.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Apply CloudFormation IaC practices from Lab 10: Author `template.yaml` (AWS SAM) defining infrastructure as code — `AWS::Serverless::Function` (Lambda), `AWS::DynamoDB::Table` (GSI definitions), `AWS::ApiGateway::RestApi`, `AWS::Cognito::UserPool`, `AWS::SQS::Queue`. Configure SAM Globals. | 07/13/2026 | 07/15/2026 | [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| Thu - Fri | Configure GitHub Actions Workflow (`.github/workflows/deploy.yml`): pipeline stages include **Lint & Test**, **Build** (ReadyToRun), **SAM Package**, **SAM Deploy**. Configure AWS credentials via **OIDC (OpenID Connect)** — zero long-term access keys stored in GitHub Secrets. | 07/16/2026 | 07/17/2026 | [GitHub Actions for AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services) |
| Sat - Sun | Validate end-to-end pipeline: push code → trigger Actions → verify successful deployment. Complete Workshop **Module 11** (Deployment Automation): SAM template walkthrough, GitHub Actions YAML explanation, OIDC setup guide. | 07/18/2026 | 07/19/2026 | [AWS CloudFormation User Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |

### Week 11 Achievements:

* Completed `template.yaml`: entire Budget Tracker infrastructure defined as IaC, reproducible in minutes.
* GitHub Actions Pipeline operational: every push to `main` automatically triggers test → build → deploy.
* OIDC authentication replaces static access keys — zero long-lived credentials in CI/CD pipeline.
* Workshop Module 11 documentation published.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
AWS SAM abstracts CloudFormation learned in Lab 10: `AWS::Serverless::Function` automatically provisions IAM Execution Roles, CloudWatch Log Groups, and API Gateway integrations. Implementing OIDC authentication allows GitHub Actions to request temporary STS credentials via JWT tokens — auto-expiring after each job run for maximum security.

#### Analytical (BA/SA Perspective)
IaC + CI/CD Pipeline embodies operational **DevOps culture**: removing manual deployment human errors. Compressing Time-to-Market from 30-minute manual CLI steps to <5-minute automated zero-downtime pipelines directly increases engineering productivity.

### Next Steps:
Execute User Acceptance Testing (UAT), audit AWS Billing costs, perform Resource Cleanup (Module 12), and prepare presentation slides for final defense.
