---
title: "Nhật ký công việc Tuần 8"
date: 2026-05-04
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Trải nghiệm môi trường doanh nghiệp thực tế; đẩy nhanh tiến độ AWS Labs (hoàn thành đến bài Lab 14).
* Tích hợp Google Gemini API (`gemini-2.5-flash`) tự động phân loại giao dịch (Structured Output) & AI Chatbot tư vấn tài chính.
* Thiết lập Edge Security (CloudFront CDN + AWS WAFv2); tham gia AWS FCAJ Community Day và khởi động dự án Workshop cá nhân.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Trải nghiệm làm việc trực tiếp tại công ty thực tập. Tích hợp Gemini REST API (`gemini-2.5-flash`) vào `AiFunction` Lambda C#: gọi API qua `HttpClient`, cấu hình **Structured Output** (JSON Schema enforcement) phân loại tự động danh mục chi tiêu. | 22/06/2026 | 24/06/2026 | [Gemini API Documentation](https://ai.google.dev/gemini-api/docs) |
| Thứ 5 - Thứ 6 | Đẩy nhanh tiến độ AWS Labs (đến **Lab 14**). Thiết kế sơ đồ Workflow HLA/LLA dự án nhóm và nhận feedback từ Mentor. Triển khai AI Financial Chatbot trên React với **System Prompt Guardrails** giới hạn phạm vi tư vấn. | 25/06/2026 | 26/06/2026 | [Gemini System Instructions](https://ai.google.dev/gemini-api/docs/system-instructions) |
| Thứ 7 - CN | Tham gia sự kiện AWS FCAJ Community Day. Cấu hình **CloudFront CDN** + **AWS WAFv2** (Rate Limiting 1000 req/5min, SQLi/XSS protection). Khởi động dự án cá nhân (Workshop báo cáo Web), clone source code template. Hoàn thành Module 7 Workshop. | 27/06/2026 | 28/06/2026 | [AWS WAFv2 Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Kết quả đạt được tuần 8:

* Hoàn thành các bài thực hành AWS Labs nâng cao đến bài Lab 14.
* `AiFunction` phân loại giao dịch chính xác nhờ Structured Output constraint; AI Chatbot tư vấn tài chính hoạt động an toàn trong guardrails.
* Hệ thống biên CloudFront + WAFv2 được thiết lập bảo mật; dự án cá nhân Workshop báo cáo Web được khởi tạo thành công.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Gemini Structured Output (JSON Schema enforcement) giải quyết triệt để vấn đề non-deterministic LLM output: buộc AI luôn trả về đúng định dạng JSON mong muốn để lưu trực tiếp vào DynamoDB mà không cần regex parsing. Việc kết hợp CloudFront CDN + WAFv2 Rate Limiting bảo vệ API khỏi các đợt tấn công DDoS và automated scraping.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Trải nghiệm trực tiếp tại doanh nghiệp giúp tiệm cận phong cách làm việc thực tế. Tính năng AI auto-categorization giúp loại bỏ rào cản nhập liệu thủ công cho người dùng. System Prompt guardrails là thành tố quản trị rủi ro không thể thiếu để tránh các câu trả lời tư vấn tài chính sai lệch.

### Kế hoạch tuần tiếp theo:
Triển khai & nghiệm thu Lab 15 (Docker) & Lab 16 (Amazon ECS Blue/Green); xây dựng kiến trúc Event-Driven SQS/SNS và tự động hóa báo cáo tháng.
