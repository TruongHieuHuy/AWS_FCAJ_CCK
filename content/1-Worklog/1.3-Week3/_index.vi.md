---
title: "Nhật ký công việc Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Nghiên cứu quản lý tài nguyên và thiết lập Khung tối ưu hóa chi phí (AWS Budgets, CloudWatch).
* Tham dự hội thảo AWS Community Day 2026 và hoàn thành báo cáo thu hoạch chuyên sâu về GenAI.
* Thiết kế kiến trúc Serverless Stack cho dự án Budget Tracker, scaffold repo Git Backend C# và viết Project Proposal.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Nghiên cứu tài nguyên & quản lý chi phí (AWS Budgets, CloudWatch Metrics/Alarms), xử lý môi trường CloudShell. Tổ chức họp nhóm thiết kế kiến trúc Serverless Stack (API Gateway + C# Lambda + DynamoDB). | 18/05/2026 | 20/05/2026 | [AWS Serverless Architecture Patterns](https://aws.amazon.com/architecture/serverless/) |
| Thứ 5 - Thứ 6 | Tham dự hội thảo AWS Community Day 2026, hoàn thành báo cáo chuyên sâu GenAI & Multi-Agent Systems. Khởi tạo Git monorepo Backend C# .NET 8 Web API với dependency injection và `.gitignore` chuẩn. | 21/05/2026 | 22/05/2026 | [.NET on AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html) |
| Thứ 7 - CN | Soạn thảo Project Proposal: kiến trúc hệ thống (Architecture Diagram), ước tính chi phí vận hành sử dụng AWS Pricing Calculator (Lambda invocations, DynamoDB RCU/WCU, API Gateway, Gemini API), phân công công việc WBS. | 23/05/2026 | 24/05/2026 | [AWS Pricing Calculator](https://calculator.aws/pricing/2/home) |

### Kết quả đạt được tuần 3:

* Nắm vững cách quản trị chi phí AWS Budgets & CloudWatch phòng tránh phát sinh chi phí ngoài ý muốn.
* Báo cáo thu hoạch AWS Community Day 2026 hoàn thành với kiến thức mới về GenAI & Multi-Agent Systems.
* Proposal dự án Budget Tracker và sơ đồ kiến trúc Serverless Stack được chốt thông qua.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Lựa chọn kiến trúc Serverless (API Gateway + Lambda + DynamoDB) không chỉ là quyết định kỹ thuật mà còn là quyết định kinh doanh: mô hình **Pay-per-use** của Lambda loại bỏ hoàn toàn chi phí server idle. Khi scaffold C# project, việc kết hợp kiểm soát chi phí ngay từ đầu với AWS Budgets giúp đảm bảo hệ thống thử nghiệm không bao giờ vượt hạn mức credits được cấp.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Bản Proposal không chỉ là tài liệu kỹ thuật — nó là **contract** giữa các thành viên nhóm. Việc ước tính chi phí sử dụng AWS Pricing Calculator với các kịch bản thực tế giúp nhóm hiểu rõ ngưỡng chi phí. Kết hợp kiến thức tiếp thu từ AWS Community Day 2026 giúp nhóm bổ sung góc nhìn AI tiên tiến vào roadmap sản phẩm.

### Kế hoạch tuần tiếp theo:
Tham vấn Mentor gỡ lỗi IAM/CloudShell, nghiên cứu repo "Hera" & Bedrock AgentCore, triển khai hạ tầng mạng VPC và Cognito Auth cho dự án.
