---
title: "Sự kiện 1"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Báo cáo thu hoạch: AWS Community Day 2026 (Tháng 5/2026)

![AWS Community Day](/images/4-EventParticipated/4.1-Event1/Event1.jpg)

## Địa điểm & Thời gian

- **Địa điểm:** Khách sạn New World, Quận 1, TP. Hồ Chí Minh
- **Thời gian:** Thứ Bảy, 23/05/2026
- **Vai trò:** Người tham dự (Attendee)

---

## Mục tiêu sự kiện

- Cập nhật các xu hướng công nghệ đám mây và trí tuệ nhân tạo tạo sinh (GenAI) mới nhất tại Việt Nam.
- Tìm hiểu các giải pháp tối ưu hóa hiệu năng hạ tầng biên (Edge Computing) và giảm độ trễ truy cập thông qua Amazon CloudFront.
- Nghiên cứu cơ chế vận hành của hệ thống đa tác nhân (Multi-Agent System) và ứng dụng trong các bài toán tài chính phức tạp.
- Khảo sát các kỹ thuật kiểm thử và giảm thiểu tính phi xác định (Non-Determinism) của mô hình ngôn ngữ lớn (LLM).
- Giao lưu, học hỏi và mở rộng mạng lưới quan hệ (networking) với các chuyên gia giải pháp (Solutions Architects) của AWS và cộng đồng.

---

## Diễn giả tiêu biểu

- **Mr. Dennis Traeger** - Head of Solutions Architecture, AWS Vietnam
- **Mr. Donnie Prakoso** - Principal Developer Advocate, AWS
- **Mr. Nguyen Phung** - AWS User Group Leader & Solutions Architect

---

## Key Highlights & Nội dung chi tiết

### 1. Xây dựng Bộ não thứ hai (Second Brain) & Context Engineering
Phiên trình bày tập trung vào cách thức chuyển dịch từ việc viết prompt đơn thuần sang xây dựng một kiến trúc quản lý tri thức toàn diện (Second Brain).
- AI chỉ thực sự mang lại giá trị khi được cung cấp đầy đủ ngữ cảnh nghiệp vụ.
- Thiết kế hệ thống quản lý context tự động giúp giảm tải token tiêu thụ và tăng độ chính xác của câu trả lời từ LLM.
- Tích hợp sâu vào các quy trình nghiệp vụ hàng ngày (workflows) để tạo ra giá trị kinh tế trực tiếp.

### 2. Xử lý tính phi xác định (Non-Determinism) của LLM trong kiểm thử
Mô hình ngôn ngữ lớn hoạt động theo cơ chế xác suất, dẫn đến việc kết quả đầu ra có thể thay đổi dù dùng chung một prompt.
- Ngay cả khi đặt tham số `temperature = 0`, LLM vẫn có tỷ lệ biến động kết quả do cách tối ưu hóa song song phần cứng trên GPU.
- Khuyến nghị áp dụng kiểm thử tự động trên tập dữ liệu lớn (Bulk Testing) kết hợp với các công cụ định hình cấu trúc dữ liệu đầu ra (Structured Outputs).
- Thiết lập cơ chế kiểm duyệt (Evaluation & Guardrails) để lọc và chuẩn hóa dữ liệu trước khi gửi đến người dùng cuối.

### 3. Kiến trúc Multi-Agent trong Thẩm định Tín dụng (Virtual Credit Committee)
Giải pháp ứng dụng các Agent chuyên biệt hóa để thay thế quy trình phê duyệt thủ công phức tạp trong ngành tài chính.
- Thay vì dùng một LLM duy nhất xử lý toàn bộ tác vụ, hệ thống chia nhỏ thành các Agent độc lập: Agent phân tích tài chính, Agent đánh giá rủi ro thị trường, Agent kiểm tra tính tuân thủ pháp lý.
- Các Agent tương tác và phản biện lẫn nhau (Agent-in-the-loop) để đưa ra quyết định đồng thuận tối ưu nhất.
- Hỗ trợ sự can thiệp của con người (Human-in-the-loop) ở những bước quyết định nhạy cảm.

