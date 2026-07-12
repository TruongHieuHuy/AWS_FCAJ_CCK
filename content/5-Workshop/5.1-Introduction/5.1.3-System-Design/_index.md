---
title: "5.1.3 Detailed System Design"
weight: 3
chapter: false
---


### 1. Database Design

Instead of using a traditional Relational Database divided into multiple complex tables, the system chooses Amazon DynamoDB with a **`Single-Table Design`** strategy.

The principle of this design is to store multiple types of entities (Users, Transactions, Budgets) within a single table to thoroughly optimize the Access Pattern, reduce hardware costs, and limit expensive JOIN operations. Data is managed by a key pair: **`Partition Key (PK)`** and **`Sort Key (SK)`**.

**Design Example:**
- User Profile record: `PK=USER#123`, `SK=PROFILE`
- Transaction record 1: `PK=USER#123`, `SK=TXN#20240701-001`
- Transaction record 2: `PK=USER#123`, `SK=TXN#20240701-002`
- Food budget record: `PK=USER#123`, `SK=BUDGET#food`

Thanks to this structure, with just a single Query command on `PK=USER#123`, the system can fetch the entire lifecycle data of a user.

### 2. API Design

The system provides a set of RESTful APIs strictly adhering to communication standards:
- **`GET /transactions`**: Retrieve transaction list (Success status: `200 OK`)
- **`POST /transactions`**: Create a new transaction (Success status: `201 Created`)
- **`PUT /transactions/{id}`**: Update information (Success status: `200 OK`)
- **`DELETE /transactions/{id}`**: Delete a record (Success status: `204 No Content`)

**Standard Error Code Handling:**
- `400 Bad Request`: Incorrect input data format.
- `401 Unauthorized`: Token is missing, incorrect, or expired.
- `403 Forbidden`: Token is valid but the user lacks permission to access the resource.
- `500 Internal Server Error`: Unexpected error arising from the Server.

### 3. Authentication Flow

Security is established at the highest level via the **`OAuth2`** and **`OpenID Connect (OIDC)`** protocols.

- The browser requests authentication using Username/Password via Amazon Cognito.
- Upon success, Cognito returns a **`JWT`** token set including: `ID Token` (user identity information), `Access Token` (authorization key to call APIs), and `Refresh Token` (used to fetch a new Access Token when expired without needing to re-login).
- API Requests to API Gateway must contain the string `Authorization: Bearer <Access_Token>`.
- API Gateway acts as the Authorizer, verifying the integrity of the **`JWT`** before allowing Lambda to execute tasks (Delegated Authorization).

### 4. Comprehensive Security Design

Besides the authentication flow, the application's protective armor is fortified by these principles:

- **Least Privilege:** AWS resources like Lambda or API Gateway are granted just enough IAM permissions to perform specific functions, preventing privilege escalation risks.
- **HTTPS & SSL/TLS:** All connection traffic via CloudFront or API Gateway must be encrypted in-transit using ACM certificates.
- **Origin Access Control (OAC):** Prevents users from directly accessing the S3 Bucket, forcing all access to go through CloudFront's cache layer.
- **WAFv2:** A layer 7 protection firewall, setting rules against bad bots, SQL Injection, XSS...
- **Secrets Manager:** Safely manages secret keys (Gemini API Key), completely eliminating hard-coded credentials in the application.

### 5. Notification Architecture

Adhering to the principles of **Loose Coupling** and **Asynchronous Processing**, we DO NOT use the primary Lambda to send Emails directly (which easily causes Timeouts).

Instead, the system utilizes the combined power of Amazon SNS and Amazon SQS:
- Lambda creates a notification and pushes the message to an **SNS Topic** (Publisher).
- SNS fans out that message into an **SQS Queue**.
- An independent Lambda Worker (Consumer) pulls the message from the SQS Queue to execute sending the Email via the SES service.
- This architecture creates a safe "buffer", supports automatic retries, and categorizes failed messages into a Dead Letter Queue (DLQ) for later processing.
