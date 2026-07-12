---
title: "Nhật ký công việc Tuần 1"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Nghiên cứu tài liệu định hướng chương trình FCAJ và lộ trình AWS Cloud Journey.
* Khởi tạo tài khoản AWS và thiết lập môi trường thực hành Lab.
* Phân tích nguyên nhân gốc rễ (Root Cause Analysis) sự cố tài khoản bị khóa.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Nghiên cứu tài liệu định hướng FCAJ; lập bản đồ lộ trình học tập AWS Cloud Journey theo từng giai đoạn (Foundation → Serverless → Production). | 04/05/2026 | 06/05/2026 | [AWS Cloud Journey Roadmap](https://cloudjourney.awsstudygroup.com/) |
| Thứ 5 - Thứ 6 | Tiếp thu lý thuyết nền tảng về mô hình IaaS/PaaS/SaaS và Shared Responsibility Model. Khởi tạo tài khoản AWS với cấu hình bảo mật chuẩn: bật MFA cho root account, thiết lập IAM Admin User, cấu hình AWS CLI với access key. | 07/05/2026 | 08/05/2026 | [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Thứ 7 - CN | Phát hiện tài khoản bị khóa sau khi khởi tạo. Thực hiện Root Cause Analysis: kiểm tra email thông báo từ AWS, rà soát cấu hình billing và IAM policy. Chuẩn bị hồ sơ xác minh để gửi AWS Support Case. | 09/05/2026 | 10/05/2026 | [AWS Support Case Guide](https://docs.aws.amazon.com/awssupport/latest/user/case-management.html) |

### Kết quả đạt được tuần 1:

* Nắm vững lộ trình học tập và quy trình vận hành của chương trình FCAJ.
* Hiểu rõ Shared Responsibility Model và phân biệt trách nhiệm bảo mật giữa AWS và người dùng.
* Xác định nguyên nhân sự cố khóa tài khoản và chuẩn bị đầy đủ tài liệu xác minh để gửi Support Case.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Sự cố tài khoản bị khóa ngay sau khi khởi tạo cho thấy AWS có cơ chế fraud detection tự động phát hiện các hành vi bất thường (địa chỉ IP mới, thiếu billing info). Quá trình RCA yêu cầu phân tích IAM Trust Policy, kiểm tra CloudTrail log (nếu đã được bật) và xác minh thông tin định danh. Bài học quan trọng: luôn bật MFA cho root account và tạo IAM Admin User với quyền tối thiểu (IAM Least Privilege) ngay từ bước khởi tạo để tránh lockout.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Từ góc độ quản lý rủi ro dự án: sự cố tài khoản ở ngay tuần đầu tiên tạo ra một blocker nghiêm trọng cho toàn bộ lộ trình 12 tuần. Quyết định lập Support Case ngay thay vì chờ đợi thụ động thể hiện tư duy chủ động (proactive risk mitigation). Đây cũng là bài học về việc cần lập kế hoạch dự phòng (contingency plan) cho môi trường phát triển trước khi bắt đầu bất kỳ dự án Cloud nào.

### Kế hoạch tuần tiếp theo:
Giải quyết dứt điểm sự cố tài khoản; hoàn thành 5 nhiệm vụ Onboarding để kích hoạt Cloud Credits và bắt đầu thực hành Lab.
