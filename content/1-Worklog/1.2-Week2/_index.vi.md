---
title: "Nhật ký công việc Tuần 2"
date: 2026-05-04
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Giải quyết dứt điểm sự cố tài khoản AWS bị khóa phân quyền thông qua Mitigation Strategy.
* Hoàn thành toàn bộ 5 nhiệm vụ Onboarding để nhận $100 AWS Cloud Credits của chương trình FCAJ.
* Thống nhất phân công nhiệm vụ và luồng làm việc nhóm cho dự án Serverless Budget Tracker.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 3 | Soạn thảo báo cáo kỹ thuật song ngữ và gửi AWS Support Case yêu cầu tra soát lỗi phân quyền tài khoản. Liên hệ các Mentor FCAJ để điều tra nguyên nhân. | 11/05/2026 | 12/05/2026 | [AWS Support Center](https://support.console.aws.amazon.com/) |
| Thứ 4 - Thứ 5 | Tiếp nhận phản hồi từ AWS. Triển khai Mitigation Strategy: khởi tạo tài khoản AWS mới để xóa bỏ blocker tiến độ. Họp nhóm chốt phân công vai trò phụ trách dự án Budget Tracker. | 13/05/2026 | 14/05/2026 | [AWS Account Management](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html) |
| Thứ 6 - Thứ 7 | Triển khai chuỗi Onboarding: **Nhiệm vụ 1** — EC2 provisioning & termination; **Nhiệm vụ 3** — AWS Budgets alert; **Nhiệm vụ 4** — AWS Lambda hello-world; **Nhiệm vụ 5** — Amazon RDS Aurora. Gửi Support Case yêu cầu cấp Model Access cho Anthropic Claude 3 Haiku (Nhiệm vụ 2). | 15/05/2026 | 16/05/2026 | [AWS Lambda Developer Guide](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| Chủ nhật | Nhận phê duyệt Model Access từ AWS. Hoàn thành **Nhiệm vụ 2**: thực nghiệm Amazon Bedrock prompt & inference model Claude 3 Haiku. Nhận 100$ AWS Cloud Credits. | 17/05/2026 | 17/05/2026 | [Amazon Bedrock User Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |

### Kết quả đạt được tuần 2:

* Giải quyết triệt để blocker môi trường bằng chiến lược tạo tài khoản AWS dự phòng.
* Hoàn tất 5/5 nhiệm vụ Onboarding và kích hoạt thành công 100$ Cloud Credits FCAJ.
* Thống nhất phân công công việc và luồng làm việc nhóm cho dự án Budget Tracker.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Sự cố IAM Trust Relationship khiến tài khoản bị khóa là một kịch bản thực chiến quan trọng: AWS áp dụng cơ chế bảo vệ tự động khi phát hiện anomaly trong quá trình đăng ký. Khi xử lý Onboarding, việc Lambda Nhiệm vụ 4 yêu cầu cấu hình IAM Execution Role với quyền `AWSLambdaBasicExecutionRole` làm rõ nguyên lý Least Privilege. Đặc biệt, Amazon Bedrock yêu cầu Model Access phải được cấp thủ công — đây là cơ chế governance kiểm soát AI usage.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Việc chủ động triển khai Mitigation Strategy (tạo tài khoản mới) thay vì chờ Support Case giải quyết thể hiện tư duy **time-to-value optimization** — ưu tiên duy trì tiến độ dự án hơn là chờ giải pháp lý tưởng. Phối hợp phân công nhiệm vụ rõ ràng trong nhóm tạo đà tăng tốc cho việc thiết kế kiến trúc hệ thống ở tuần tiếp theo.

### Kế hoạch tuần tiếp theo:
Quản lý tài nguyên & tối ưu chi phí AWS Budgets/CloudWatch; tham dự AWS Community Day 2026; thiết kế kiến trúc Serverless và viết Proposal dự án.
