---
title: "Nhật ký công việc Tuần 8"
date: 2026-05-04
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Tích hợp Google Gemini API (`gemini-2.5-flash`) để tự động phân loại giao dịch tài chính.
* Triển khai AI Chatbot tư vấn tài chính cá nhân với guardrails nghiêm ngặt.
* Cấu hình Edge Security: CloudFront CDN + AWS WAFv2 bảo vệ hệ thống khỏi DDoS và injection attacks.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Tích hợp Gemini REST API (`gemini-2.5-flash`) vào `AiFunction` Lambda C#: gọi API qua `HttpClient`, parse response JSON. Thiết kế prompt engineering cho tính năng **auto-categorization**: truyền transaction description → Gemini phân loại sang danh mục (Food, Transport, Shopping...) và trả về kết quả dạng **Structured Output** (JSON schema enforcement) để đảm bảo response luôn parseable. | 22/06/2026 | 24/06/2026 | [Gemini API Documentation](https://ai.google.dev/gemini-api/docs) |
| Thứ 5 - Thứ 6 | Triển khai AI Financial Chatbot trong Frontend React: thiết kế **System Prompt** với guardrails rõ ràng — AI chỉ được trả lời các câu hỏi về quản lý chi tiêu cá nhân, từ chối các câu hỏi ngoài phạm vi (chứng khoán, tiền số) để tránh rủi ro pháp lý về tư vấn đầu tư. | 25/06/2026 | 26/06/2026 | [Gemini System Instructions](https://ai.google.dev/gemini-api/docs/system-instructions) |
| Thứ 7 - CN | Phối hợp với Database Engineer thiết lập Edge Security: cấu hình **CloudFront Distribution** làm CDN trước S3 và API Gateway; gắn **AWS WAFv2 Web ACL** với ruleset: Rate Limit (1000 req/5min/IP), AWS Managed Rules (SQL injection, XSS, Bad Bot protection). Hoàn thành tài liệu Workshop Module 7 (Edge Security). | 27/06/2026 | 28/06/2026 | [AWS WAFv2 Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Kết quả đạt được tuần 8:

* AiFunction tự động phân loại giao dịch với độ chính xác cao nhờ Structured Output enforcement.
* AI Chatbot hoạt động trong phạm vi kiểm soát: guardrails ngăn chặn off-topic responses thành công.
* CloudFront + WAFv2 triển khai và kiểm thử: Rate Limiting và SQL Injection protection hoạt động chính xác.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Gemini Structured Output (JSON Schema enforcement) giải quyết vấn đề **non-deterministic LLM output**: khi không có schema constraint, Gemini có thể trả về text tự do không parseable, gây lỗi runtime trong Lambda. Bằng cách truyền JSON schema mong muốn vào API call, Gemini được ràng buộc luôn trả về đúng format — loại bỏ hoàn toàn việc cần regex/string parsing ở tầng ứng dụng. WAFv2 Rate Limiting với threshold 1000 req/5min/IP là lựa chọn hợp lý cho ứng dụng cá nhân: đủ rộng để không ảnh hưởng UX bình thường nhưng hiệu quả chặn automated scraping và credential stuffing.

#### Hệ thống & Phối hợp (BA/SA Perspective)
AI auto-categorization giải quyết **friction point lớn nhất** trong hành vi nhập liệu tài chính: người dùng phải chọn danh mục thủ công khiến >60% bỏ qua việc ghi chép. Bằng cách cho phép user nhập text tự nhiên ("Ăn phở 50k") và để AI tự phân loại, ứng dụng giảm số bước nhập liệu từ 4 xuống 1 — trực tiếp giảm **User Friction** và tăng **Daily Active Usage**. System Prompt guardrails là yêu cầu không thể thiếu: tư vấn đầu tư không được cấp phép có thể tạo ra rủi ro pháp lý nghiêm trọng cho nhà phát triển.

### Kế hoạch tuần tiếp theo:
Xây dựng kiến trúc xử lý bất đồng bộ SQS/SNS cho hệ thống cảnh báo ngân sách và báo cáo tháng tự động.
