---
title: "5.1.4 Operations & Deployment Strategy"
weight: 4
chapter: false
---


### 1. Infrastructure Deployment Strategy

To ensure consistency and automation in management, the project applies the Infrastructure as Code (IaC) model and CI/CD pipelines:

- **Infrastructure as Code (IaC):** All resources (Lambda, DynamoDB, API Gateway) are declared as source code via **AWS SAM** (Serverless Application Model). With just `template.yaml` files, we can deploy a new environment in minutes.
- **CI/CD Pipeline:** Uses **GitHub Actions** to automate the Build -> Test -> Deploy chain. Every valid commit to the `main` branch triggers the pipeline to compile the C# .NET source code, package the React Frontend, and smoothly deploy the SAM infrastructure to Dev/Prod environments.
- **Safe Rollback:** The CloudFormation feature (the foundation of SAM) supports automatic rollback, returning the system to its previous safe state if an error occurs during deployment.

### 2. System Testing Strategy

Software quality is ensured through a multi-level testing pyramid:

- **Unit Testing:** Tests the local logic of each Lambda function, Mocking the DynamoDB database. Helps detect business processing logic errors early.
- **Integration Testing:** Verifies the seamless connection between Lambda and DynamoDB, Lambda and Cognito within a test/staging environment.
- **E2E Testing (End-to-End):** Simulates real user experiences using Automation tools, ensuring the scenario from Login -> Generating API -> Writing to Database operates flawlessly.
- **Continuous Testing:** Attaches all test scenarios to the CI/CD pipeline to block bug-containing updates from being pushed to Production.

### 3. Monitoring Strategy

Every movement of the system is placed under the control of Amazon CloudWatch:

- **Logs Insights:** Logs detailed progress of API Gateway calls, Lambda processing, and Cognito authentication.
- **Metrics Dashboard:** Measures real-time system health with indicators such as Request count, Latency, Error Rate, and DynamoDB Consumed Capacity.
- **Alarms:** Sets limit thresholds (e.g., Lambda errors exceeding 5 times/minute). CloudWatch Alarms will trigger SNS to send urgent SMS/Email notifications to the administration team.

### 4. Best Practices

To maintain a robust long-term project, the system strictly adheres to the following principles:

- **Naming Convention:** Clearly demarcates resource names by environment, for example: `BudgetTracker-dev-table` and `BudgetTracker-prod-table`.
- **Environment Variables:** Absolutely no hard-coding resource names or configurations. Parameterize everything.
- **Idempotency:** API design (especially creating new transactions) capable of self-identifying duplicate requests, ensuring that if a Client accidentally resends a request (due to network drop), the transaction is not duplicated in the Database.
- **Exception Handling:** Wraps all dangerous logic in Try/Catch blocks. Ensures detailed error logs are printed instead of throwing raw errors to end-users.
- **API Versioning:** Designs Endpoints in the form of `/api/v1/...` to easily upgrade or change data structures in the `/v2/` version without breaking the application for users on the old version.
