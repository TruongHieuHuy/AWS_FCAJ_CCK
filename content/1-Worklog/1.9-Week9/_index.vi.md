---
title: "Nhật ký công việc Tuần 9"
date: 2026-05-04
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Xây dựng kiến trúc Event-Driven xử lý thông báo bất đồng bộ với Amazon SQS và SNS.
* Triển khai Idempotency mechanism để ngăn chặn gửi email trùng lặp.
* Thiết lập EventBridge Cron Rule tự động kích hoạt báo cáo chi tiêu hàng tháng.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Thiết kế và triển khai Async Notification Pipeline: khi `BudgetFunction` phát hiện chi tiêu vượt ngưỡng, publish message vào **Amazon SQS Queue** (Dead Letter Queue configured với maxReceiveCount=3). `NotificationFunction` Lambda consume SQS messages và trigger email qua **Amazon SNS Topic**. SQS Queue là buffer giúp decouple `BudgetFunction` khỏi latency của email sending. | 29/06/2026 | 01/07/2026 | [Amazon SQS Developer Guide](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html) |
| Thứ 5 - Thứ 6 | Triển khai **Idempotency pattern** trong `NotificationFunction`: lưu SQS `MessageId` vào DynamoDB với TTL 24h trước khi gửi email; kiểm tra trùng lặp trước mỗi lần gửi — ngăn chặn double-send khi SQS re-deliver message (at-least-once delivery guarantee). Thiết lập **EventBridge Cron Rule** (`cron(0 8 1 * ? *)`) trigger `MonthlySummaryFunction` vào 8h sáng ngày 1 hàng tháng. | 02/07/2026 | 03/07/2026 | [Amazon EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html) |
| Thứ 7 - CN | Soạn thảo và hoàn thiện tài liệu Workshop **Module 8** (Asynchronous Processing & Notifications): mô tả kiến trúc SNS/SQS, lab steps triển khai Idempotency, cấu hình Dead Letter Queue và EventBridge Scheduler. | 04/07/2026 | 05/07/2026 | [AWS SNS Developer Guide](https://docs.aws.amazon.com/sns/latest/dg/welcome.html) |

### Kết quả đạt được tuần 9:

* Event-Driven notification pipeline hoạt động: budget alerts gửi email thành công qua SQS → SNS.
* Idempotency mechanism ngăn chặn duplicate emails kể cả khi SQS re-delivers message.
* EventBridge Cron Rule kích hoạt `MonthlySummaryFunction` đúng lịch.
* Tài liệu Workshop Module 8 hoàn chỉnh.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
SQS **at-least-once delivery guarantee** là thiết kế đúng cho Notification system nhưng tạo ra nguy cơ duplicate messages: nếu Lambda timeout sau khi gửi email nhưng trước khi xóa message khỏi Queue, SQS sẽ re-deliver và gửi email lần 2. Idempotency pattern với DynamoDB (store MessageId + TTL) giải quyết hoàn toàn vấn đề này. Dead Letter Queue với `maxReceiveCount=3` đảm bảo message không bị "stuck" vô hạn khi Lambda liên tục fail — message sau 3 lần retry sẽ chuyển vào DLQ để debug sau. EventBridge Cron expression `cron(0 8 1 * ? *)` là UTC time, cần tính toán offset múi giờ Việt Nam (+7h) khi configure.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Kiến trúc Async Notification không chỉ là giải pháp kỹ thuật — nó là **resilience pattern** quan trọng: decoupling `BudgetFunction` (latency-sensitive, user-facing) khỏi email-sending (latency-tolerant, background) đảm bảo việc email service chậm hoặc fail không bao giờ ảnh hưởng đến trải nghiệm nhập liệu giao dịch. Đây là nguyên lý **Pay-as-you-go Resilience**: SQS chỉ tính phí theo số message, không có chi phí idle server — phù hợp tuyệt đối với ứng dụng có traffic không đều.

### Kế hoạch tuần tiếp theo:
Viết Unit Tests bao phủ toàn bộ Lambda functions, thiết lập CloudWatch Dashboard và Alarm monitoring.
