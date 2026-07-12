---
title: "Nhật ký công việc Tuần 7"
date: 2026-05-04
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Giải quyết các lỗi CORS và JWT parsing phát sinh trong quá trình tích hợp Frontend-Backend.
* Tối ưu Lambda Cold Start từ ~3.5s xuống dưới 1s bằng kỹ thuật ReadyToRun compilation.
* Hoàn thành tài liệu Workshop Module 5 và Module 6.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Phối hợp với Frontend Engineer: debug luồng API call từ ReactJS đến API Gateway. Xác định và khắc phục lỗi **CORS**: bật CORS trên từng Method của API Gateway (OPTIONS preflight), thêm headers `Access-Control-Allow-Origin`, `Access-Control-Allow-Headers` vào Lambda response. Debug lỗi JWT payload: xác minh `Authorization: Bearer <token>` header format và cấu hình Cognito Authorizer nhận đúng header key. | 15/06/2026 | 17/06/2026 | [API Gateway CORS](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html) |
| Thứ 5 - Thứ 6 | Tối ưu Cold Start C# Lambda: bật `PublishReadyToRun=true` trong `.csproj` để pre-compile IL sang native code; giảm số lượng NuGet package dependencies; chuyển từ `Newtonsoft.Json` sang `System.Text.Json` (lightweight serializer). Đo lường kết quả bằng Lambda CloudWatch Logs (Init Duration metric). | 18/06/2026 | 19/06/2026 | [Lambda Cold Start Optimization](https://docs.aws.amazon.com/lambda/latest/dg/snapstart.html) |
| Thứ 7 - CN | Soạn thảo và hoàn thiện tài liệu Workshop: **Module 5** (DynamoDB Single-Table Design — lý thuyết, lab và giải thích Access Patterns) và **Module 6** (C# Serverless Web API — scaffold, Lambda handler, DynamoDB integration). | 20/06/2026 | 21/06/2026 | [AWS Workshop Studio](https://studio.us-east-1.prod.workshops.aws/) |

### Kết quả đạt được tuần 7:

* Giải quyết triệt để lỗi CORS và JWT parsing — Frontend kết nối API Backend thành công 100%.
* Cold Start C# Lambda giảm từ ~3.5s xuống ~800ms sau khi áp dụng ReadyToRun + Json serializer optimization.
* Hoàn thành Module 5 & 6 Workshop với đầy đủ lab steps và giải thích kỹ thuật.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
CORS không phải "tính năng" mà là **cơ chế bảo mật của trình duyệt** — cần cấu hình ở cả hai tầng: API Gateway (OPTIONS method + CORS headers) và Lambda response (phải include headers trong mọi response object, kể cả error responses). Cold Start của C# Lambda là vấn đề điển hình của JIT-compiled runtime: ReadyToRun pre-compiles managed code thành native instructions, loại bỏ JIT compilation overhead tại runtime. Kết hợp với việc giảm payload cold-loading (ít packages hơn), Init Duration giảm từ 3.5s xuống <1s — cải thiện ~70%.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Từ góc độ User Experience: Lambda Cold Start 3.5s trên API call đầu tiên sau idle period là **trải nghiệm không chấp nhận được** với ứng dụng tài chính — người dùng sẽ nghĩ hệ thống bị lỗi. Cải thiện xuống <1s đảm bảo **Perceived Performance** đáp ứng ngưỡng chấp nhận (Google Research: bounce rate tăng 32% khi load time >3s). Đây là một ví dụ điển hình về việc quyết định kỹ thuật có tác động trực tiếp đến Business Metric (User Retention).

### Kế hoạch tuần tiếp theo:
Tích hợp Google Gemini API cho tính năng AI auto-categorization và triển khai Edge Security với CloudFront + AWS WAFv2.
