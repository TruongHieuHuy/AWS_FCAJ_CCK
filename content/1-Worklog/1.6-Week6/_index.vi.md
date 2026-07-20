---
title: "Nhật ký công việc Tuần 6"
date: 2026-05-04
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Nghiệm thu Lab 3 (VPC Security/NAT/VPN) và triển khai >50% Lab 4 (Windows Server 2025/Linux, AMI, EBS Snapshot).
* Cấu hình API Gateway REST API với Cognito JWT Authorizer và Payload Mapping Template (VTL).
* Triển khai business logic cho 3 Lambda functions cốt lõi (`TransactionFunction`, `BudgetFunction`, `ReportFunction`) và xuất bản tài liệu OpenAPI.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Khắc phục sự cố luồng mạng và nghiệm thu bài **Lab 3** (VPC Firewall, NAT Gateway, Site-to-Site VPN). Khởi động và triển khai >50% bài **Lab 4**: khởi tạo VPC độc lập, chạy EC2 Windows Server 2025 và Amazon Linux. | 08/06/2026 | 10/06/2026 | [Amazon EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) |
| Thứ 5 - Thứ 6 | Thực hành quản trị vòng đời EC2 trong Lab 4 (EBS Snapshot, Custom AMI). Cấu hình API Gateway REST API cho dự án nhóm: tạo Resources `/transactions`, `/budgets`, `/reports` và Methods. Gắn Cognito JWT Authorizer. | 11/06/2026 | 12/06/2026 | [API Gateway Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html) |
| Thứ 7 - CN | Triển khai C# business logic cho ba Lambda cốt lõi: `TransactionFunction`, `BudgetFunction`, `ReportFunction`. Sử dụng VTL Payload Mapping Template inject `sub` User ID từ JWT. Soạn thảo tài liệu đặc tả OpenAPI/Swagger bàn giao Frontend. | 13/06/2026 | 14/06/2026 | [AWS Lambda Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html) |

### Kết quả đạt được tuần 6:

* Nghiệm thu bài Lab 3 thành công và hoàn thành hơn 50% tiến độ bài Lab 4.
* API Gateway REST API với Cognito Authorizer hoạt động: chặn request không hợp lệ ngay tại biên.
* Ba hàm C# Lambda cốt lõi triển khai hoàn chỉnh; bàn giao OpenAPI specification cho Frontend.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Đặt Cognito Authorizer tại API Gateway thay vì xác thực trong Lambda code giúp **reject unauthenticated requests tại biên** — tiết kiệm chi phí Lambda invocation. Việc kết hợp kiến thức quản trị EC2 AMI & EBS Snapshots từ Lab 4 giúp nâng cao tư duy bảo toàn dữ liệu và tạo bản sao dự phòng cho hạ tầng máy chủ.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Tài liệu OpenAPI/Swagger đóng vai trò là **Single Source of Truth** giữa Backend và Frontend trong suốt quá trình phát triển. Việc chốt rõ HTTP status codes và payload schema giúp nhóm phát triển Frontend làm việc độc lập, tự chủ xử lý error states mà không bị gián đoạn.

### Kế hoạch tuần tiếp theo:
Nghiệm thu chuỗi Lab 4 đến Lab 9; khởi động Lab 10 CloudFormation; tích hợp Frontend-Backend, sửa lỗi CORS/JWT và tối ưu C# Lambda Cold Start.