### 4. Tối ưu hóa RTT và Bảo mật biên với Amazon CloudFront
Giải pháp tối ưu hóa hạ tầng phân phối nội dung toàn cầu để tăng tốc trải nghiệm người dùng và bảo mật hệ thống.
- Sử dụng Amazon CloudFront để giảm thiểu chỉ số RTT (Round Trip Time) thông qua các điểm hiện diện biên (Edge Locations).
- Tối ưu hóa chi phí truyền tải dữ liệu đi ra ngoài (Data Transfer Out - DTO).
- Tích hợp CloudFront Functions và Lambda@Edge để xử lý logic lập trình trực tiếp tại vùng biên mà không cần gọi về máy chủ gốc (Origin).

---

## Key Takeaways (Bài học cốt lõi)

### 1. Tư duy Kỹ thuật (Cloud Engineer Perspective)
- **Tối ưu hạ tầng biên:** Việc ứng dụng CloudFront không chỉ đơn thuần là phân phối nội dung tĩnh, mà là lớp chốt chặn bảo mật đầu tiên (DDoS protection, Web Application Firewall) và tối ưu hóa hiệu năng ứng dụng thông qua bộ nhớ đệm (caching).
- **Kiểm soát tính ổn định của AI:** Hiểu rõ giới hạn phần cứng và tính phi xác định của LLM giúp kỹ sư thiết kế hệ thống có tính phòng thủ cao hơn, sử dụng các cơ chế retry và validation chặt chẽ.

### 2. Tư duy Nghiệp vụ (BA/SA Perspective)
- **Giải quyết nỗi đau của doanh nghiệp:** Mô hình "Ủy ban tín dụng ảo" cho thấy GenAI có thể giải quyết các bài toán có tính quy chuẩn cao, loại bỏ sự chậm trễ và tính chủ quan trong khâu xét duyệt hồ sơ, trực tiếp đẩy nhanh tốc độ vận hành của doanh nghiệp.
- **Tối ưu chi phí và ROI:** Việc tối ưu hóa Context Engineering giúp doanh nghiệp tiết kiệm hàng ngàn USD chi phí gọi API từ các nhà cung cấp mô hình lớn, đồng thời tăng tốc độ phản hồi dịch vụ khách hàng.

---

## Ứng dụng vào Lộ trình thực tập FCAJ & Định hướng tương lai

- **Ứng dụng thực tế:** Tôi đã ứng dụng ngay kiến thức tối ưu hóa hạ tầng biên bằng Amazon CloudFront vào Module 8 (Website) của dự án Budget Tracker để lưu trữ và phân phối báo cáo tĩnh một cách nhanh chóng, bảo mật.
- **Định hướng thiết kế:** Thiết lập các cấu trúc Prompt rõ ràng, có ngữ cảnh và cấu trúc dữ liệu đầu ra nghiêm ngặt cho các tính năng hỗ trợ thông minh của dự án.

---

## Trải nghiệm sự kiện

Tham gia AWS Community Day 2026 giúp tôi mở rộng tầm mắt về quy mô ứng dụng công nghệ đám mây trong thế giới thực tế. Tôi nhận ra rằng khoảng cách giữa lý thuyết Lab và ứng dụng thực tiễn của doanh nghiệp được san lấp bằng sự chi tiết trong thiết kế bảo mật, quản lý chi phí tối ưu và tinh thần tự động hóa không ngừng nghỉ. Đây là động lực lớn để tôi hoàn thành xuất sắc dự án thực tập của mình.

---

## Một số hình ảnh tại sự kiện

![AWS Community Day 2026](/images/4-EventParticipated/4.1-Event1/Event1.jpg)
