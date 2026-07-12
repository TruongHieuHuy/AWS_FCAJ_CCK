---
title: "Nhật ký công việc Tuần 12"
date: 2026-05-04
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12:

* Thực hiện User Acceptance Testing (UAT) toàn diện và kiểm toán chi phí AWS Billing.
* Dọn dẹp tài nguyên (Resource Cleanup) theo Module 12 Workshop.
* Biên soạn báo cáo thực tập tổng kết và Slide thuyết trình trước hội đồng đánh giá.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 3 | Thực hiện **User Acceptance Testing (UAT)**: kiểm thử toàn bộ luồng người dùng thực tế — đăng ký/đăng nhập Cognito, nhập giao dịch với AI auto-categorization, kiểm tra budget alert qua email, xem monthly report. Kiểm toán **AWS Cost Explorer** và Billing Dashboard: xác định các tài nguyên tiêu tốn chi phí không cần thiết (NAT Gateway idle, CloudWatch Log Group retention unlimited). | 20/07/2026 | 21/07/2026 | [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| Thứ 4 | Thực hiện **Resource Cleanup** theo Module 12: xóa CloudFormation Stack (tự động xóa tất cả tài nguyên được tạo bởi SAM), xóa S3 Bucket contents trước khi xóa bucket, revoke Cognito App Client, disable CloudFront Distribution trước khi xóa. Xác nhận không còn tài nguyên billable tồn tại sau cleanup. | 22/07/2026 | 22/07/2026 | [AWS Resource Cleanup Guide](https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html) |
| Thứ 5 - Thứ 6 | Biên soạn **Báo cáo thực tập tổng kết**: tóm tắt 12 tuần theo lộ trình tăng tiến (Setup → Architecture → Backend → AI/Security → Automation → Handover), định lượng kết quả đạt được (số Lambda function, độ phủ test, Cold Start improvement, cost reduction). Thiết kế **Slide thuyết trình** với kiến trúc diagram, demo screenshots và bài học kinh nghiệm thực chiến. | 23/07/2026 | 25/07/2026 | — |

### Kết quả đạt được tuần 12:

* UAT hoàn thành — toàn bộ user flows hoạt động đúng spec, không có critical bug.
* Resource Cleanup hoàn tất — zero billable resources còn tồn tại sau khi kết thúc thực tập.
* Báo cáo thực tập và Slide thuyết trình sẵn sàng cho buổi bảo vệ.
* Tài liệu Workshop 12 Module xuất bản đầy đủ, sẵn sàng dùng làm tài liệu tham khảo.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Resource Cleanup là một kỹ năng quan trọng thường bị bỏ qua: việc xóa CloudFormation Stack đúng thứ tự (Consumer trước, Provider sau) tránh dependency errors. Một số tài nguyên cần xóa thủ công trước khi xóa Stack: S3 Bucket phải empty trước, CloudFront Distribution phải disabled trước khi delete. AWS Cost Explorer trong quá trình UAT giúp xác định **cost anomaly**: NAT Gateway tính phí ~$0.045/giờ kể cả khi không có traffic — trong environment dev/test, nên dùng VPC Endpoint thay thế để tiết kiệm chi phí.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Báo cáo thực tập không chỉ là tài liệu học thuật — nó là **portfolio chuyên nghiệp đầu tiên** của kỹ sư. Việc định lượng kết quả cụ thể (ví dụ: "Cold Start giảm 70% từ 3.5s xuống 800ms", "Lambda cost tối ưu với mô hình Pay-per-use thay vì EC2 luôn chạy") quan trọng hơn mô tả chung chung. Buổi bảo vệ trước hội đồng là cơ hội thực hành **Technical Storytelling**: chuyển hóa các quyết định kỹ thuật phức tạp thành narrative dễ hiểu cho audience không chuyên — một kỹ năng cốt lõi của Solution Architect.

### Kế hoạch tuần tiếp theo:
Hoàn thành chương trình thực tập FCAJ. Tiếp tục học theo lộ trình AWS Certification (AWS Solutions Architect Associate) và đóng góp open-source cho cộng đồng.
