---
title: "5.1.3 Thiết kế Hệ thống Chi tiết"
weight: 3
chapter: false
---


### 1. Kiến trúc Cơ sở dữ liệu (Database Design)

Thay vì sử dụng cơ sở dữ liệu quan hệ truyền thống (Relational Database) chia thành nhiều bảng phức tạp, hệ thống lựa chọn Amazon DynamoDB với chiến lược **`Single-Table Design`**. 

Nguyên lý của thiết kế này là lưu trữ nhiều loại thực thể (Users, Transactions, Budgets) vào trong một bảng duy nhất để tối ưu hóa triệt để mô hình truy vấn (Access Pattern), giảm chi phí phần cứng và hạn chế các phép JOIN đắt đỏ. Dữ liệu được quản lý bằng cặp khóa: **`Partition Key (PK)`** và **`Sort Key (SK)`**.

**Ví dụ thiết kế:**
- Bản ghi Profile người dùng: `PK=USER#123`, `SK=PROFILE`
- Bản ghi Giao dịch số 1: `PK=USER#123`, `SK=TXN#20240701-001`
- Bản ghi Giao dịch số 2: `PK=USER#123`, `SK=TXN#20240701-002`
- Bản ghi Ngân sách ăn uống: `PK=USER#123`, `SK=BUDGET#food`

Nhờ cấu trúc này, chỉ với một câu lệnh Query duy nhất vào `PK=USER#123`, hệ thống có thể kéo (fetch) về toàn bộ dữ liệu vòng đời của một người dùng.

### 2. Thiết kế API (API Design)

Hệ thống cung cấp một tập hợp các RESTful APIs tuân thủ chặt chẽ các chuẩn mực giao tiếp:
- **`GET /transactions`**: Lấy danh sách giao dịch (Trạng thái thành công: `200 OK`)
- **`POST /transactions`**: Tạo mới giao dịch (Trạng thái thành công: `201 Created`)
- **`PUT /transactions/{id}`**: Cập nhật thông tin (Trạng thái thành công: `200 OK`)
- **`DELETE /transactions/{id}`**: Xóa bản ghi (Trạng thái thành công: `204 No Content`)

**Xử lý mã lỗi chuẩn:**
- `400 Bad Request`: Sai định dạng dữ liệu đầu vào.
- `401 Unauthorized`: Token bị thiếu, sai hoặc đã hết hạn.
- `403 Forbidden`: Token hợp lệ nhưng user không đủ quyền truy cập tài nguyên.
- `500 Internal Server Error`: Lỗi phát sinh ngoài dự kiến từ phía Server.

### 3. Luồng Xác thực (Authentication Flow)

Bảo mật được thiết lập ở mức cao nhất thông qua giao thức **`OAuth2`** và **`OpenID Connect (OIDC)`**.

- Trình duyệt yêu cầu xác thực bằng Username/Password qua Amazon Cognito.
- Thành công, Cognito trả về bộ mã thông báo **`JWT`** bao gồm: `ID Token` (thông tin định danh người dùng), `Access Token` (chìa khóa ủy quyền để gọi API) và `Refresh Token` (dùng để lấy Access Token mới khi hết hạn mà không cần đăng nhập lại).
- Các API Requests tới API Gateway phải chứa chuỗi `Authorization: Bearer <Access_Token>`.
- API Gateway đóng vai trò làm Authorizer, xác minh tính toàn vẹn của **`JWT`** trước khi cho phép Lambda thực thi tác vụ (Delegated Authorization).

### 4. Thiết kế Bảo mật Toàn diện (Security Design)

Bên cạnh luồng xác thực, lớp giáp bảo vệ ứng dụng được gia cố bởi các nguyên lý:

- **Least Privilege (Đặc quyền tối thiểu):** Các tài nguyên AWS như Lambda hay API Gateway chỉ được cấp quyền IAM vừa đủ để thực hiện chức năng cụ thể, ngăn chặn rủi ro leo thang đặc quyền.
- **HTTPS & SSL/TLS:** Mọi lưu lượng kết nối qua CloudFront hay API Gateway đều phải được mã hóa in-transit bằng chứng chỉ ACM.
- **Origin Access Control (OAC):** Ngăn chặn người dùng truy cập trực tiếp vào S3 Bucket, buộc mọi truy cập phải đi qua lớp cache của CloudFront.
- **WAFv2:** Tường lửa bảo vệ layer 7, thiết lập các rules chống lại bot xấu, SQL Injection, XSS...
- **Secrets Manager:** Quản lý an toàn khóa bí mật (Gemini API Key), loại bỏ hoàn toàn mã hard-code trong ứng dụng.

### 5. Kiến trúc Thông báo (Notification Architecture)

Tuân thủ nguyên tắc **Loose Coupling (Kết nối lỏng lẻo)** và **Asynchronous Processing (Xử lý bất đồng bộ)**, ta KHÔNG sử dụng Lambda chính để gửi Email trực tiếp (rất dễ gây Timeout).

Thay vào đó, hệ thống sử dụng sức mạnh kết hợp của Amazon SNS và Amazon SQS:
- Lambda tạo thông báo đẩy bản tin lên **SNS Topic** (Publisher).
- SNS quạt (fan-out) bản tin đó vào **SQS Queue**.
- Một Lambda Worker (Consumer) độc lập kéo tin từ SQS Queue để thực hiện gửi Email qua dịch vụ SES.
- Kiến trúc này tạo ra "bộ đệm" an toàn (buffer), hỗ trợ tự động gửi lại (retry) và phân loại tin lỗi vào Dead Letter Queue (DLQ) để xử lý sau.
