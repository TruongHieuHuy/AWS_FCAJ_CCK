---
title: "Nhật ký công việc Tuần 7"
date: 2026-05-04
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Nghiệm thu chuỗi thực hành từ Lab 4 đến Lab 9 (IAM, EC2-RDS, Auto Scaling, ALB, Budgets, CloudWatch) và khởi động Lab 10 IaC.
* Giải quyết các lỗi CORS và JWT parsing phát sinh khi tích hợp Frontend React với Backend API Gateway.
* Tối ưu C# Lambda Cold Start từ ~3.5s xuống ~800ms (ReadyToRun compilation); hoàn thành Module 5 & 6 Workshop.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Nghiệm thu chuỗi thực hành **Lab 4 đến Lab 9** (IAM Governance, EC2-RDS Multi-AZ, Auto Scaling, ALB, Budgets, CloudWatch, AWS Support). Áp dụng chiến lược Bypass lỗi ngoại vi bảo vệ tiến độ. Phối hợp tích hợp Frontend-Backend, debug lỗi CORS và JWT token parsing. | 15/06/2026 | 17/06/2026 | [AWS Auto Scaling User Guide](https://docs.aws.amazon.com/autoscaling/) |
| Thứ 5 - Thứ 6 | Thiết kế sơ đồ Reference Architecture trên draw.io & khởi động **Lab 10** (IaC với CloudFormation). Tối ưu C# Lambda Cold Start: bật `PublishReadyToRun=true` trong `.csproj`, chuyển sang `System.Text.Json` serializer. Đo lường Init Duration qua CloudWatch Logs. | 18/06/2026 | 19/06/2026 | [Lambda Cold Start Optimization](https://docs.aws.amazon.com/lambda/latest/dg/snapstart.html) |
| Thứ 7 - CN | Soạn thảo và hoàn thiện tài liệu Workshop: **Module 5** (DynamoDB Single-Table Design) và **Module 6** (C# Serverless Web API). | 20/06/2026 | 21/06/2026 | [AWS Workshop Studio](https://studio.us-east-1.prod.workshops.aws/) |

### Kết quả đạt được tuần 7:

* Hoàn thành nghiệm thu liên hoàn các bài Lab AWS từ Lab 4 đến Lab 9 và bắt đầu bài Lab 10 CloudFormation.
* Giải quyết triệt để lỗi CORS & JWT parsing: Frontend kết nối mượt mà với API Gateway 100%.
* Cold Start C# Lambda giảm từ ~3.5s xuống ~800ms (~70% improvement); xuất bản Module 5 & 6 Workshop.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Kiến thức hạ tầng HA (High Availability) từ bài Lab Auto Scaling & ALB giúp thấu hiểu cơ chế tự động mở rộng quy mô. Việc kết hợp bật `PublishReadyToRun=true` khi build C# Lambda pre-compiles IL sang native code, loại bỏ JIT overhead giúp giảm Init Duration từ 3.5s xuống <1s.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Cải thiện độ trễ Cold Start từ 3.5s xuống <1s trực tiếp nâng cao **Perceived Performance** cho người dùng cuối trên giao diện tài chính. Áp dụng chiến lược Bypass bài lab linh hoạt giúp bảo vệ tiến độ tổng thể mà không bị nghẽn bởi các sự cố hạ tầng ngoại vi.

### Kế hoạch tuần tiếp theo:
Đẩy nhanh tiến độ AWS Labs (đến Lab 14); tích hợp Google Gemini AI (auto-categorization & Financial Chatbot), thiết lập Edge Security (CloudFront/WAFv2) và khởi động dự án cá nhân Workshop.
