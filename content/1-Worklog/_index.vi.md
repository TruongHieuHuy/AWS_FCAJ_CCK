---
title: "Nhật ký công việc"
date: 2026-05-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Đây là toàn bộ nhật ký công việc thực tập 12 tuần của tôi trong khuôn khổ chương trình **First Cloud AI Journey (FCAJ)**, tích hợp song song **Lộ trình thực hành 16 bài AWS Labs chuẩn FCAJ** và **Tiến độ phát triển Dự án nhóm (Serverless Budget Tracker) & Workshop cá nhân**.

Lộ trình 12 tuần được tổ chức theo 5 giai đoạn tăng tiến rõ rệt:

**Giai đoạn 1 — Thiết lập môi trường, Onboarding & Thiết kế hệ thống (Tuần 1–3)**

**Tuần 1:** [Khởi động, Phân tích Root Cause & Proposal](1.1-Week1/) — Nghiên cứu định hướng FCAJ & lộ trình Cloud Journey; khởi tạo tài khoản AWS, xử lý sự cố tài khoản bị khóa và thực hiện Root Cause Analysis; khảo sát bài toán tài chính và định hình phạm vi dự án nhóm Budget Tracker.

**Tuần 2:** [Onboarding Tasks & Mitigation Strategy](1.2-Week2/) — Giải quyết blocker bằng tài khoản dự phòng; hoàn thành 5/5 nhiệm vụ Onboarding (EC2, Lambda, RDS Aurora, AWS Budgets, Bedrock Claude 3 Haiku Model Access); kích hoạt $100 AWS Cloud Credits; thống nhất phân công vai trò nhóm.

**Tuần 3:** [AWS Budgets/CloudWatch & Thiết kế Kiến trúc](1.3-Week3/) — Xây dựng Khung quản lý chi phí AWS Budgets/CloudWatch; tham dự AWS Community Day 2026 (GenAI & Multi-Agent); chốt sơ đồ Serverless Stack (API Gateway → C# Lambda → DynamoDB → S3); soạn thảo Proposal với AWS Pricing Calculator.

---

**Giai đoạn 2 — Hạ tầng Mạng VPC, DynamoDB & Backend Core (Tuần 4–6)**

**Tuần 4:** [VPC Network, Cognito Auth & Bedrock AgentCore](1.4-Week4/) — Tham vấn Mentor khắc phục sự cố IAM/CloudShell; tham gia AWS Student Builder Group & nghiên cứu repo "Hera" (Bedrock AgentCore Voice Agents); provision VPC Subnets, Cognito User Pool Auth & phát triển C# Lambda CRUD APIs.

**Tuần 5:** [Lab 2-3 VPC Troubleshooting, DynamoDB & S3 Presigned URL](1.5-Week5/) — Nghiệm thu Lab 2 (AWS Networking & VPC); troubleshooting nghẽn kết nối EC2 trong Lab 3; thiết kế DynamoDB Single-Table Schema (`PK`/`SK`); triển khai cơ chế S3 Presigned URL cho upload ảnh hóa đơn.

**Tuần 6:** [Lab 3-4 EC2 Lifecycle, API Gateway & Business Logic](1.6-Week6/) — Nghiệm thu Lab 3 (VPC Security/NAT/VPN); hoàn thành >50% Lab 4 (Windows Server 2025/Linux, Custom AMI, EBS Snapshots); thiết lập API Gateway REST API với Cognito JWT Authorizer (VTL mapping) & 3 C# Lambdas cốt lõi; bàn giao OpenAPI specs.

---

**Giai đoạn 3 — Nghiệm thu Chuỗi AWS Labs & AI/Edge Security (Tuần 7–8)**

**Tuần 7:** [Chuỗi Lab 4-9, Cold Start Optimization & Module 5-6](1.7-Week7/) — Nghiệm thu liên hoàn chuỗi Lab 4-9 (IAM Governance, EC2-RDS Multi-AZ, Auto Scaling, ALB, CloudWatch, AWS Support); khởi động Lab 10 CloudFormation IaC; gỡ lỗi CORS/JWT tích hợp UI; tối ưu Cold Start C# Lambda (`ReadyToRun`, 3.5s ➔ ~800ms); hoàn thiện Module 5-6 Workshop.

**Tuần 8:** [Advanced AWS Labs 10-14, Gemini AI & Edge Security](1.8-Week8/) — Trải nghiệm môi trường doanh nghiệp; hoàn thành các bài AWS Labs đến Lab 14; tham gia AWS FCAJ Community Day; tích hợp Google Gemini 2.5 Flash (Structured Outputs auto-categorization & Financial Chatbot with Guardrails); cấu hình CloudFront CDN + AWS WAFv2; khởi động dự án cá nhân Workshop Web report.

---

**Giai đoạn 4 — 100% AWS Labs Completion, Event-Driven & Document Alignment (Tuần 9–10)**

**Tuần 9:** [Nghiệm thu 100% Lab 15-16 ECS/Docker & Event-Driven Async Pipeline](1.9-Week9/) — Nghiệm thu 100% Lab 15 (Docker) & Lab 16 (Amazon ECS Blue/Green Deployment); hoàn tất chuỗi 16 bài AWS Labs; xây dựng luồng thông báo bất đồng bộ SQS + SNS với Idempotency pattern (DynamoDB TTL 24h) & EventBridge Cron scheduler.

**Tuần 10:** [Final Review, Single Source of Truth & Well-Architected Framework](1.10-Week10/) — Nghiệm thu 100% Dự án nhóm & Cá nhân; phát hiện bất đồng bộ tài liệu và refactor toàn bộ Proposal, Blog, Workshop theo tiêu chuẩn Single Source of Truth; nghiên cứu AWS Well-Architected Framework.

---

**Giai đoạn 5 — Infrastructure as Code, CI/CD Pipeline & Handover (Tuần 11–12)**

**Tuần 11:** [Infrastructure as Code (AWS SAM) & GitHub Actions OIDC](1.11-Week11/) — Soạn thảo AWS SAM `template.yaml` đóng gói toàn bộ hạ tầng Serverless từ kinh nghiệm Lab 10; xây dựng CI/CD Pipeline tự động qua GitHub Actions tích hợp cơ chế xác thực OIDC (zero long-lived credentials); xuất bản Module 11 Workshop.

**Tuần 12:** [UAT, Cost Audit, Resource Cleanup & Báo cáo tổng kết](1.12-Week12/) — Thực hiện User Acceptance Testing (UAT) toàn diện; kiểm toán AWS Cost Explorer; thực hiện Resource Cleanup (Module 12) giải phóng 100% billable resources trên AWS Cloud; biên soạn Báo cáo thực tập tổng kết.
