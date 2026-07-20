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
* Tối ưu C# Lambda Cold Start từ ~3.5s xuống ~800ms (ReadyToRun compilation), hoàn thành Module 5 & 6 Workshop.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 3 | Nghiệm thu chuỗi thực hành từ Lab 4 đến Lab 9 (IAM Governance, EC2-RDS Multi-AZ, Auto Scaling, ALB, CloudWatch). Áp dụng chiến lược Bypass lỗi ngoại vi bảo vệ tiến độ; khởi động Lab 10 (IaC với CloudFormation). | 15/06/2026 | 16/06/2026 | [AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/) |
| Thứ 4 - Thứ 5 | Tích hợp Frontend-Backend: gỡ lỗi CORS (cấu hình cả API Gateway lẫn Lambda response headers), debug JWT Authorization header format (`Bearer <token>`). | 17/06/2026 | 18/06/2026 | [API Gateway CORS Troubleshooting](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html) |
| Thứ 6 - CN | Tối ưu C# Lambda Cold Start: kích hoạt `PublishReadyToRun=true` trong MSBuild, thay thế `Newtonsoft.Json` bằng `System.Text.Json`, cấu hình Lambda Memory 1024MB. Biên soạn Module 5 & 6 Workshop. | 19/06/2026 | 21/06/2026 | [Optimizing .NET Lambda Performance](https://aws.amazon.com/blogs/compute/optimizing-net-lambda-performance/) |

### Kết quả đạt được tuần 7:

* Nghiệm thu thành công chuỗi Lab 4-9 và khởi động bài thực hành Lab 10 CloudFormation.
* Lỗi CORS và JWT Token parsing được khắc phục triệt để, ứng dụng chạy mượt từ UI đến DB.
* Cold Start C# Lambda giảm từ ~3.5s xuống ~800ms (~70% improvement), xuất bản Module 5 & 6 Workshop.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Giảm Cold Start latency cho .NET Lambda từ 3.5s xuống <1s bằng `PublishReadyToRun` (AOT compilation) và `System.Text.Json` (giảm reflection overhead) là minh chứng cho việc **tối ưu hóa ở mức runtime**. Việc cấu hình CORS ở cả 2 tầng (API Gateway Mappings và Lambda Response Headers) giải quyết triệt để vấn đề Preflight OPTIONS request.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Nghiệm thu chuỗi AWS Labs 4-9 củng cố kiến thức High Availability (Multi-AZ RDS, ALB, Auto Scaling). Chiến lược "Bypass lỗi ngoại vi bảo vệ tiến độ" giúp toàn nhóm không bị chôn chân tại các sự cố môi trường không thuộc phạm vi cốt lõi, giữ vững tiến độ giao hàng (delivery schedule).

### Kế hoạch tuần tiếp theo:
Đẩy nhanh tiến độ AWS Labs (đến Lab 14), tích hợp Google Gemini AI (auto-categorization & Financial Chatbot), thiết lập Edge Security (CloudFront/WAFv2) và khởi động dự án cá nhân Workshop.
