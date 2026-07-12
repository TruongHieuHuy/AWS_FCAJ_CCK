---
title: "Module 4: Database & Data Layer"
weight: 4
pre: "<b>5.4. </b>"
---

## Module 4: Database & Data Layer

**Member:** Khiem

### 4.1 DynamoDB Table Creation

![DynamoDB tables](/images/5-Workshop/5.4-Database-Storage/15.png)

**Step 1:** AWS Console → DynamoDB → Tables → Create table

![Create table](/images/5-Workshop/5.4-Database-Storage/16.png)

- Table name: `BudgetTracket-dev`
- Partition key (PK): `userId` (String) — Sort key (SK): `entityId` (String)
- Example items:
  - PK: `USER#user123`, SK: `PROFILE`
  - PK: `USER#user123`, SK: `TXN#2026-01-15#txn001`
  - PK: `USER#user123`, SK: `BUDGET#2026-01#Food`

**Step 2:** Create table

![Table created](/images/5-Workshop/5.4-Database-Storage/17.png)

**Step 3:** Wait for status = ACTIVE

```
# Verify via CLI
aws dynamodb describe-table --table-name BudgetTracket-dev --region ap-southeast-1
```

![Table status ACTIVE](/images/5-Workshop/5.4-Database-Storage/18.png)

### 4.2 DynamoDB Schema Details

Sample Items:

```json
{
  "userId": { "S": "user#abc123" },
  "entityId": { "S": "PROFILE" },
  "email": { "S": "user@example.com" },
  "name": { "S": "John Doe" },
  "currency": { "S": "VND" },
  "notifyBudgetAlert": { "BOOL": true },
  "notifyMonthlyReport": { "BOOL": true },
  "notifyAnomaly": { "BOOL": false },
  "createdAt": { "S": "2026-01-15T10:30:00Z" },
  "updatedAt": { "S": "2026-01-15T10:30:00Z" }
}
```

```json
{
  "userId": { "S": "user#abc123" },
  "entityId": { "S": "TXN#2026-01-15#txn001" },
  "type": { "S": "expense" },
  "description": { "S": "Lunch at Pho restaurant" },
  "amount": { "N": "150000" },
  "category": { "S": "food" },
  "date": { "S": "2026-01-15" },
  "note": { "S": "Business lunch" },
  "receiptUrl": { "S": "s3://bucket/receipts/txn001.jpg" }
}
```

### 4.3 S3 Buckets

![S3 buckets overview](/images/5-Workshop/5.4-Database-Storage/19.png)

**Step 1:** AWS Console → S3 → Create bucket

![Create bucket](/images/5-Workshop/5.4-Database-Storage/20.png)

**Bucket 1: Frontend Hosting**
- Bucket name: `budget-tracket-frontend-dev` (must be globally unique)
- Region: `ap-southeast-1`
- Block all public access: Uncheck (for CloudFront public access)
- Create bucket

![Frontend bucket created](/images/5-Workshop/5.4-Database-Storage/21.png)

**Step 2:** Enable Static Website Hosting

![Bucket properties](/images/5-Workshop/5.4-Database-Storage/22.png)
![Static website hosting setting](/images/5-Workshop/5.4-Database-Storage/23.png)
![Static website hosting enabled](/images/5-Workshop/5.4-Database-Storage/24.png)

- Click into the bucket → Properties → Static website hosting → Edit
- Enable
- Index document: `index.html`
- Error document: `index.html` (for React routing)
- Save

**Bucket 2: Receipt Storage**

![Receipt bucket](/images/5-Workshop/5.4-Database-Storage/25.png)

- Bucket name: `budget-tracket-receipts-dev`
- Region: `ap-southeast-1`
- Block all public access: Check (pre-signed URLs only)
- Create bucket

**Step 3:** Add a lifecycle policy (delete old receipts)

![Lifecycle rules](/images/5-Workshop/5.4-Database-Storage/26.png)

- Click into the bucket → Management → Lifecycle rules → Create lifecycle rule

![Create lifecycle rule](/images/5-Workshop/5.4-Database-Storage/27.png)

- Rule name: `DeleteOldReceipts`
- Apply to all objects
- Expiration: 180 days
- Create rule

### 4.4 Secrets Manager

![Secrets Manager overview](/images/5-Workshop/5.4-Database-Storage/28.png)

**Step 1:** AWS Console → Secrets Manager → Store a new secret

![Store a new secret](/images/5-Workshop/5.4-Database-Storage/29.png)

**Secret 1: Gemini API Key**

![Secret key/value pair](/images/5-Workshop/5.4-Database-Storage/30.png)

- Secret type: Other type of secret
- Key/value: `GEMINI_API_KEY` = `<your-gemini-api-key>`
- Secret name: `budget-tracket/gemini-api-key`
- Store secret
- Copy ARN (used for the Lambda environment)

**Secret 2: Cognito Config** (created after Module 7)
- Key/value: `COGNITO_USER_POOL_ID: <pool-id>`, `COGNITO_CLIENT_ID: <client-id>`
- Secret name: `budget-tracket/cognito-config`

### 4.5 Verify via AWS CLI

Check the DynamoDB table:

![Verify DynamoDB via CLI](/images/5-Workshop/5.4-Database-Storage/30.1.png)

```
aws dynamodb list-tables --region ap-southeast-1
```

Check the S3 buckets:

```
aws s3 ls
```
