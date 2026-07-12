---
title: "Nhật ký công việc Tuần 11"
date: 2026-05-04
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Triển khai Infrastructure as Code (IaC) toàn bộ hệ thống Budget Tracker bằng AWS SAM Template.
* Thiết lập CI/CD Pipeline tự động hóa build, test và deploy qua GitHub Actions.
* Hoàn thiện tài liệu Workshop Module 11 (Deployment Automation).

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Soạn thảo `template.yaml` (AWS SAM): định nghĩa toàn bộ tài nguyên dưới dạng IaC — `AWS::Serverless::Function` (Lambda với memory, timeout, environment variables), `AWS::DynamoDB::Table` (với GSI definitions), `AWS::ApiGateway::RestApi`, `AWS::Cognito::UserPool`, `AWS::SQS::Queue`. Cấu hình SAM Globals để tránh lặp lại cấu hình chung giữa các Lambda. | 13/07/2026 | 15/07/2026 | [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| Thứ 5 - Thứ 6 | Thiết lập GitHub Actions Workflow (`.github/workflows/deploy.yml`): pipeline gồm các stages: **Lint & Test** (chạy xUnit tests, fail-fast nếu test fail), **Build** (dotnet publish với ReadyToRun), **SAM Package** (upload artifacts lên S3), **SAM Deploy** (deploy CloudFormation stack). Cấu hình AWS credentials sử dụng **OIDC (OpenID Connect)** — không lưu long-term access keys trong GitHub Secrets. | 16/07/2026 | 17/07/2026 | [GitHub Actions for AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services) |
| Thứ 7 - CN | Kiểm thử pipeline end-to-end: push code → trigger Actions → verify deploy thành công. Hoàn thiện tài liệu Workshop **Module 11** (Deployment Automation): SAM template walkthrough, GitHub Actions YAML explanation, OIDC setup guide. | 18/07/2026 | 19/07/2026 | [AWS CloudFormation User Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |

### Kết quả đạt được tuần 11:

* `template.yaml` hoàn chỉnh: toàn bộ hạ tầng Budget Tracker được định nghĩa dưới dạng IaC, có thể tái tạo trong vài phút.
* GitHub Actions Pipeline hoạt động: mỗi push lên `main` tự động trigger test → build → deploy.
* OIDC authentication thay thế static access keys — zero long-lived credentials trong CI/CD pipeline.
* Tài liệu Workshop Module 11 hoàn chỉnh.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
AWS SAM là abstraction layer trên CloudFormation: `AWS::Serverless::Function` tự động tạo kèm IAM Execution Role, CloudWatch Log Group và tích hợp với API Gateway — giảm đáng kể boilerplate YAML. Điểm quan trọng về OIDC: thay vì lưu `AWS_ACCESS_KEY_ID` và `AWS_SECRET_ACCESS_KEY` dưới dạng GitHub Secrets (long-lived, nếu leak sẽ cực kỳ nguy hiểm), OIDC cho phép GitHub Actions xin temporary credentials từ AWS STS bằng JWT token — credentials tự expire sau mỗi job, không có thông tin nhạy cảm nào được lưu trữ lâu dài.

#### Hệ thống & Phối hợp (BA/SA Perspective)
IaC + CI/CD Pipeline là nền tảng của **DevOps culture**: mọi thay đổi hạ tầng phải đi qua Git (Infrastructure as Code), được review (Pull Request), được kiểm thử tự động (CI), và được deploy tự động (CD) — loại bỏ hoàn toàn manual deployment errors (human error là nguyên nhân hàng đầu của production outages). Về mặt kinh doanh, pipeline giảm **Time-to-Market** cho mỗi feature mới: thay vì deploy thủ công mất 30 phút, automated pipeline hoàn thành trong <5 phút với zero downtime.

### Kế hoạch tuần tiếp theo:
Thực hiện User Acceptance Testing (UAT), kiểm toán chi phí AWS Billing và bàn giao dự án hoàn chỉnh.
