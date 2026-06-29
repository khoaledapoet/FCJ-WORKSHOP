---
title: "Báo cáo Tuần 10"
date: 2026-06-27
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:

* Bắt đầu giai đoạn phát triển (Implementation) cho Capstone Project: **Serverless Feedback Pipeline**.
* Khởi tạo cơ sở dữ liệu NoSQL và thiết lập các cổng giao tiếp API cho ứng dụng.
* Phát triển logic xử lý cốt lõi và thiết lập hệ thống thông báo tự động.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Database Provisioning:**<br>- Khởi tạo bảng dữ liệu trên Amazon DynamoDB để lưu trữ thông tin phản hồi của người dùng.<br>- Cấu hình Partition Key và các Index cần thiết. | 22/06/2026 | 22/06/2026 | AWS Docs |
| **Ba** | **API Gateway Setup:**<br>- Thiết lập Amazon API Gateway làm điểm đầu vào (entry point) cho hệ thống.<br>- Cấu hình các phương thức HTTP (POST/GET) để nhận dữ liệu từ Frontend. | 23/06/2026 | 23/06/2026 | AWS Docs |
| **Tư** | **Lambda Function Development:**<br>- Phát triển mã nguồn Backend cho hàm AWS Lambda xử lý dữ liệu phản hồi.<br>- Tích hợp quyền IAM cho phép Lambda ghi dữ liệu vào DynamoDB. | 24/06/2026 | 24/06/2026 | AWS Docs |
| **Năm** | **Integration & Testing:**<br>- Kết nối API Gateway với hàm Lambda (Lambda Proxy Integration).<br>- Dùng Postman để kiểm thử luồng gửi dữ liệu: API Gateway -> Lambda -> DynamoDB. | 25/06/2026 | 25/06/2026 | AWS Docs |
| **Sáu** | **Notification System:**<br>- Cấu hình Amazon SNS (Simple Notification Service) để tạo chủ đề (Topic) gửi thông báo.<br>- Cập nhật code Lambda để trigger SNS gửi email mỗi khi có phản hồi mới. | 26/06/2026 | 26/06/2026 | AWS Docs |
| **Bảy** | **End-to-End Testing:**<br>- Kiểm thử toàn trình toàn bộ luồng dữ liệu của dự án.<br>- Ghi nhận các lỗi (bugs) phát sinh và tối ưu hóa mã nguồn. | 27/06/2026 | 27/06/2026 | AWS Docs |

### Kết quả đạt được:

* **Triển khai hạ tầng thực tế:** Đã hiện thực hóa được sơ đồ kiến trúc thành các tài nguyên thực tế trên AWS. Kết nối thành công luồng nhận dữ liệu từ API Gateway đẩy vào Lambda.
* **Xử lý Backend không máy chủ:** Viết thành công logic xử lý phản hồi và lưu trữ trơn tru vào cơ sở dữ liệu DynamoDB.
* **Hệ thống thông báo:** Hoàn thiện tính năng gửi thông báo thời gian thực qua email bằng SNS ngay khi hệ thống ghi nhận một phản hồi mới từ người dùng, đáp ứng đúng yêu cầu của bài toán đặt ra.