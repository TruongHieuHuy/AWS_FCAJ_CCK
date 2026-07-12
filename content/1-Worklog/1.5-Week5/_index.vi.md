---
title: "Nhật ký công việc Tuần 5"
date: 2026-05-04
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Thiết kế DynamoDB Single-Table Schema tối ưu cho tất cả Access Patterns của Budget Tracker.
* Cấu hình S3 Bucket và triển khai cơ chế S3 Presigned URL để upload hóa đơn an toàn.
* Tích hợp AWS SDK DynamoDB vào C# Lambda và tối ưu query để giảm RCU/WCU tiêu thụ.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Thiết kế DynamoDB Single-Table Schema: xác định Partition Key (`PK`) và Sort Key (`SK`) cho các entity USER, TRANSACTION, BUDGET. Họp chốt kiến trúc với Database Engineer để đảm bảo các Access Patterns (lấy transactions theo tháng, kiểm tra budget theo category) không gây **Hot Partition** và tiêu thụ RCU/WCU tối thiểu. | 01/06/2026 | 03/06/2026 | [DynamoDB Core Components](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html) |
| Thứ 5 - Thứ 6 | Provision S3 Bucket với cấu hình: Block Public Access toàn bộ, Server-Side Encryption (SSE-S3), Bucket Policy cho phép Lambda role truy cập. Triển khai cơ chế Presigned URL (TTL 15 phút) trong C# Lambda cho phép client upload ảnh hóa đơn trực tiếp lên S3 mà không đi qua Backend — giảm tải Lambda và tiết kiệm băng thông. | 04/06/2026 | 05/06/2026 | [Amazon S3 Presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-presigned-url.html) |
| Thứ 7 - CN | Tích hợp `AWSSDK.DynamoDBv2` vào C# Lambda: sử dụng `DynamoDBContext` với `QueryAsync` (thay vì `ScanAsync`) để truy vấn theo PK — tránh Full Table Scan tốn kém. Cấu hình S3 CORS policy cho phép domain Frontend thực hiện PUT request trực tiếp. | 06/06/2026 | 07/06/2026 | [AWS SDK for .NET - DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DotNetSDKHighLevel.html) |

### Kết quả đạt được tuần 5:

* Single-Table Schema hoàn chỉnh, hỗ trợ tất cả Access Patterns với chi phí RCU/WCU được tối ưu.
* S3 Presigned URL hoạt động: client upload hóa đơn trực tiếp, Lambda không phải xử lý binary data.
* C# Lambda kết nối DynamoDB thành công với `QueryAsync`, tránh Hot Partition và Full Table Scan.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
DynamoDB Single-Table Design yêu cầu tư duy **Access-Pattern-First** thay vì Entity-First: thay vì thiết kế bảng theo entity (User table, Transaction table riêng biệt), ta thiết kế theo câu query thực tế. Ví dụ: `PK=USER#userId` + `SK=TRANSACTION#2026-06` cho phép lấy toàn bộ transaction của tháng 6 bằng một query duy nhất mà không cần Scan. Việc phân tách upload hóa đơn qua S3 Presigned URL thay vì multipart form qua Lambda giúp tránh Lambda timeout với file lớn và giảm chi phí invocation.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Bài toán DynamoDB Hot Partition là một rủi ro ẩn: nếu nhiều user cùng truy cập một Partition Key (ví dụ: admin account), throughput bị bottleneck tại một partition duy nhất. Việc thiết kế PK phân tán theo `userId` ngay từ đầu đảm bảo **horizontal scalability** — khi user base tăng, DynamoDB tự động phân phối tải đều. Đây là quyết định kiến trúc có tác động dài hạn mà nếu không giải quyết sớm, việc migration schema sau này sẽ cực kỳ tốn kém.

### Kế hoạch tuần tiếp theo:
Cấu hình API Gateway REST API với Cognito JWT Authorizer và triển khai business logic hoàn chỉnh cho các Lambda functions.
