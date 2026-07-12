---
title: "5.1.4 Chiến lược Vận hành & Triển khai"
weight: 4
chapter: false
---


### 1. Chiến lược Triển khai Hạ tầng (Deployment Strategy)

Để đảm bảo tính nhất quán và tự động hóa trong quản lý, dự án áp dụng mô hình Infrastructure as Code (IaC) và quy trình CI/CD:

- **Infrastructure as Code (IaC):** Toàn bộ tài nguyên (Lambda, DynamoDB, API Gateway) được khai báo dưới dạng mã nguồn thông qua **AWS SAM** (Serverless Application Model). Chỉ bằng các file `template.yaml`, chúng Phần có thể triển khai môi trường mới trong vài phút.
- **CI/CD Pipeline:** Sử dụng **GitHub Actions** để tự động hóa chuỗi Build -> Test -> Deploy. Mỗi lệnh commit hợp lệ vào nhánh `main` sẽ kích hoạt pipeline để biên dịch mã nguồn C# .NET, đóng gói React Frontend và triển khai hạ tầng SAM lên môi trường Dev/Prod một cách mượt mà.
- **Rollback an toàn:** Tính năng CloudFormation (nền tảng của SAM) hỗ trợ rollback tự động đưa hệ thống về trạng thái an toàn trước đó nếu có lỗi phát sinh trong quá trình deploy.

### 2. Chiến lược Kiểm thử Hệ thống (Testing Strategy)

Chất lượng của phần mềm được đảm bảo thông qua tháp kiểm thử nhiều cấp độ:

- **Unit Testing (Kiểm thử Đơn vị):** Kiểm tra logic cục bộ của từng hàm Lambda, Mocking cơ sở dữ liệu DynamoDB. Giúp phát hiện sớm lỗi logic xử lý nghiệp vụ.
- **Integration Testing (Kiểm thử Tích hợp):** Xác minh sự kết nối thông suốt giữa Lambda và DynamoDB, Lambda và Cognito trong môi trường test/staging.
- **E2E Testing (Kiểm thử Đầu - Cuối):** Mô phỏng trải nghiệm người dùng thực bằng các công cụ Automation, đảm bảo kịch bản từ lúc Đăng nhập -> Sinh API -> Ghi Database hoạt động hoàn hảo.
- **Continuous Testing:** Gắn toàn bộ các kịch bản test vào quy trình CI/CD để chặn các bản cập nhật chứa lỗi (bug) đẩy lên Production.

### 3. Chiến lược Giám sát (Monitoring Strategy)

Mọi nhất cử nhất động của hệ thống được đặt dưới sự kiểm soát của Amazon CloudWatch:

- **Logs Insights:** Ghi log chi tiết tiến trình gọi API Gateway, xử lý Lambda và xác thực Cognito.
- **Metrics Dashboard:** Đo lường sức khỏe hệ thống thời gian thực với các chỉ số như Số lượng request, Thời gian phản hồi (Latency), Tỷ lệ lỗi (Error Rate) và Consumed Capacity của DynamoDB.
- **Alarms (Báo động):** Thiết lập các ngưỡng giới hạn (ví dụ: Lambda lỗi quá 5 lần/phút). CloudWatch Alarms sẽ kích hoạt SNS gửi thông báo SMS/Email khẩn cấp đến đội ngũ quản trị.

### 4. Thực hành chuẩn (Best Practices)

Để duy trì một dự án vững mạnh lâu dài, hệ thống tuân thủ chặt chẽ các nguyên tắc sau:

- **Quy ước Đặt tên (Naming Convention):** Phân định rõ ràng tên tài nguyên theo môi trường, ví dụ: `BudgetTracker-dev-table` và `BudgetTracker-prod-table`.
- **Sử dụng Biến môi trường (Environment Variables):** Tuyệt đối không hard-code tên tài nguyên hoặc cấu hình. Tham số hóa mọi thứ.
- **Tính lũy đẳng (Idempotency):** Thiết kế API (đặc biệt là tạo giao dịch mới) có khả năng tự nhận diện các request trùng lặp, đảm bảo nếu Client có lỡ gửi lại request (do rớt mạng), giao dịch không bị tạo đúp trong Database.
- **Xử lý Ngoại lệ (Exception Handling):** Bọc toàn bộ các logic nguy hiểm bằng khối Try/Catch. Đảm bảo in log chi tiết lỗi thay vì ném lỗi thô ra cho người dùng cuối.
- **Phiên bản API (API Versioning):** Thiết kế Endpoint có dạng `/api/v1/...` để dễ dàng nâng cấp hoặc thay đổi cấu trúc dữ liệu ở phiên bản `/v2/` mà không làm chết ứng dụng của người dùng đang xài bản cũ.
