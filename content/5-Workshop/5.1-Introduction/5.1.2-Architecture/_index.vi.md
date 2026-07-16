---
title: "5.1.2 Kiến trúc Serverless & Luồng dữ liệu"
weight: 2
chapter: false
---


### 1. Tổng quan về AWS Serverless

**Serverless (Điện toán phi máy chủ)** là mô hình đám mây cho phép nhà phát triển tập trung hoàn toàn vào việc viết code mà không phải lo lắng về việc quản lý, cấu hình hay bảo trì máy chủ vật lý. AWS tự động đảm nhận việc mở rộng quy mô (scaling), cân bằng tải, vá lỗi hệ điều hành và áp dụng mô hình tính phí **"Pay-as-you-go"** (chỉ trả phí cho những gì thực sự sử dụng tới đơn vị mili-giây).

Mô hình này là mảnh ghép hoàn hảo cho **Kiến trúc Hướng sự kiện (Event-driven Architecture)**. Mỗi hành động (như gọi API, upload file, thay đổi dữ liệu) sẽ kích hoạt một hàm xử lý tương ứng (Function-as-a-Service - FaaS). 

### 2. Hệ sinh thái Dịch vụ AWS trong Dự án

Dự án Budget Tracker sử dụng một hệ sinh thái Managed Services mạnh mẽ:

- **AWS Lambda (Compute):** Trái tim của logic nghiệp vụ. Xử lý lưu giao dịch, gọi AI, gửi thông báo mà không cần chạy server 24/7.
- **Amazon API Gateway (API Layer):** Đóng vai trò "cửa trước", tiếp nhận HTTP(S) request, quản lý routing, xác thực, quota và tự động điều hướng tới các hàm Lambda tương ứng.
- **Amazon DynamoDB (Database):** CSDL NoSQL fully-managed, độ trễ mili-giây. Áp dụng Single-Table Design để truy xuất dữ liệu người dùng, giao dịch siêu tốc.
- **Amazon Cognito (Auth):** Dịch vụ Identity. Cung cấp luồng đăng nhập, phát hành token JWT chuẩn OAuth2/OIDC.
- **Amazon S3 & CloudFront (Frontend Delivery):** S3 lưu trữ code ReactJS. CloudFront làm CDN toàn cầu với 750+ Edge locations, đảm bảo load trang cực nhanh và bảo mật bằng Origin Access Control (OAC).
- **Amazon Route 53 & WAF (Networking & Security):** Route 53 định tuyến DNS. WAF làm lá chắn bảo vệ ứng dụng khỏi các cuộc tấn công web phổ biến (SQLi, XSS, Botnets).
- **Amazon SNS & SQS (Messaging):** Decoupling (tách rời) kiến trúc hệ thống. SNS dùng để Publish thông báo, SQS dùng làm hàng đợi (Queue) đảm bảo không mất mát dữ liệu và xử lý bất đồng bộ (ví dụ: gửi email).
- **Amazon EventBridge (Event Bus):** Lập lịch định kỳ (cron job) hoặc điều phối các luồng sự kiện phức tạp.
- **Amazon CloudWatch (Monitoring):** Trung tâm giám sát toàn diện mọi metric, log và báo động (Alarms).
- **AWS Secrets Manager (Security):** Nơi lưu trữ bảo mật các chuỗi kết nối và API Key (ví dụ: Google Gemini API Key), giảm thiểu rủi ro hard-code.

### 3. Giải thích kiến trúc hệ thống

![Sơ đồ kiến trúc Budget Tracker](/images/5-Workshop/5.1-Introduction/architecture.jpg)

Hệ thống được thiết kế theo mô hình **Multi-layer (Nhiều tầng)** nhằm tối đa hóa tính độc lập, dễ dàng nâng cấp và bảo trì:

1. **Frontend Layer:** Ứng dụng SPA (Single Page Application) bằng React, lưu trên S3 và phân phối qua mạng lưới Edge của CloudFront.
2. **API Layer:** API Gateway chặn mọi luồng traffic, kiểm tra xác thực thông qua Cognito authorizer trước khi cho phép đi sâu vào hệ thống.
3. **Business Logic Layer:** Các hàm Lambda xử lý nghiệp vụ độc lập theo hướng microservices (Auth, Transactions, Budget, AI).
4. **Data Layer:** Bảng DynamoDB duy nhất chứa dữ liệu của toàn bộ ứng dụng (Single-Table Design).
5. **AI Layer:** Lambda tương tác với Google Gemini Flash 1.5 để phân loại giao dịch tự động.
6. **Notification Layer:** Luồng xử lý bất đồng bộ SNS -> SQS -> Lambda để gửi thông báo không làm tăng độ trễ (latency) của API chính.

### 4. Luồng dữ liệu hoạt động (Step-by-Step Data Flow)

Dưới đây là một ví dụ minh họa cách dữ liệu chảy qua hệ thống khi thực hiện một chức năng cốt lõi:

**Kịch bản: Người dùng tạo một giao dịch chi tiêu mới**

- **Bước 1 (Xác thực):** Ứng dụng React gửi `POST /transactions` đính kèm chuỗi JWT trong Header Authorization.
- **Bước 2 (Kiểm duyệt):** API Gateway tiếp nhận, gửi JWT sang Cognito để xác thực. Nếu hợp lệ, chuyển tiếp request tới hàm Lambda xử lý giao dịch.
- **Bước 3 (Xử lý Data):** Lambda nhận payload, kiểm tra business logic, lưu bản ghi giao dịch xuống bảng DynamoDB với cấu trúc PK=USER#ID, SK=TXN#ID.
- **Bước 4 (Phân tích AI):** Một hàm Lambda khác được kích hoạt (hoặc xử lý bất đồng bộ qua EventBridge), gọi API Google Gemini đọc description giao dịch để gán nhãn Category (ví dụ: "Groceries", "Utilities") và cập nhật lại DynamoDB.
- **Bước 5 (Gửi thông báo):** Lambda ban đầu phát hành (Publish) một tin nhắn báo hiệu có giao dịch mới lên SNS Topic.
- **Bước 6 (Bất đồng bộ SQS):** SNS đẩy tin nhắn vào SQS Queue. Một Lambda Consumer sẽ lấy tin từ SQS để tiến hành gửi Email/SMS xác nhận cho người dùng, đảm bảo API trả về kết quả (201 Created) gần như tức thì mà không phải chờ email gửi xong.
- **Bước 7 (Giám sát):** Xuyên suốt quá trình, CloudWatch liên tục ghi nhận thời gian phản hồi, số lần gọi API và các log lỗi nếu có.
