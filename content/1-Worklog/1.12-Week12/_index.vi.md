---
title: "Nhật ký công việc Tuần 12"
date: 2026-05-04
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12:

* Thực hiện User Acceptance Testing (UAT) toàn diện và kiểm toán chi phí AWS Billing.
* Thực hiện Resource Cleanup giải phóng 100% tài nguyên billable trên AWS Cloud theo Module 12 Workshop.
* Biên soạn Báo cáo thực tập tổng kết.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 3 | Thực hiện **User Acceptance Testing (UAT)**: kiểm thử toàn bộ luồng người dùng — Cognito Auth, nhập giao dịch AI auto-categorization, budget alerts qua email, monthly report. Kiểm toán **AWS Cost Explorer** và Billing Dashboard xác định các tài nguyên tốn chi phí. | 20/07/2026 | 21/07/2026 | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| Thứ 4 | Thực hiện **Resource Cleanup** theo Module 12: xóa CloudFormation Stack (tự động xóa tài nguyên SAM), xóa rỗng S3 Buckets, revoke Cognito App Client, disable CloudFront Distribution trước khi delete. Xác nhận 0% billable resources tồn tại. | 22/07/2026 | 22/07/2026 | [AWS Resource Cleanup Guide](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) |
| Thứ 5 - Thứ 6 | Biên soạn **Báo cáo thực tập tổng kết**: tổng hợp 12 tuần thực tập (Setup → AWS Labs 1-16 → Architecture → Backend → AI/Security → Automation → Handover), định lượng kết quả. | 23/07/2026 | 25/07/2026 | — |

### Kết quả đạt được tuần 12:

* UAT hoàn thành — toàn bộ user flows hoạt động đúng spec, không có critical bug.
* Resource Cleanup hoàn tất — zero billable resources tồn tại sau khi kết thúc thực tập.
* Báo cáo thực tập tổng kết hoàn tất.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Resource Cleanup là kỹ năng quan trọng: xóa CloudFormation Stack đúng thứ tự (Consumer trước, Provider sau). Xóa rỗng S3 bucket và disable CloudFront trước khi delete stack tránh lỗi dependency lockout. AWS Cost Explorer giúp phát hiện cost anomalies hiệu quả.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Báo cáo thực tập tổng kết là **portfolio chuyên nghiệp đầu tiên** của kỹ sư. Định lượng kết quả cụ thể (Cold Start giảm 70%, 100% 16 AWS Labs completed, CI/CD automated) thể hiện năng lực thực chiến. Buổi bảo vệ trước hội đồng là cơ hội thực hành **Technical Storytelling** truyền tải giá trị giải pháp.

### Kế hoạch tuần tiếp theo:
Hoàn thành xuất sắc chương trình thực tập FCAJ. Tiếp tục ôn luyện AWS Certified Solutions Architect Associate (SAA-C03) và đóng góp open-source cho cộng đồng.
