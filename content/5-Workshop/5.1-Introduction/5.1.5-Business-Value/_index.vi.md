---
title: "5.1.5 Đánh giá Nghiệp vụ & Tầm nhìn"
weight: 5
chapter: false
---


### 1. Tối ưu hóa Chi phí (Cost Optimization) - Góc nhìn BA/SA

Sức mạnh lớn nhất của Serverless là biến chi phí cố định (CapEx) thành chi phí hoạt động biến đổi (OpEx). Dưới góc độ quản trị doanh nghiệp, đây là một mô hình tài chính siêu việt:

- **Pay-as-you-go (Scale-to-zero):** Bạn không phải trả tiền cho một máy chủ EC2 chạy rỗi cả đêm. Khi hệ thống không có user truy cập, chi phí máy tính gần như bằng 0.
- **Tối ưu theo Nhu cầu:** DynamoDB On-Demand tự động co giãn sức chứa dữ liệu. Hệ thống CloudFront CDN cache nội dung Frontend giúp giảm thiểu số lượt request phải đánh vào origin server, tiết kiệm hàng loạt chi phí truyền tải dữ liệu (Data Transfer Out).
- **Tối ưu Vận hành:** Không cần tuyển một đội ngũ System Admin chuyên biệt để vá lỗi hệ điều hành hay bảo trì máy chủ vật lý. Đội ngũ có thể dồn toàn lực vào phát triển tính năng sinh lời.

### 2. Một số hạn chế hiện tại (Limitations)

Dù ưu việt, kiến trúc hiện tại vẫn đang đánh đổi một số yếu tố để đổi lấy tốc độ phát triển nhanh:

- **Phụ thuộc vào một Vùng (Single Region):** Hệ thống chỉ đang chạy ở `ap-southeast-1`. Khả năng chống chịu thảm họa toàn diện (DR - Disaster Recovery) ở cấp độ khu vực chưa được thiết lập.
- **Hạn chế của Compute Layer:** AWS Lambda có giới hạn timeout tối đa 15 phút. Nếu phát sinh các tác vụ xử lý dữ liệu hạng nặng kéo dài, kiến trúc bắt buộc phải chuyển dịch sang AWS Fargate hoặc Amazon EKS.
- **Nguy cơ tăng chi phí đột biến:** Dù tối ưu khi lượng truy cập thấp hoặc biến động, nếu ứng dụng đạt quy mô hàng chục triệu request liên tục mỗi ngày, chi phí trả cho API Gateway và Lambda có thể cao hơn so với việc thuê máy chủ vật lý chuyên dụng.

### 3. Tầm nhìn Tương lai (Future Work) - Góc nhìn BA/SA

Để nâng tầm Budget Tracker từ một ứng dụng cá nhân thành một giải pháp SaaS tài chính chuyên nghiệp, lộ trình chiến lược có thể bao gồm:

- **Mô hình kinh doanh B2B & Freemium:** Mở rộng API cho các ứng dụng ngân hàng/Fintech khác nhúng nền tảng quản lý tài chính vào hệ sinh thái của họ.
- **Cố vấn Tài chính AI Tích hợp:** Ứng dụng sâu mô hình AI tạo sinh (Google Gemini/Amazon Bedrock) phân tích thói quen dòng tiền của người dùng để tư vấn kế hoạch tiết kiệm tự động thay vì chỉ phân loại giao dịch đơn thuần.
- **Kiến trúc Đa khu vực (Multi-Region):** Triển khai DynamoDB Global Tables và CloudFront Route 53 Geolocation để tạo ra trải nghiệm người dùng xuất sắc tại nhiều quốc gia, hướng tới SLA 99.99%.
- **Hiện đại hóa Dữ liệu (Data Lake):** Xây dựng kho dữ liệu tổng hợp trên Amazon S3 và dùng Amazon QuickSight để cung cấp biểu đồ báo cáo tài chính thông minh (Data-driven Insights) theo thời gian thực cho Ban giám đốc.

### 4. Kết luận

Dự án Workshop Budget Tracker không đơn thuần là một bài tập kỹ thuật cấu hình AWS. Nó là một bản thiết kế chuẩn mực thể hiện sự giao thoa giữa **Kỹ nghệ Phần mềm Đám mây (Cloud Engineering)** và **Tư duy Kiến trúc Hệ thống (Solution Architecture)**.

Người thực hành sẽ nắm vững triết lý thiết kế ứng dụng có khả năng co giãn linh hoạt, tính bảo mật cao và quan trọng nhất là giải quyết bài toán nghiệp vụ một cách triệt để với ngân sách tối ưu nhất.
