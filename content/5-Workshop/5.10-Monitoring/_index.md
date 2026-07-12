---
title: "Module 10: Monitoring & Operations"
weight: 10
pre: "<b>5.10. </b>"
---

## Module 10: Monitoring & Operations

**Member:** Whole team

### 10.1 CloudWatch Logs

![CloudWatch log groups](/images/5-Workshop/5.10-Monitoring/81.png)
![Log group details](/images/5-Workshop/5.10-Monitoring/82.png)

AWS Console → CloudWatch → Log groups

Log groups created automatically:
- `/aws/lambda/BudgetTracket-AuthFunction-dev`
- `/aws/lambda/BudgetTracket-TransactionFunction-dev`
- `/aws/lambda/BudgetTracket-BudgetFunction-dev`
- `/aws/lambda/BudgetTracket-ReportFunction-dev`
- `/aws/lambda/BudgetTracket-AiFunction-dev`
- `/aws/lambda/BudgetTracket-ProfileFunction-dev`
- `/aws/lambda/BudgetTracket-NotificationFunction-dev`
- `/aws/lambda/BudgetTracket-MonthlySummaryFunction-dev`

### 10.2 CloudWatch Metrics & Alarms

**Step 1:** Create an Alarm for Lambda Errors

![Create alarm](/images/5-Workshop/5.11-Deployment/83.png)

- CloudWatch → Alarms → Create alarm
- Metric: Lambda → Errors
- Function: `BudgetTracket-AuthFunction-dev`
- Statistic: Sum
- Period: 5 minutes
- Threshold: >= 5
- Action: Send SNS notification
- Create alarm

Meaning: if AuthFunction has ≥ 5 errors in 5 minutes, send an email alert.

**Step 2:** Create an Alarm for DynamoDB

- Metric: DynamoDB → ConsumedWriteCapacityUnits
- Table: `BudgetTracket-dev`
- Threshold: >= 80% of provisioned capacity
- Create alarm (same steps as above)

Meaning: alert when approaching the DynamoDB write limit.

### 10.3 WAF Monitoring

- WAF & Shield → Web ACLs → `BudgetTracketWAF`
- Monitoring tab
- View blocked requests by rule

### 10.4 Lambda Performance Insights

Get Lambda invocation metrics and review CloudWatch dashboards to track Lambda duration, error rates, and concurrent executions.
