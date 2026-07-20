---
title: "Nhật ký công việc Tuần 4"
date: 2026-05-04
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Tham vấn Mentor khắc phục chuỗi lỗi phân quyền hệ thống (CloudShell, Bedrock, IAM User).
* Tham gia sinh hoạt AWS Student Builder Group; phân tích mã nguồn mở "Hera" & Voice Agents trên Bedrock AgentCore.
* Provision hạ tầng mạng VPC cơ bản, thiết lập Amazon Cognito User Pool và phát triển C# Lambda CRUD endpoints.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Tham vấn Mentor FCAJ để giải quyết chuỗi lỗi phân quyền IAM, CloudShell và Bedrock Model Access. Tham gia AWS Student Builder Group; nghiên cứu kiến trúc repo "Hera" và giải pháp Voice Agents trên Amazon Bedrock AgentCore. | 25/05/2026 | 27/05/2026 | [Amazon Bedrock AgentCore](https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html) |
| Thứ 5 - Thứ 6 | Triển khai hạ tầng mạng dự án: tạo VPC với CIDR `/16`, phân tách Public/Private Subnets, cấu hình Internet Gateway và Security Groups. Thiết lập Amazon Cognito User Pool & viết C# middleware xác thực JWT claims. | 28/05/2026 | 29/05/2026 | [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| Thứ 7 - CN | Phát triển các hàm Lambda C# xử lý CRUD Transactions (`POST`, `GET`, `PUT`, `DELETE`). Thống nhất JSON Schema (API Contract) với Frontend Engineer để hai nhóm phát triển song song. | 30/05/2026 | 31/05/2026 | [API Gateway REST API Reference](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html) |

### Kết quả đạt được tuần 4:

* Khắc phục hoàn toàn các lỗi phân quyền IAM/CloudShell nhờ sự hỗ trợ chuyên môn từ Mentor.
* Tiếp thu tư kiến trúc Voice Agent từ repo "Hera" phục vụ định hướng nâng cao.
* Hạ tầng VPC an toàn, Amazon Cognito Auth và bộ API CRUD C# Lambda được thiết lập thành công.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Thiết kế VPC với Public/Private Subnet separation là nền tảng của **Defense in Depth**: Lambda function chạy trong Private Subnet không có public IP, mọi inbound traffic đều phải đi qua API Gateway. Việc tham vấn Mentor điều chỉnh IAM Trust Policy cho Bedrock AgentCore giúp nắm rõ cách phân quyền cho các dịch vụ AI Agent trên AWS.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Quyết định thống nhất **API Contract (JSON Schema) trước khi viết code** giúp Frontend và Backend phát triển song song mà không bị blocking lẫn nhau. Việc chủ động tham gia hoạt động cộng đồng (Student Builder Group) mở ra những góc nhìn công nghệ mới về Voice Agents cho lộ trình phát triển ứng dụng.

### Kế hoạch tuần tiếp theo:
Nghiệm thu Lab 2 & thực hành Lab 3 (VPC/EC2 Troubleshooting); thiết kế DynamoDB Single-Table Schema và S3 Presigned URL cho dự án.
