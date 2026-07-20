---
title: "Nhật ký công việc Tuần 9"
date: 2026-05-04
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Triển khai và nghiệm thu 100% Lab 15 (Docker Containerization) & Lab 16 (Amazon ECS, Blue/Green Deployment).
* Xây dựng kiến trúc Event-Driven xử lý thông báo bất đồng bộ với Amazon SQS và SNS, áp dụng cơ chế Idempotency.
* Thiết lập EventBridge Cron Rule tự động chạy báo cáo tháng và hoàn thiện dự án Workshop cá nhân.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Triển khai và nghiệm thu thành công bài **Lab 15** (Docker Containerization) và bài **Lab 16** (Amazon ECS, Blue/Green Deployment). Khắc phục sự cố đứt gãy tài nguyên giữa các bài Lab. Thiết lập **Amazon SQS Queue** và **Amazon SNS Topic** gửi mail cảnh báo ngân sách. | 29/06/2026 | 01/07/2026 | [Amazon SQS Developer Guide](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html) |
| Thứ 5 - Thứ 6 | Triển khai **Idempotency pattern** trong `NotificationFunction`: lưu SQS `MessageId` vào DynamoDB với TTL 24h trước khi gửi mail, chống gửi trùng lặp. Thiết lập **EventBridge Cron Rule** (`cron(0 8 1 * ? *)`) tự động trigger `MonthlySummaryFunction` ngày 1 hàng tháng. | 02/07/2026 | 03/07/2026 | [Amazon EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html) |
| Thứ 7 - CN | Tổng hợp sơ đồ Workflow kiến trúc chuẩn cho dự án nhóm. Tập trung lập trình và viết báo cáo Web cho dự án Workshop cá nhân. Complete Module 8 Workshop (Asynchronous Processing). | 04/07/2026 | 05/07/2026 | [AWS SNS Developer Guide](https://docs.aws.amazon.com/sns/latest/dg/welcome.html) |

### Kết quả đạt được tuần 9:

* Nghiệm thu thành công 100% toàn bộ chuỗi 16 bài thực hành AWS Labs.
* Event-Driven notification pipeline hoạt động: cảnh báo ngân sách gửi email qua SQS → SNS ổn định với cơ chế Idempotency chống trùng mail.
* EventBridge Cron Rule kích hoạt báo cáo tháng tự động, hoàn thành Module 8 Workshop và tiến độ báo cáo Web cá nhân.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Kiến thức containerization từ Lab 15-16 giúp mở rộng hiểu biết về Microservices ngoài Serverless. Áp dụng **Idempotency Pattern với DynamoDB TTL (MessageId deduplication)** trong SQS consumer Lambda đảm bảo dù SQS delivery retry nhiều lần thì email cảnh báo budget cũng chỉ được gửi đúng 1 lần duy nhất cho người dùng.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Nghiệm thu 100% 16 AWS Labs đánh dấu sự trưởng thành vượt bậc về kỹ năng hạ tầng Đám mây. Luồng thông báo Event-Driven giúp phân tách mối quan tâm (Decoupling): việc tính toán budget alert được xử lý ngầm ở background mà không làm tăng độ trễ response của API thêm bất kỳ ms nào.

### Kế hoạch tuần tiếp theo:
Hoàn tất 100% dự án nhóm & cá nhân, rà soát đồng bộ hóa tài liệu (Proposal, Blog, Workshop), nghiên cứu AWS Well-Architected Framework.
