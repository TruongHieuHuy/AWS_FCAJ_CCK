---
title: "5.1.1 Tổng quan & Mục tiêu dự án"
weight: 1
chapter: false
---


### 1. Executive Summary (Tóm tắt điều hành)

Bài hướng dẫn (Workshop) **Budget Tracker** cung cấp lộ trình chi tiết để triển khai một ứng dụng quản lý chi tiêu cá nhân sử dụng kiến trúc **AWS Serverless**. 

Dự án mô phỏng một bài toán thực tế: ứng dụng quản lý tài chính cá nhân với các tính năng như đăng nhập an toàn, ghi nhận giao dịch, tự động phân loại giao dịch bằng AI, và hệ thống thông báo đa kênh. Thông qua việc thực hành, chúng ta sẽ làm quen với việc thiết lập hạ tầng đám mây, phát triển Backend (API Gateway + Lambda), Frontend (React trên S3 + CloudFront), tự động hóa triển khai (CI/CD), và giám sát vận hành hệ thống.

Kết quả đầu ra của Workshop là khả năng tự tin xây dựng và vận hành một ứng dụng Serverless hoàn chỉnh. Bạn sẽ nắm vững nguyên lý tự động mở rộng (auto-scaling) và mô hình thanh toán theo nhu cầu (pay-as-you-go), giúp tối ưu hóa chi phí vận hành ở mức tối đa.

### 2. Learning Objectives (Mục tiêu học tập)

Sau khi hoàn thành khóa học này, bạn sẽ làm chủ các năng lực kỹ thuật cốt lõi sau:

- **Kiến trúc Cloud-Native:** Hiểu sâu về kiến trúc AWS Serverless và nguyên lý lập trình hướng sự kiện (Event-driven programming).
- **Backend Services:** 
  - Triển khai **Amazon API Gateway** để quản lý và định tuyến REST API.
  - Xây dựng **AWS Lambda** functions (FaaS) xử lý logic nghiệp vụ một cách độc lập.
- **Bảo mật & Phân quyền:** Sử dụng **Amazon Cognito** quản lý định danh người dùng và phát hành JWT (ID token, Access token).
- **Cơ sở dữ liệu:** Quản trị dữ liệu phi quan hệ bằng **Amazon DynamoDB**, áp dụng chiến lược Single-Table Design tối ưu hóa hiệu suất truy vấn.
- **Frontend Hosting:** Triển khai ứng dụng React tĩnh lên **Amazon S3** kết hợp mạng phân phối nội dung **Amazon CloudFront** (CDN).
- **DevOps & Tự động hóa:** Thiết lập luồng CI/CD với **GitHub Actions** và **AWS SAM** (Serverless Application Model).
- **Giám sát hệ thống:** Thu thập metrics, log và thiết lập cảnh báo chủ động qua **Amazon CloudWatch**.

### 3. Prerequisite Knowledge (Yêu cầu kiến thức đầu vào)

Để có thể theo sát và thực hành hiệu quả trong Workshop, bạn cần trang bị nền tảng sau:

- **Lập trình Web:** Cơ bản về HTML, CSS, JavaScript và framework React.
- **Lập trình Backend:** Có kinh nghiệm với một ngôn ngữ Backend (như C# .NET hoặc Node.js) và hiểu rõ về thiết kế REST API.
- **Công cụ:** Thành thạo quản lý mã nguồn với Git/GitHub.
- **Nền tảng Cloud:** Có hiểu biết sơ bộ về hệ sinh thái AWS và cách tương tác qua Command Line Interface (AWS CLI).
