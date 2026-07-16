---
title: "5.1.2 Serverless Architecture & Data Flow"
weight: 2
chapter: false
---


### 1. Overview of AWS Serverless

**Serverless** is a cloud computing execution model where developers can focus entirely on writing code without worrying about managing, configuring, or maintaining physical servers. AWS automatically handles scaling, load balancing, OS patching, and applies a **"Pay-as-you-go"** billing model (only paying for what is actually used, down to the millisecond).

This model is the perfect piece for an **Event-driven Architecture**. Every action (like calling an API, uploading a file, changing data) triggers a corresponding handler function (Function-as-a-Service - FaaS).

### 2. AWS Service Ecosystem in the Project

The Budget Tracker project utilizes a powerful ecosystem of Managed Services:

- **AWS Lambda (Compute):** The heart of the business logic. Handles saving transactions, calling AI, and sending notifications without running a server 24/7.
- **Amazon API Gateway (API Layer):** Acts as the "front door", receiving HTTP(S) requests, managing routing, authentication, quotas, and automatically directing them to the corresponding Lambda functions.
- **Amazon DynamoDB (Database):** A fully-managed NoSQL database with millisecond latency. Applies Single-Table Design for ultra-fast user and transaction data retrieval.
- **Amazon Cognito (Auth):** Identity service. Provides the login flow and issues OAuth2/OIDC standard JWT tokens.
- **Amazon S3 & CloudFront (Frontend Delivery):** S3 stores the ReactJS code. CloudFront acts as a global CDN with 750+ Edge locations, ensuring lightning-fast page loads and security using Origin Access Control (OAC).
- **Amazon Route 53 & WAF (Networking & Security):** Route 53 routes DNS. WAF acts as a shield protecting the application from common web attacks (SQLi, XSS, Botnets).
- **Amazon SNS & SQS (Messaging):** Decoupling the system architecture. SNS is used to Publish notifications, SQS acts as a Queue ensuring zero data loss and asynchronous processing (e.g., sending emails).
- **Amazon EventBridge (Event Bus):** Periodic scheduling (cron jobs) or orchestrating complex event flows.
- **Amazon CloudWatch (Monitoring):** A comprehensive monitoring center for all metrics, logs, and Alarms.
- **AWS Secrets Manager (Security):** A secure storage for connection strings and API Keys (e.g., Google Gemini API Key), minimizing hard-code risks.

### 3. System Architecture Explanation

![Budget Tracker Architecture Diagram](/images/5-Workshop/5.1-Introduction/architecture.jpg)

The system is designed following a **Multi-layer** model to maximize independence, ease of upgrading, and maintenance:

1. **Frontend Layer:** A React SPA (Single Page Application), hosted on S3 and delivered via CloudFront's Edge network.
2. **API Layer:** API Gateway intercepts all traffic flows, verifying authentication via the Cognito authorizer before allowing deeper system access.
3. **Business Logic Layer:** Lambda functions handle independent business logic in a microservices approach (Auth, Transactions, Budget, AI).
4. **Data Layer:** A single DynamoDB table containing data for the entire application (Single-Table Design).
5. **AI Layer:** Lambda interacts with Google Gemini Flash 1.5 to automatically categorize transactions.
6. **Notification Layer:** An asynchronous processing flow of SNS -> SQS -> Lambda to send notifications without increasing the primary API's latency.

### 4. Step-by-Step Data Flow

Below is an illustrative example of how data flows through the system when executing a core function:

**Scenario: A user creates a new expense transaction**

- **Step 1 (Authentication):** The React app sends a `POST /transactions` attaching the JWT string in the Authorization Header.
- **Step 2 (Verification):** API Gateway receives it and sends the JWT to Cognito for authentication. If valid, it forwards the request to the transaction-handling Lambda function.
- **Step 3 (Data Processing):** Lambda receives the payload, checks business logic, and saves the transaction record to the DynamoDB table with the structure PK=USER#ID, SK=TXN#ID.
- **Step 4 (AI Analysis):** Another Lambda function is triggered (or processed asynchronously via EventBridge), calling the Google Gemini API to read the transaction description, assign a Category label (e.g., "Groceries", "Utilities"), and update DynamoDB.
- **Step 5 (Sending Notification):** The initial Lambda publishes a message indicating a new transaction to an SNS Topic.
- **Step 6 (Asynchronous SQS):** SNS pushes the message into an SQS Queue. A Lambda Consumer will pull the message from SQS to proceed with sending a confirmation Email/SMS to the user, ensuring the API returns a result (201 Created) almost instantly without waiting for the email to finish sending.
- **Step 7 (Monitoring):** Throughout the process, CloudWatch continuously records response times, API call counts, and error logs if any.
