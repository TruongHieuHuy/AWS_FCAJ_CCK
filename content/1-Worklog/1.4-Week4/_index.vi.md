---
title: "Nhật ký công việc Tuần 4"
date: 2026-05-04
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Tham vấn Mentor khắc phục chuỗi lỗi phân quyền hệ thống (CloudShell, Bedrock, IAM User).
* Tham gia sinh hoạt AWS Student Builder Group, phân tích mã nguồn mở "Hera" & Voice Agents trên Bedrock AgentCore.
* Khởi tạo VPC Subnets, Cognito User Pool Auth và xây dựng các API CRUD Transactions C# Lambda.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Tham vấn Mentor FCAJ để giải quyết chuỗi lỗi phân quyền IAM, CloudShell và Bedrock Model Access. Tham gia AWS Student Builder Group, nghiên cứu kiến trúc repo "Hera" và giải pháp Voice Agents trên Amazon Bedrock AgentCore. | 25/05/2026 | 27/05/2026 | [Amazon Bedrock AgentCore](https://docs.aws.amazon.com/bedrock/latest/userguide/agents.html) |
| Thứ 5 - Thứ 6 | Khởi tạo hạ tầng mạng VPC cơ bản (Public/Private Subnets), Amazon Cognito User Pool Auth và cấu hình App Client secret cho dự án. | 28/05/2026 | 29/05/2026 | [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html) |
| Thứ 7 - CN | Phát triển bộ API C# Lambda CRUD cho đối tượng Transactions (`CreateTransaction`, `GetTransactions`, `UpdateTransaction`), tích hợp Cognito JWT validation middleware. | 30/05/2026 | 31/05/2026 | [AWS SDK for .NET](https://docs.aws.amazon.com/sdk-for-net/v3/developer-guide/welcome.html) |

### Kết quả đạt được tuần 4:

* Khắc phục hoàn toàn lỗi phân quyền IAM/CloudShell/Bedrock nhờ tham vấn chuyên gia Mentor.
* Tiếp thu kiến thức thiết kế Voice Agents tiên tiến từ repo "Hera" của AWS Student Builder Group.
* Hạ tầng mạng VPC isolation và Cognito User Pool Auth sẵn sàng bảo mật cho ứng dụng.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Phân tách Public/Private Subnet ngay từ đầu là nguyên tắc bảo mật tối quan trọng (**Least Privilege & Defense in Depth**). Việc tích hợp Cognito JWT claims giúp Lambda backend xác thực người dùng dựa trên `sub` ID một cách tự động, loại bỏ nguy cơ giả mạo Identity.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Nghiên cứu dự án "Hera" giúp mở rộng tầm nhìn về tích hợp Voice Agents trên đám mây. Việc chốt API Contract (Request/Response DTOs) tuần này tạo điều kiện để Frontend và Backend phát triển song song mà không bị nghẽn phụ thuộc (blocking dependencies).

### Kế hoạch tuần tiếp theo:
Nghiệm thu Lab 2 & thực hành Lab 3 (VPC/EC2 Troubleshooting), thiết kế DynamoDB Single-Table Schema và S3 Presigned URL cho dự án.
