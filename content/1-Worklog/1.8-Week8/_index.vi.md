---
title: "Nhật ký công việc Tuần 8"
date: 2026-05-04
weight: 8
chapter: false
pre: " <b> 1.8 </b> "
---

### Mục tiêu tuần 8:

* Trải nghiệm môi trường doanh nghiệp thực tế, đẩy nhanh tiến độ AWS Labs (hoàn thành đến bài Lab 14).
* Tích hợp Google Gemini 2.5 Flash API (Structured Outputs auto-categorization & Financial Chatbot with Guardrails).
* Thiết lập Edge Security (CloudFront CDN + AWS WAFv2), tham gia AWS FCAJ Community Day và khởi động dự án Workshop cá nhân.

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 3 | Thực tập trực tiếp tại công ty. Đẩy nhanh tiến độ làm AWS Labs (hoàn thành đến bài Lab 14). Vẽ sơ đồ Workflow (HLA/LLA) dự án nhóm và xin feedback từ Mentor. | 22/06/2026 | 23/06/2026 | [AWS Architecture Center](https://aws.amazon.com/architecture/) |
| Thứ 4 - Thứ 6 | Tích hợp **Google Gemini 2.5 Flash**: viết `AiFunction` C# Lambda sử dụng `gemini-2.5-flash` với Structured Output (JSON schema) tự động phân loại giao dịch (Ví dụ: `Lương` ➔ `Thu nhập`, `Starbucks` ➔ `Ăn uống`). Phát triển Chatbot tài chính tích hợp System Prompt Guardrails. | 24/06/2026 | 26/06/2026 | [Google Gemini Structured Outputs](https://ai.google.dev/gemini-api/docs/structured-output) |
| Thứ 7 - CN | Tham gia sự kiện AWS FCAJ Community Day. Cấu hình **CloudFront CDN** + **AWS WAFv2** (Rate Limiting 1000 req/5min, SQLi/XSS protection). Khởi động dự án cá nhân (Workshop báo cáo Web), clone source code template. Hoàn thành Module 7 Workshop. | 27/06/2026 | 28/06/2026 | [AWS WAFv2 Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html) |

### Kết quả đạt được tuần 8:

* Tiến độ AWS Labs đạt cột mốc Lab 14 đúng kế hoạch đề ra.
* `AiFunction` phân loại giao dịch chính xác nhờ Structured Output constraint, AI Chatbot tư vấn tài chính hoạt động an toàn trong guardrails.
* Hệ thống biên CloudFront + WAFv2 được thiết lập bảo mật, dự án cá nhân Workshop báo cáo Web được khởi tạo thành công.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
Sử dụng Google Gemini 2.5 Flash qua SDK với **Structured Outputs (Response Schema)** đảm bảo LLM luôn trả về JSON hợp lệ 100%, loại bỏ lỗi JSON parsing. Kết hợp CloudFront CDN + AWS WAFv2 tạo thành **Edge Security Perimeter** chặn các đợt tấn công Web (SQLi, XSS, DDoS) trước khi chạm vào Lambda Backend.

#### Hệ thống & Phối hợp (BA/SA Perspective)
Việc tham gia AWS FCAJ Community Day mở ra cơ hội giao lưu học hỏi kinh nghiệm triển khai Cloud thực tế. Guardrails thiết lập cho Financial Chatbot ngăn ngừa LLM đưa ra lời khuyên tài chính sai lệch (hallucination), tuân thủ tiêu chuẩn AI Ethics & Safety.

### Kế hoạch tuần tiếp theo:
Triển khai & nghiệm thu Lab 15 (Docker) & Lab 16 (Amazon ECS Blue/Green), xây dựng kiến trúc Event-Driven SQS/SNS và tự động hóa báo cáo tháng.
