---
title: "Module 10: Monitoring & Operations"
weight: 10
pre: "<b>5.10. </b>"
---

## Module 10: Monitoring & Operations

**Thành viên:** Cả nhóm

### 10.1 CloudWatch Logs

![Danh sách log groups](/images/5-Workshop/5.10-Monitoring/81.png)
![Chi tiết log group](/images/5-Workshop/5.10-Monitoring/82.png)

AWS Console → CloudWatch → Log groups

Log Groups được tạo tự động:
- `/aws/lambda/BudgetTracket-AuthFunction-dev`
- `/aws/lambda/BudgetTracket-TransactionFunction-dev`
- `/aws/lambda/BudgetTracket-BudgetFunction-dev`
- `/aws/lambda/BudgetTracket-ReportFunction-dev`
- `/aws/lambda/BudgetTracket-AiFunction-dev`
- `/aws/lambda/BudgetTracket-ProfileFunction-dev`
- `/aws/lambda/BudgetTracket-NotificationFunction-dev`
- `/aws/lambda/BudgetTracket-MonthlySummaryFunction-dev`

### 10.2 CloudWatch Metrics & Alarms

**Bước 1:** Create Alarm for Lambda Errors

![Create alarm](/images/5-Workshop/5.11-Deployment/83.png)

- CloudWatch → Alarms → Create alarm
- Metric: Lambda → Errors
- Function: `BudgetTracket-AuthFunction-dev`
- Statistic: Sum
- Period: 5 minutes
- Threshold: >= 5
- Action: Send SNS notification
- Create alarm

Ý nghĩa: Nếu AuthFunction có ≥ 5 lỗi trong 5 phút, gửi email cảnh báo.

**Bước 2:** Create Alarm for DynamoDB

- Metric: DynamoDB → ConsumedWriteCapacityUnits
- Table: `BudgetTracket-dev`
- Threshold: >= 80% of provisioned capacity
- Create alarm (tương tự như trên)

Ý nghĩa: Cảnh báo khi approaching DynamoDB write limit.

### 10.3 WAF Monitoring

- WAF & Shield → Web ACLs → `BudgetTracketWAF`
- Monitoring tab
- View blocked requests by rule

### 10.4 Lambda Performance Insights

Xem các chỉ số Lambda invocation qua CloudWatch dashboards để theo dõi duration, error rates và concurrent executions.
