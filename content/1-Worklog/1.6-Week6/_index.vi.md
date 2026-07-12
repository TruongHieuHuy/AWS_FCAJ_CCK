---
title: "Nhật ký công việc Tuần 6"
date: 2026-05-04
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Cấu hình API Gateway REST API với Cognito JWT Authorizer và Payload Mapping Template.
* Triển khai business logic hoàn chỉnh cho ba Lambda functions cốt lõi.
* Soạn thảo tài liệu đặc tả API (OpenAPI/Swagger) bàn giao cho Frontend.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Cấu hình API Gateway REST API: tạo Resources và Methods cho từng endpoint, gắn Cognito JWT Authorizer để reject unauthenticated requests ngay tại Gateway (không tốn Lambda invocation). Thiết lập **Payload Mapping Template** để trích xuất `sub` từ JWT claims và inject vào request body gửi xuống Lambda. | 08/06/2026 | 10/06/2026 | [API Gateway Authorizers](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-use-lambda-authorizer.html) |
| Thứ 5 - Thứ 6 | Triển khai business logic C# cho ba Lambda functions: **TransactionFunction** (CRUD giao dịch vào DynamoDB, validate budget threshold khi thêm mới); **BudgetFunction** (tính toán và cập nhật remaining budget theo category); **ReportFunction** (tổng hợp spending statistics theo tháng bằng `QueryAsync` với GSI). | 11/06/2026 | 12/06/2026 | [AWS Lambda Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html) |
| Thứ 7 - CN | Kiểm thử tích hợp end-to-end: test toàn bộ luồng Authentication → API Gateway → Lambda → DynamoDB với Postman. Soạn thảo tài liệu đặc tả OpenAPI (Swagger YAML) mô tả đầy đủ request/response schema, error codes và authentication header cho Frontend Engineer. | 13/06/2026 | 14/06/2026 | [OpenAPI Specification](https://swagger.io/specification/) |

### Kết quả đạt được tuần 6:

* API Gateway với Cognito Authorizer hoạt động: unauthorized requests bị chặn tại Gateway, không tiêu tốn Lambda compute.
* Ba Lambda functions cốt lõi (Transaction, Budget, Report) triển khai hoàn chỉnh và kiểm thử thành công.
* Tài liệu OpenAPI/Swagger bàn giao Frontend, unblock quá trình tích hợp song song.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Việc đặt Cognito Authorizer tại API Gateway thay vì xác thực trong Lambda code là một quyết định kiến trúc quan trọng: **reject unauthenticated requests tại biên** giúp tiết kiệm Lambda invocation (mỗi invocation có chi phí + Cold Start). Payload Mapping Template sử dụng Velocity Template Language (VTL) để trích xuất `context.authorizer.claims.sub` và inject vào body — đảm bảo Lambda không bao giờ phải parse JWT token trực tiếp, tuân thủ nguyên tắc Separation of Concerns. ReportFunction sử dụng GSI (Global Secondary Index) thay vì Scan để tổng hợp spending theo tháng với cost predictable.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Tài liệu OpenAPI/Swagger không chỉ là mô tả kỹ thuật — nó là **nguồn giao tiếp duy nhất** (Single Source of Truth) giữa Backend và Frontend trong suốt quá trình tích hợp. Định nghĩa rõ ràng HTTP status codes (200/400/401/403/500), error response schema và authentication header requirements giúp Frontend Engineer tự chủ xử lý error states mà không cần liên tục hỏi Backend — giảm overhead giao tiếp và tăng tốc độ phát triển song song.

### Kế hoạch tuần tiếp theo:
Phối hợp tích hợp Frontend-Backend: debug CORS policy, giải quyết JWT parsing issues và tối ưu Lambda Cold Start bằng ReadyToRun compilation.
