---
title: "Báo cáo Tuần 12"
date: 2026-07-08
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:
* Hoàn thiện khả năng quan sát (Observability) của hệ thống PawVerse.
* Thiết lập báo động và truy vết tự động.
* Thực hiện quy trình quản lý chi phí tài nguyên (FinOps Cleanup) và hoàn thiện báo cáo.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Giám sát Chỉ số (Metrics):**<br>- Truy cập CloudWatch, xây dựng Dashboard tập trung.<br>- Lấy dữ liệu CPU chuyên sâu từ CWAgent, Request Count từ ALB và DB Connections từ RDS. | 06/07/2026 | 06/07/2026 |  |
| **Ba** | **Truy xuất Log Tập trung:**<br>- Kiểm tra Log Groups, truy xuất log ứng dụng Spring Boot và Docker từ xa mà không cần SSH vào từng con máy ảo EC2. | 07/07/2026 | 07/07/2026 |  |
| **Tư** | **Cảnh báo Hệ thống (Alarms):**<br>- Thiết lập Alarm cảnh báo khi CPU EC2 vượt ngưỡng 80%.<br>- Cấu hình Amazon SNS tự động gửi Email báo động khẩn cấp cho Quản trị viên. | 08/07/2026 | 08/07/2026 |  |
| **Năm** | **Kiểm toán & Test Sự cố:**<br>- Kích hoạt CloudTrail ghi nhận nhật ký API (Audit Logs).<br>- Dùng AWS CloudShell (CLI) để ép Alarm báo động đỏ và xác thực luồng gửi Email SNS hoạt động hoàn hảo. | 09/07/2026 | 09/07/2026 | |
| **Sáu** | **Báo cáo:**<br>- Đóng gói mã nguồn tài liệu Hugo và nộp báo cáo thực tập tổng kết. | 10/07/2026 | 10/07/2026 ||

### Kết quả đạt được:
* **Hệ thống tự động báo cáo:** Bảng điều khiển CloudWatch cung cấp cái nhìn toàn cảnh về sức khỏe của hạ tầng. Chuỗi Incident Response (Phản hồi sự cố) hoạt động trơn tru qua SNS.
* **Minh bạch hóa Vận hành:** Mọi thao tác đều được CloudTrail ghi lại, đáp ứng các tiêu chuẩn khắt khe về Security và Compliance.
* **Kiểm soát chi phí:** Nắm vững và thực hành thành thạo kỹ năng dọn dẹp tài nguyên (Clean up), đảm bảo không phát sinh chi phí ngoài ý muốn sau khi kết thúc quá trình triển khai dự án.