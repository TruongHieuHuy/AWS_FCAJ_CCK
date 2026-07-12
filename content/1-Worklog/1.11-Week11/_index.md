---
title: "Week 11 Worklog"
date: 2026-05-04
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:

* Deploy the entire Budget Tracker system as Infrastructure as Code (IaC) using AWS SAM Template.
* Set up an automated CI/CD Pipeline for build, test, and deploy via GitHub Actions.
* Complete Workshop Module 11 (Deployment Automation) documentation.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| Mon - Wed | Author `template.yaml` (AWS SAM): define all infrastructure as IaC — `AWS::Serverless::Function` (Lambda with memory, timeout, environment variables), `AWS::DynamoDB::Table` (with GSI definitions), `AWS::ApiGateway::RestApi`, `AWS::Cognito::UserPool`, `AWS::SQS::Queue`. Configure SAM Globals to eliminate repeated settings across Lambda functions. | 07/13/2026 | 07/15/2026 | [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| Thu - Fri | Configure GitHub Actions Workflow (`.github/workflows/deploy.yml`): pipeline stages include **Lint & Test** (run xUnit tests, fail-fast on failure), **Build** (dotnet publish with ReadyToRun), **SAM Package** (upload artifacts to S3), **SAM Deploy** (apply CloudFormation stack). Configure AWS credentials via **OIDC (OpenID Connect)** — no long-term access keys stored in GitHub Secrets. | 07/16/2026 | 07/17/2026 | [GitHub Actions for AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services) |
| Sat - Sun | Validate end-to-end pipeline: push code → trigger Actions → verify successful deployment. Complete Workshop **Module 11** (Deployment Automation): SAM template walkthrough, GitHub Actions YAML explanation, OIDC setup guide. | 07/18/2026 | 07/19/2026 | [AWS CloudFormation User Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |

### Week 11 Achievements:

* Complete `template.yaml`: entire Budget Tracker infrastructure defined as IaC, reproducible in minutes.
* GitHub Actions Pipeline operational: every push to `main` automatically triggers test → build → deploy.
* OIDC authentication replaces static access keys — zero long-lived credentials in CI/CD pipeline.
* Workshop Module 11 documentation complete.

### Dual-Perspective Reflection:

#### Technical (Cloud Engineer Perspective)
AWS SAM abstracts CloudFormation: `AWS::Serverless::Function` automatically provisions an IAM Execution Role, CloudWatch Log Group, and API Gateway integration — significantly reducing YAML boilerplate. The OIDC implementation is critical from a security standpoint: instead of storing `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` as GitHub Secrets (long-lived credentials that, if leaked, provide persistent AWS access), OIDC allows GitHub Actions to request temporary credentials from AWS STS via a JWT token. Credentials auto-expire after each job — no sensitive credentials are ever persisted in the CI environment.

#### Analytical (BA/SA Perspective)
IaC + CI/CD Pipeline is the operational foundation of **DevOps culture**: every infrastructure change must flow through Git (reviewable), pass automated tests (reliable), and deploy automatically (repeatable) — eliminating manual deployment errors, which are the leading cause of production outages across the industry. From a business perspective, the pipeline compresses **Time-to-Market** for each new feature: from 30-minute manual CLI deployments to <5-minute automated zero-downtime pipelines — a direct productivity multiplier for the engineering team.

### Next Steps:
Execute User Acceptance Testing (UAT), audit AWS Billing costs, and deliver the completed project.
