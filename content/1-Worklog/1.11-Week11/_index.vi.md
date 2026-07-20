---
title: "Nhật ký công việc Tuần 11"
date: 2026-05-04
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

* Vận dụng kiến thức IaC từ bài Lab 10: Soạn thảo `template.yaml` (AWS SAM) đóng gói toàn bộ hạ tầng dự án dưới dạng IaC.
* Thiết lập CI/CD Pipeline tự động hóa build, test và deploy qua GitHub Actions với bảo mật OIDC (OpenID Connect).
* Hoàn thiện tài liệu Workshop Module 11 (Deployment Automation).

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 - Thứ 4 | Vận dụng kiến thức IaC CloudFormation từ bài Lab 10: Soạn thảo `template.yaml` (AWS SAM): định nghĩa toàn bộ hạ tầng dưới dạng IaC — `AWS::Serverless::Function` (Lambda), `AWS::DynamoDB::Table` (GSI definitions), `AWS::ApiGateway::RestApi`, `AWS::Cognito::UserPool`, `AWS::SQS::Queue`. Cấu hình SAM Globals. | 13/07/2026 | 15/07/2026 | [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| Thứ 5 - Thứ 6 | Thiết lập GitHub Actions Workflow (`.github/workflows/deploy.yml`): pipeline gồm các stages **Lint & Test**, **Build** (ReadyToRun), **SAM Package**, **SAM Deploy**. Cấu hình AWS credentials sử dụng **OIDC (OpenID Connect)** — không lưu static access keys trong GitHub Secrets. | 16/07/2026 | 17/07/2026 | [GitHub Actions for AWS](https://docs.github.com/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-amazon-web-services) |
| Thứ 7 - CN | Kiểm thử pipeline end-to-end: push code → trigger Actions → verify deploy thành công. Hoàn thiện tài liệu Workshop **Module 11** (Deployment Automation): SAM template walkthrough, GitHub Actions YAML, OIDC setup. | 18/07/2026 | 19/07/2026 | [AWS CloudFormation User Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html) |

### Kết quả đạt được tuần 11:

* `template.yaml` hoàn chỉnh: toàn bộ hạ tầng Budget Tracker định nghĩa dưới dạng IaC, tái tạo trong vài phút.
* GitHub Actions Pipeline hoạt động: tự động hóa Test → Build → Deploy khi push lên `main`.
* OIDC authentication thay thế static access keys — zero long-lived credentials trong CI/CD pipeline.
* Tài liệu Workshop Module 11 xuất bản đầy đủ.

### Góc nhìn Đối ngẫu (Dual-Perspective Reflection):

#### Kỹ thuật (Cloud Engineer Perspective)
AWS SAM là abstraction layer nâng cao từ kinh nghiệm học CloudFormation ở bài Lab 10: `AWS::Serverless::Function` tự động tạo IAM Execution Role, CloudWatch Log Group và API Gateway integration. Việc sử dụng OIDC thay cho static access keys giúp xin temporary credentials từ AWS STS qua JWT token — tự động expire sau mỗi job job, bảo mật tối đa.

#### Hệ thống & Phối hợp (BA/SA Perspective)
IaC + CI/CD Pipeline đại diện cho văn hóa **DevOps**: loại bỏ hoàn toàn thủ công deployment (human error). Giảm Time-to-Market từ 30 phút deploy tay xuống <5 phút tự động với zero downtime.

### Kế hoạch tuần tiếp theo:
Thực hiện User Acceptance Testing (UAT), kiểm toán chi phí AWS Billing, Resource Cleanup (Module 12) và chuẩn bị Slide thuyết trình bảo vệ dự án.
