---
title: "Báo cáo Tuần 7"
date: 2026-06-06
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:

* Xây dựng kiến trúc Serverless hoàn chỉnh, bao gồm giao tiếp Frontend - Backend qua API Gateway và xử lý dữ liệu với Lambda, S3, DynamoDB.
* Triển khai, bảo mật và vận hành ứng dụng bằng các công cụ hiện đại (AWS SAM, Cognito, SSL).
* Tối ưu hóa hiệu suất và tự động hóa quy trình với hệ thống thông báo bất đồng bộ (SQS/SNS), CI/CD (CodePipeline) và giám sát (X-Ray, CloudWatch).

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Serverless Core & API:**<br>- Viết hàm Lambda tương tác với S3 và cơ sở dữ liệu DynamoDB.<br>- Xây dựng Frontend và gọi API thông qua Amazon API Gateway. | 01/06/2026 | 01/06/2026 | Tài liệu Lab FCAJ |
| **Ba** | **Infrastructure as Code (IaC):**<br>- Đóng gói và triển khai ứng dụng Serverless bằng framework AWS SAM (Serverless Application Model). | 02/06/2026 | 02/06/2026 | Tài liệu Lab FCAJ |
| **Tư** | **Security & Authentication:**<br>- Thiết lập hệ thống xác thực người dùng an toàn với Amazon Cognito.<br>- Cấu hình chứng chỉ SSL cho ứng dụng Serverless. | 03/06/2026 | 03/06/2026 | Tài liệu Lab FCAJ |
| **Năm** | **Asynchronous Processing:**<br>- Xây dựng luồng xử lý đơn hàng bất đồng bộ bằng dịch vụ hàng đợi (SQS) và thông báo (SNS). | 04/06/2026 | 04/06/2026 | Tài liệu Lab FCAJ |
| **Sáu** | **CI/CD & Monitoring:**<br>- Thiết lập quy trình phát hành liên tục (CI/CD) với AWS CodePipeline.<br>- Giám sát và truy vết hiệu suất ứng dụng bằng CloudWatch và AWS X-Ray. | 05/06/2026 | 05/06/2026 | Tài liệu Lab FCAJ |
| **Bảy** | **Advanced Data Query:**<br>- Tìm hiểu và giới thiệu về dịch vụ GraphQL được quản lý toàn diện - AWS AppSync. | 06/06/2026 | 06/06/2026 | Tài liệu Lab FCAJ |

### Kết quả đạt được:

* **Phát triển Serverless toàn diện:** Làm chủ được việc kết nối Frontend với Backend không máy chủ. Xử lý thành thạo các luồng dữ liệu giữa API Gateway, hàm Lambda, lưu trữ tĩnh S3 và cơ sở dữ liệu NoSQL DynamoDB.
* **Bảo mật & Triển khai:** Biết cách sử dụng AWS SAM để quản lý hạ tầng bằng code. Bảo vệ hệ thống bằng cách cài đặt chứng chỉ SSL và tích hợp Amazon Cognito để quản lý định danh người dùng.
* **Vận hành & Tối ưu hệ thống:** Giải quyết được bài toán thắt nút cổ chai trong kiến trúc bằng cách tách rời các dịch vụ qua SQS và SNS. Tự động hóa quá trình deploy với CodePipeline và có khả năng phân tích, gỡ lỗi hệ thống sâu nhờ AWS X-Ray và CloudWatch. Nắm bắt được nền tảng của AWS AppSync cho các ứng dụng thời gian thực.