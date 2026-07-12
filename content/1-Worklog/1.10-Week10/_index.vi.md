---
title: "Nhật ký công việc Tuần 10"
date: 2026-05-04
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

* Kiểm thử toàn bộ hệ thống và đồng bộ hóa tài liệu (Proposal, Blog, Workshop).
* Nghiên cứu AWS Well-Architected Framework để tự đánh giá và cải thiện kiến trúc.
* Cập nhật và hoàn thiện Worklog cá nhân.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 – Thứ 3 | Thực hiện Final Review toàn bộ dự án: phát hiện sự không nhất quán nghiêm trọng giữa nội dung Proposal, Blog và Workshop — mỗi tài liệu mô tả kiến trúc theo góc nhìn khác nhau, vi phạm nguyên tắc **Single Source of Truth**. Tổ chức Sync-up Meeting với toàn nhóm để chốt lại kiến trúc chuẩn, thống nhất thuật ngữ và diagram. | 06/07/2026 | 07/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |
| Thứ 4 – Thứ 5 | Tái cấu trúc (Refactor) toàn bộ hệ thống tài liệu: cập nhật Proposal với kiến trúc đã được chốt, đồng bộ nội dung Blog và Workshop theo cùng một Architecture Diagram và Technology Stack. Áp dụng nguyên tắc Single Source of Truth: mọi thay đổi kiến trúc phải cập nhật tại một điểm duy nhất và propagate ra tất cả tài liệu. | 08/07/2026 | 09/07/2026 | [Documentation Best Practices](https://www.writethedocs.org/guide/docs-as-code/) |
| Thứ 6 | Hoàn thiện và đóng gói dự án cá nhân: kiểm tra deployment, verify luồng hoạt động trên Web, cập nhật Worklog cá nhân đến tuần 10. | 10/07/2026 | 10/07/2026 | — |
| Thứ 7 - CN | Nghiên cứu **AWS Well-Architected Framework**: phân tích dự án Budget Tracker theo 2 trụ cột — **Security Pillar** (IAM Least Privilege, S3 encryption, Cognito MFA) và **Cost Optimization Pillar** (Lambda memory right-sizing, DynamoDB on-demand vs provisioned, SQS vs polling). Lập danh sách cải tiến cho tuần 11-12. | 11/07/2026 | 12/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |

### Kết quả đạt được tuần 10:

* Hệ thống tài liệu (Proposal, Blog, Workshop) được đồng bộ hóa hoàn toàn với một kiến trúc chuẩn duy nhất.
* Dự án cá nhân hoàn thiện, deployment ổn định.
* Xác định được các điểm cải tiến theo AWS Well-Architected Framework để áp dụng trong tuần 11-12.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Đánh giá dự án theo AWS Well-Architected Security Pillar phát hiện một số điểm cần cải thiện: Lambda Execution Role chưa được scope theo từng function (tất cả dùng chung một role rộng), S3 Versioning chưa bật, CloudTrail chưa được enable để audit API calls. Cost Optimization Pillar chỉ ra Lambda memory allocation (256MB mặc định) có thể được right-size bằng Lambda Power Tuning tool — đây là hướng cải thiện cụ thể cho tuần 11.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Sự kiện phát hiện tài liệu không đồng bộ ở tuần cuối là một **near-miss** trong quản lý dự án: nếu không phát hiện kịp, sản phẩm bàn giao (báo cáo, slides) sẽ mâu thuẫn với demo thực tế, gây mất uy tín trước hội đồng đánh giá. Hành động Sync-up Meeting và Refactoring tài liệu ngay lập tức thể hiện tư duy **documentation as a first-class deliverable** — không chỉ code mới cần review, tài liệu cũng cần được maintain với cùng mức nghiêm ngặt.

### Kế hoạch tuần tiếp theo:
Triển khai Infrastructure as Code (IaC) với AWS SAM Template và thiết lập CI/CD Pipeline tự động bằng GitHub Actions.
