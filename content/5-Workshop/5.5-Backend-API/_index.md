---
title: "Module 5: Backend Core - Lambda & API"
weight: 5
pre: "<b>5.5. </b>"
---

## Module 5: Backend Core: Lambda & API

**Member:** Huy

### 5.1 API Gateway Setup

**Step 1:** AWS Console → API Gateway → Create API

![Create API](/images/5-Workshop/5.5-Backend-API/31.png)
![Choose API type](/images/5-Workshop/5.5-Backend-API/32.png)
![REST API build](/images/5-Workshop/5.5-Backend-API/33.png)

- Choose API type: REST API
- Build

**Step 2:** Create API Details

![API details](/images/5-Workshop/5.5-Backend-API/34.png)

- API name: `BudgetTracketAPI`
- Endpoint type: Regional
- Create API

**Step 3:** Create Resource Structure

- Root → Create resource → Resource name: `api` → Create resource → `/api`
- Create resource → Resource name: `v1` → Create resource → `/api/v1`
- Create resource → Resource name: `auth` → Create resource → `/api/v1/auth`
- Create method: POST → Integration type: Lambda function → Lambda function: (created in step 5.2) → Save

Repeat for these endpoints:
- `/api/v1/transactions` (GET, POST, PUT, DELETE)
- `/api/v1/budgets` (GET, POST)
- `/api/v1/reports` (GET)
- `/api/v1/profile` (GET, PUT, DELETE)
- `/api/v1/ai/categorize` (POST)
- `/api/v1/ai/insights` (GET)
- `/api/v1/ai/chat` (POST, GET, DELETE)

**Step 4:** Enable CORS

![CORS setting](/images/5-Workshop/5.5-Backend-API/35.png)
![Enable CORS confirmation](/images/5-Workshop/5.5-Backend-API/36.png)

- Select the `/api/v1` resource → Actions → Enable CORS
- Default 4XX and 5XX CORS headers: Check
- Replace existing CORS headers: Yes
- Enable CORS and replace existing CORS headers

**Step 5:** Deploy API

![Deploy API](/images/5-Workshop/5.5-Backend-API/37.png)
![Invoke URL](/images/5-Workshop/5.5-Backend-API/38.png)

- Actions → Deploy API
- Deployment stage: `dev`
- Create
- Copy Invoke URL: `https://etqygc1m4d.execute-api.ap-southeast-1.amazonaws.com/dev`

### 5.2 Lambda Functions Setup

![Lambda functions list](/images/5-Workshop/5.5-Backend-API/39.png)

**Step 1:** AWS Console → Lambda → Create function

![Create function](/images/5-Workshop/5.5-Backend-API/40.png)

**Function 1: AuthFunction**

![AuthFunction configuration](/images/5-Workshop/5.5-Backend-API/41.png)

- Function name: `BudgetTracket-AuthFunction-dev`
- Runtime: .NET 8 (C#)
- Architecture: x86_64
- Create function

**Step 2:** Configure Environment Variables

Configuration → Environment variables → Edit. Add variables:

```
DYNAMODB_TABLE=BudgetTracket-dev
COGNITO_USER_POOL_ID=<from-module-7>
COGNITO_CLIENT_ID=<from-module-7>
AWS_REGION=ap-southeast-1
ASPNETCORE_ENVIRONMENT=Production
```

Save.

**Step 3:** Deploy Code

```
cd backend
dotnet build
dotnet lambda package -o
```

AWS Console → Lambda Function → Upload from → .zip file → Select → Save

Repeat for the other Lambda Functions:

![Other Lambda functions deployed](/images/5-Workshop/5.5-Backend-API/42.png)

- TransactionFunction
- BudgetFunction
- ReportFunction
- ProfileFunction
- AiFunction
- NotificationFunction
- MonthlySummaryFunction

**Step 4:** Link Lambda to API Gateway

API Gateway → Resource → Method → Integration request → Lambda function: Select function → Save

![Lambda API Gateway integration](/images/5-Workshop/5.5-Backend-API/43.png)
![Lambda deployment complete](/images/5-Workshop/5.5-Backend-API/44.png)

### 5.3 Test Lambda Locally (Optional)

```
sam local start-api
Server running on http://localhost:3000/api/v1
```

Test endpoint:

```
curl -X GET http://localhost:3000/api/v1/transactions \
  -H "Authorization: Bearer <token>"
```
