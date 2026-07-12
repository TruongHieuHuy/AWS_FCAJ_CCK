---
title: "Nhật ký công việc"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Đây là toàn bộ nhật ký công việc thực tập 12 tuần của tôi trong khuôn khổ chương trình **First Cloud AI Journey (FCAJ)**, gắn liền với dự án nhóm **Budget Tracker** — ứng dụng quản lý tài chính cá nhân xây dựng trên nền tảng AWS Serverless.

Lộ trình 12 tuần được tổ chức theo 5 giai đoạn tăng tiến rõ rệt:

**Giai đoạn 1 — Thiết lập môi trường & Thiết kế hệ thống (Tuần 1–3)**

**Tuần 1:** [Khởi động & Phân tích Root Cause](1.1-week1/) — Nghiên cứu định hướng FCAJ, khởi tạo tài khoản AWS với security baseline (MFA, IAM Least Privilege), xử lý sự cố tài khoản bị khóa và thực hiện Root Cause Analysis.

**Tuần 2:** [Onboarding & Mitigation Strategy](1.2-week2/) — Giải quyết blocker bằng tài khoản dự phòng, hoàn thành 5/5 nhiệm vụ Onboarding (EC2, Lambda, RDS Aurora, AWS Budgets, Amazon Bedrock), kích hoạt Cloud Credits.

**Tuần 3:** [Thiết kế Kiến trúc & Project Proposal](1.3-week3/) — Chốt Serverless Stack (API Gateway → Lambda C# → DynamoDB → S3), soạn thảo Proposal với ước tính chi phí AWS Pricing Calculator và Work Breakdown Structure theo role.

---

**Giai đoạn 2 — Xây dựng hạ tầng & Backend Core (Tuần 4–6)**

**Tuần 4:** [Provision Hạ tầng Mạng & Cognito](1.4-week4/) — Provision VPC với Public/Private Subnet isolation, cấu hình Amazon Cognito User Pool, triển khai JWT middleware C# và thống nhất API Contract với Frontend.

**Tuần 5:** [DynamoDB Single-Table Design & S3 Presigned URL](1.5-week5/) — Thiết kế Access-Pattern-First schema tránh Hot Partition, tích hợp AWS SDK DynamoDB với `QueryAsync`, triển khai S3 Presigned URL cho upload hóa đơn trực tiếp từ client.

**Tuần 6:** [API Gateway & Lambda Business Logic](1.6-week6/) — Cấu hình Cognito JWT Authorizer trên API Gateway, Payload Mapping Template trích xuất `sub` từ JWT claims, triển khai TransactionFunction/BudgetFunction/ReportFunction với GSI, bàn giao OpenAPI/Swagger spec.

---

**Giai đoạn 3 — Tích hợp & AI/Security (Tuần 7–8)**

**Tuần 7:** [Frontend Integration & Cold Start Optimization](1.7-week7/) — Gỡ lỗi CORS (cấu hình cả API Gateway lẫn Lambda response headers), debug JWT header format, tối ưu Cold Start C# Lambda từ 3.5s xuống <1s bằng `ReadyToRun` compilation và `System.Text.Json` migration.

**Tuần 8:** [Gemini AI Integration & Edge Security](1.8-week8/) — Tích hợp `gemini-2.5-flash` với Structured Output enforcement cho auto-categorization, triển khai AI Chatbot với guardrails System Prompt, cấu hình CloudFront CDN + WAFv2 Rate Limiting và Managed Rules (SQLi, XSS, Bad Bot).

---

**Giai đoạn 4 — Resilience & Observability (Tuần 9–10)**

**Tuần 9:** [Async SNS/SQS Pipeline & EventBridge](1.9-week9/) — Xây dựng Event-Driven Notification Pipeline (SQS buffer → SNS fan-out), triển khai Idempotency Pattern với DynamoDB MessageId TTL, cấu hình Dead Letter Queue và EventBridge Cron scheduler cho monthly summary.

**Tuần 10:** [Final Review & Well-Architected Assessment](1.10-week10/) — Phát hiện và khắc phục document drift (Single Source of Truth), đánh giá kiến trúc theo AWS Well-Architected Framework (Security & Cost Optimization Pillars), lập backlog cải tiến cho tuần 11-12.

---

**Giai đoạn 5 — Tự động hóa & Bàn giao (Tuần 11–12)**

**Tuần 11:** [Infrastructure as Code & CI/CD Pipeline](1.11-week11/) — Soạn thảo AWS SAM `template.yaml` định nghĩa toàn bộ hạ tầng, thiết lập GitHub Actions pipeline với OIDC authentication (zero long-lived credentials), tự động hóa test → build → deploy trên mỗi push.

**Tuần 12:** [UAT, Cost Audit & Project Handover](1.12-week12/) — Thực hiện User Acceptance Testing toàn diện, kiểm toán AWS Cost Explorer (phát hiện và loại bỏ NAT Gateway idle cost), dọn dẹp CloudFormation Stack, biên soạn báo cáo thực tập và Slide thuyết trình trước hội đồng đánh giá.
