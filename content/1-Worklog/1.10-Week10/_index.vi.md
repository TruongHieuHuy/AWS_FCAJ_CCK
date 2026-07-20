---
title: "Nhật ký công việc Tuần 10"
date: 2026-05-04
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

* Hoàn tất và nghiệm thu 100% Dự án nhóm và Dự án cá nhân.
* Phát hiện và đồng bộ hóa toàn bộ hệ thống tài liệu (Proposal, Blog, Workshop) theo tiêu chuẩn Single Source of Truth.
* Nghiên cứu AWS Well-Architected Framework và cập nhật Worklog tuần 10.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 – Thứ 3 | Final Review toàn bộ dự án: phát hiện điểm bất đồng bộ nghiêm trọng giữa Proposal, Blog và Workshop do viết theo góc nhìn cá nhân sai lệch. Tổ chức cuộc họp Sync-up meeting với toàn nhóm để đối chiếu scope và chốt kiến trúc chuẩn. | 06/07/2026 | 07/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |
| Thứ 4 – Thứ 5 | Thực hiện Refactoring đập đi xây lại hệ thống tài liệu: cập nhật Proposal, Blog và kịch bản Workshop khớp nối 100% với kiến trúc nhóm đã chốt theo nguyên tắc **Single Source of Truth**. | 08/07/2026 | 09/07/2026 | [Documentation Best Practices](https://www.writethedocs.org/guide/docs-as-code/) |
| Thứ 6 | Hoàn thiện và đóng gói dự án cá nhân: kiểm tra luồng chạy thực tế trên Web, tổng hợp và cập nhật Worklog cá nhân tuần 10. | 10/07/2026 | 10/07/2026 | — |
| Thứ 7 - CN | Đọc và nghiên cứu tài liệu **AWS Well-Architected Framework**: phân tích sản phẩm theo 2 trụ cột chính — Security Pillar (IAM, S3, Cognito) và Cost Optimization Pillar (Lambda right-sizing, DynamoDB capacity). Lập kế hoạch IaC/CICD cho tuần 11. | 11/07/2026 | 12/07/2026 | [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html) |

### Kết quả đạt được tuần 10:

* 100% Dự án nhóm và Dự án cá nhân hoàn tất nghiệm thu đúng thời hạn.
* Khắc phục triệt để sự cố bất đồng bộ tài liệu, chuẩn hóa Proposal, Blog và Workshop.
* Nghiên cứu thành công bộ tiêu chuẩn AWS Well-Architected Framework và hoạch định cải tiến.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Đánh giá dự án theo AWS Well-Architected Security & Cost Optimization Pillars chỉ ra các cơ hội cải thiện cụ thể: right-sizing bộ nhớ Lambda bằng Lambda Power Tuning, chuẩn hóa IAM Role scope theo từng function.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Việc phát hiện tài liệu lệch và kiên quyết refactor đập đi xây lại thể hiện tư duy **Documentation Management** chuyên nghiệp. Đảm bảo nguyên tắc Single Source of Truth giúp thông điệp dự án đồng nhất khi trình bày trước hội đồng.

### Kế hoạch tuần tiếp theo:
Triển khai Infrastructure as Code (IaC) với AWS SAM Template và xây dựng CI/CD Pipeline tự động qua GitHub Actions (OIDC auth).
