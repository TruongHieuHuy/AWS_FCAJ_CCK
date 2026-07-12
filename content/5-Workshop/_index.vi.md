---
title: "Workshop"
date: 2026-07-05
weight: 5
chapter: false
pre: " <b> 5. </b> "
---


### Tổng quan

Chào mừng bạn đến với tài liệu hướng dẫn (Workshop) triển khai ứng dụng quản lý tài chính cá nhân **Budget Tracker**. Trong chuỗi bài thực hành này, chúng ta sẽ từng bước xây dựng một hệ thống hoàn chỉnh ứng dụng kiến trúc **AWS Serverless** và **Event-driven Architecture** (Kiến trúc hướng sự kiện).

Ứng dụng hướng đến việc cung cấp một giải pháp quản lý chi tiêu cá nhân linh hoạt, tích hợp tính năng tự động phân loại giao dịch bằng trí tuệ nhân tạo (Google Gemini) và hệ thống thông báo đa kênh, trong khi vẫn tối ưu hóa chi phí vận hành ở mức thấp nhất nhờ sức mạnh của điện toán đám mây.

### Mục tiêu đạt được

Sau khi hoàn thành 12 Module thực hành của khóa học, bạn sẽ có khả năng:
- Thiết lập và quản lý danh tính người dùng an toàn qua **Amazon Cognito**.
- Xây dựng tầng API với **Amazon API Gateway** và các hàm xử lý serverless với **AWS Lambda**.
- Quản trị cơ sở dữ liệu NoSQL hiệu năng cao với **Amazon DynamoDB** (áp dụng mô hình Single-Table Design).
- Lưu trữ và phân phối ứng dụng React tĩnh toàn cầu thông qua **Amazon S3** và **Amazon CloudFront**.
- Xử lý các luồng nghiệp vụ bất đồng bộ bằng **Amazon SNS** và **Amazon SQS**.
- Triển khai Infrastructure as Code (IaC) tự động thông qua **AWS SAM** và **GitHub Actions**.

### Phân công thành viên — 4 Thành viên, 1 Account chung

| Thành viên | Khối phụ trách | Mục |
|---|---|---|
| Chung | IAM + Route 53 + WAFv2 (Infrastructure Foundation) | [5.3](5.3-Infrastructure-IAM/) |
| Khiêm | DynamoDB + Secrets Manager + S3 (Database & Data layer) + Cognito Auth & Edge | [5.4](5.4-Database-Storage/), [5.7](5.7-Edge-Security/) |
| Huy | API Gateway + Lambda Core (Transaction/Budget/Report) + Notifications (SNS/SQS/EventBridge) | [5.5](5.5-Backend-API/), [5.8](5.8-Notifications/) |
| Công | React Frontend + Cognito login flow + Gemini AI integration | [5.6](5.6-Frontend-Auth-AI/) |

(Các bài thực hành 1, 2, 9, 10, 11, 12 — Introduction, Prerequisites, Testing, Monitoring, Deployment, Cleanup — được thực hiện chung bởi cả nhóm.)

### Cấu trúc nội dung

Workshop được chia thành 12 bài học liên tiếp (Modules), bao phủ toàn bộ vòng đời phát triển phần mềm:

1. [Module 1 - Tổng quan Dự án & Kiến trúc](5.1-Introduction/)
2. [Module 2 - Yêu cầu Môi trường & Setup Chung](5.2-Prerequisites/)
3. [Module 3 - Nền tảng Hạ tầng & Phân quyền IAM](5.3-Infrastructure-IAM/)
4. [Module 4 - Lớp Dữ liệu (DynamoDB & S3)](5.4-Database-Storage/)
5. [Module 5 - Lớp Backend Core (Lambda & API Gateway)](5.5-Backend-API/)
6. [Module 6 - Frontend, Xác thực & Tích hợp AI](5.6-Frontend-Auth-AI/)
7. [Module 7 - Bảo mật Edge & Phân phối Toàn cầu](5.7-Edge-Security/)
8. [Module 8 - Luồng Xử lý Bất đồng bộ & Thông báo](5.8-Notifications/)
9. [Module 9 - Chiến lược Kiểm thử End-to-End](5.9-Testing/)
10. [Module 10 - Giám sát Hệ thống & Vận hành](5.10-Monitoring/)
11. [Module 11 - Triển khai Tự động với IaC & CI/CD](5.11-Deployment/)
12. [Module 12 - Dọn dẹp Tài nguyên](5.12-Cleanup/)

Hãy bắt đầu hành trình chinh phục kiến trúc Serverless với **Module 1: Tổng quan Dự án & Kiến trúc**!