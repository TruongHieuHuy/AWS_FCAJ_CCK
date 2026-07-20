---
title: "Nhật ký công việc Tuần 5"
date: 2026-05-04
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Khắc phục lỗi phân quyền IAM, nghiệm thu thành công Lab 2 và thực hành Troubleshooting Lab 3 (EC2/VPC).
* Thiết kế DynamoDB Single-Table Schema tối ưu cho tất cả Access Patterns của Budget Tracker.
* Cấu hình S3 Bucket và triển khai cơ chế S3 Presigned URL để upload ảnh hóa đơn an toàn.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Khắc phục sự cố phân quyền IAM và nghiệm thu bài **Lab 2** (VPC & Networking). Nghiên cứu chuẩn hóa sơ đồ kiến trúc AWS qua draw.io. Thiết kế DynamoDB Single-Table Schema: xác định `PK` và `SK` cho USER, TRANSACTION, BUDGET. | 01/06/2026 | 03/06/2026 | [DynamoDB Core Components](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html) |
| Thứ 5 - Thứ 6 | Triển khai bài **Lab 3**: thực hành Troubleshooting rà soát Security Group, Route Table và VPC do gặp sự cố nghẽn kết nối tại máy chủ EC2. Provision S3 Bucket với SSE-S3 encryption và Block Public Access. | 04/06/2026 | 05/06/2026 | [Amazon S3 Presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) |
| Thứ 7 - CN | Triển khai cơ chế Presigned URL (TTL 15 phút) trong C# Lambda cho phép client upload ảnh hóa đơn trực tiếp lên S3. Tích hợp `AWSSDK.DynamoDBv2` sử dụng `QueryAsync` thay vì `ScanAsync`. Hoàn thiện Module 4 Workshop. | 06/06/2026 | 07/06/2026 | [AWS SDK for .NET - DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DotNetSDKHighLevel.html) |

### Kết quả đạt được tuần 5:

* Nghiệm thu bài Lab 2 thành công và nâng cao kỹ năng troubleshooting mạng VPC trong Lab 3.
* Single-Table Schema hoàn chỉnh trên DynamoDB, hỗ trợ đầy đủ Access Patterns với chi phí tối ưu.
* S3 Presigned URL hoạt động: client upload hóa đơn trực tiếp, Lambda không bị tính phí xử lý file binary.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Kỹ năng troubleshooting mạng trong Lab 3 (rút ra từ việc thiếu Route `0.0.0.0/0` trong Route Table của EC2 Subnet) bổ trợ trực tiếp cho tư duy vận hành hạ tầng Cloud. Với DynamoDB, thiết kế Single-Table yêu cầu tư duy **Access-Pattern-First**: việc đặt `SK=TXN#<timestamp>#<id>` cho phép truy vấn lọc giao dịch theo thời gian nhanh chóng mà không cần Full Table Scan.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Việc tách luồng upload hóa đơn qua S3 Presigned URL thay vì gửi file qua Lambda Backend là quyết định tối ưu chi phí và hiệu năng quan trọng (giảm tải CPU/Memory cho Lambda). Kết hợp việc hoàn thành bài Lab 2 về VPC giúp toàn nhóm tự tin cấu hình hạ tầng lưu trữ và mạng an toàn.

### Kế hoạch tuần tiếp theo:
Nghiệm thu Lab 3 & triển khai Lab 4 (Windows/Linux EC2 lifecycle), cấu hình API Gateway REST API, Cognito JWT Authorizer và 3 Lambda core functions.
