---
title: "Nhật ký công việc Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Thiết kế và chốt kiến trúc hệ thống Serverless cho dự án Budget Tracker.
* Khởi tạo repository Git và cấu hình cấu trúc dự án Backend C# .NET 8.
* Soạn thảo Project Proposal hoàn chỉnh bao gồm kiến trúc, chi phí và phân công nhóm.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Tổ chức và chủ trì buổi họp nhóm thiết kế kiến trúc hệ thống: chốt công nghệ Serverless Stack (API Gateway + Lambda + DynamoDB), phác thảo data flow diagram và wireframe giao diện người dùng. | 18/05/2026 | 20/05/2026 | [AWS Serverless Architecture Patterns](https://aws.amazon.com/architecture/serverless/) |
| Thứ 5 - Thứ 6 | Khởi tạo Git repository với cấu trúc monorepo (backend/frontend/infra). Scaffold dự án C# .NET 8 Web API với dependency injection, cấu hình `appsettings.json` và thiết lập `.gitignore` chuẩn cho môi trường Lambda. Thiết lập branch strategy (main/develop/feature). | 21/05/2026 | 22/05/2026 | [.NET on AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html) |
| Thứ 7 - CN | Soạn thảo Project Proposal: kiến trúc hệ thống (Architecture Diagram), ước tính chi phí vận hành sử dụng AWS Pricing Calculator (Lambda invocations, DynamoDB RCU/WCU, API Gateway calls, Gemini API tokens), bảng Work Breakdown Structure (WBS) phân công chi tiết theo role. | 23/05/2026 | 24/05/2026 | [AWS Pricing Calculator](https://calculator.aws/pricing/2/home) |

### Kết quả đạt được tuần 3:

* Chốt kiến trúc Serverless Stack được toàn nhóm phê duyệt: API Gateway → Lambda (C#) → DynamoDB → S3.
* Thiết lập repository và cấu trúc thư mục chuẩn, sẵn sàng cho phát triển song song (Frontend/Backend).
* Hoàn thành Project Proposal với ước tính chi phí vận hành và WBS phân công rõ ràng theo role.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Lựa chọn kiến trúc Serverless (API Gateway + Lambda + DynamoDB) không chỉ là quyết định kỹ thuật mà còn là quyết định kinh doanh: mô hình **Pay-per-use** của Lambda loại bỏ hoàn toàn chi phí server idle khi không có traffic — phù hợp với ứng dụng cá nhân có lưu lượng không đều. Khi scaffold C# project, cần cấu hình `PublishReadyToRun=true` trong `.csproj` ngay từ đầu để tối ưu Cold Start latency cho Lambda runtime.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Bản Proposal không chỉ là tài liệu kỹ thuật — nó là **contract** giữa các thành viên nhóm. Việc ước tính chi phí sử dụng AWS Pricing Calculator với các kịch bản thực tế (100 users/day, 10 transactions/user) giúp nhóm hiểu rõ ngưỡng chi phí và đưa ra quyết định thiết kế đúng đắn. WBS phân công theo role (Backend Engineer, Frontend Engineer, Database Engineer) đảm bảo không có sự chồng chéo trách nhiệm và tạo nền tảng để track tiến độ khách quan.

### Kế hoạch tuần tiếp theo:
Provision hạ tầng mạng (VPC, Subnet, Security Group) và thiết lập Amazon Cognito User Pool cho luồng xác thực người dùng.
