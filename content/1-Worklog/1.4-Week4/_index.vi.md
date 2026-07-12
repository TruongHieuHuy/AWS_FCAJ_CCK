---
title: "Nhật ký công việc Tuần 4"
date: 2026-05-04
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Provision hạ tầng mạng cơ sở (VPC, Subnet, Security Group, NAT Gateway).
* Thiết lập Amazon Cognito User Pool và tích hợp xác thực JWT vào C# Lambda.
* Phát triển các Lambda endpoint CRUD cơ bản với mock data để kiểm thử luồng API.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Provision hạ tầng mạng: tạo VPC với CIDR `/16`, phân tách Public Subnet (cho API Gateway/ALB) và Private Subnet (cho Lambda/Database), cấu hình Internet Gateway, Route Table và NAT Gateway. Thiết lập Security Group với nguyên tắc Least Privilege (chỉ mở port cần thiết). | 25/05/2026 | 27/05/2026 | [Amazon VPC User Guide](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| Thứ 5 - Thứ 6 | Thiết lập Amazon Cognito User Pool: cấu hình password policy, MFA optional, App Client (không có client secret cho SPA). Viết C# middleware xác thực JWT: parse và validate signature token sử dụng JWKS endpoint của Cognito; trích xuất `sub` (User ID) từ claims để phân quyền tài nguyên. | 28/05/2026 | 29/05/2026 | [Amazon Cognito Developer Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html) |
| Thứ 7 - CN | Phát triển các Lambda C# xử lý CRUD Transactions với mock data (in-memory): `POST /transactions`, `GET /transactions`, `PUT /transactions/{id}`, `DELETE /transactions/{id}`. Thống nhất JSON Schema (API Contract) với Frontend Engineer để hai nhóm phát triển song song. | 30/05/2026 | 31/05/2026 | [API Gateway REST API Reference](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api.html) |

### Kết quả đạt được tuần 4:

* Hạ tầng mạng VPC production-ready với network isolation giữa các tier.
* Amazon Cognito User Pool hoạt động; C# Lambda xác thực JWT token thành công.
* API Contract (JSON Schema) cho CRUD Transactions được hai nhóm thống nhất, mở đường cho phát triển song song.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Thiết kế VPC với Public/Private Subnet separation là nền tảng của **Defense in Depth**: Lambda function chạy trong Private Subnet không có public IP, mọi inbound traffic đều phải đi qua API Gateway. Khi cấu hình Security Group, áp dụng nguyên tắc Least Privilege: chỉ cho phép traffic nội bộ giữa các subnet, không mở port 22/3389 trừ khi thực sự cần. Việc xác thực JWT bằng JWKS endpoint của Cognito đảm bảo signature verification đúng chuẩn OAuth 2.0 — không cần lưu client secret phía server.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Quyết định thống nhất **API Contract trước khi viết code** là một trong những quyết định quan trọng nhất của tuần này. Bằng cách chốt JSON Schema cho từng endpoint, Frontend và Backend có thể phát triển song song mà không bị blocking lẫn nhau — điều này trực tiếp rút ngắn **Time-to-Integration** và giảm chi phí sửa lỗi tích hợp (integration bug thường tốn thời gian gấp 3-5 lần bug đơn thuần).

### Kế hoạch tuần tiếp theo:
Thiết kế DynamoDB Single-Table Schema và triển khai kết nối database thực tế từ C# Lambda.
