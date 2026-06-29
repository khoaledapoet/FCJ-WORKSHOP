---
title: "Báo cáo Tuần 8"
date: 2026-06-13
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu Tuần 8:

* Nâng cấp hạ tầng triển khai Microservices với các giải pháp Container nâng cao: Amazon Lightsail Containers, AWS Fargate và Amazon EKS (Kubernetes).
* Tự động hóa quá trình phát hành ứng dụng trên nền tảng Kubernetes thông qua CI/CD với CodePipeline và GitHub.
* Xây dựng kho lưu trữ dữ liệu tập trung (Data Lake), trực quan hóa dữ liệu (QuickSight) và làm quen với công nghệ Machine Learning (SageMaker).

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Containers & Fargate:**<br>- Bắt đầu làm quen với Amazon Lightsail Containers.<br>- Chuyển đổi Monolith sang Microservices bằng Docker và triển khai không máy chủ với AWS Fargate. | 08/06/2026 | 08/06/2026 | Tài liệu Lab FCAJ |
| **Ba** | **Kubernetes Operations:**<br>- Khởi tạo và làm quen với hệ thống điều phối container cấp độ doanh nghiệp (Get started with Amazon EKS). | 09/06/2026 | 09/06/2026 | Tài liệu Lab FCAJ |
| **Tư** | **CI/CD Automation:**<br>- Xây dựng luồng CI/CD cơ bản với AWS CodePipeline.<br>- Thiết lập CI/CD tự động trên cụm EKS kết nối mã nguồn từ GitHub. | 10/06/2026 | 10/06/2026 | Tài liệu Lab FCAJ |
| **Năm** | **Data Lake Architecture:**<br>- Nghiên cứu kiến trúc tổng thể xây dựng Data lake trên AWS.<br>- Thực hành đưa dữ liệu thực tế vào Data Lake (Build Datalake with your data). | 11/06/2026 | 11/06/2026 | Tài liệu Lab FCAJ |
| **Sáu** | **Data Analytics & BI:**<br>- Khám phá hệ sinh thái các dịch vụ Phân tích dữ liệu (Data Analytics) trên AWS.<br>- Trực quan hóa dữ liệu kinh doanh với Amazon QuickSight. | 12/06/2026 | 12/06/2026 | Tài liệu Lab FCAJ |
| **Bảy** | **Machine Learning:**<br>- Làm quen với nền tảng xây dựng, huấn luyện và triển khai mô hình học máy Amazon SageMaker. | 13/06/2026 | 13/06/2026 | Tài liệu Lab FCAJ |

### Kết quả đạt được:

* **Quản trị Container chuyên sâu:** Vận dụng linh hoạt các dịch vụ điều phối từ đơn giản (Lightsail) đến phức tạp (EKS, Fargate). Khả năng thiết lập cụm Kubernetes chuẩn bảo mật, kết nối trơn tru với hạ tầng mạng.
* **Tự động hóa trên Kubernetes:** Tích hợp thành công luồng CI/CD kết nối thẳng từ GitHub đến Amazon EKS, giúp mã nguồn tự động đóng gói thành image và cập nhật lên cụm container không thời gian chết (zero downtime).
* **Quản trị dữ liệu & Phân tích:** Nắm vững quy trình đưa luồng dữ liệu thô vào Data Lake, xử lý qua các dịch vụ Analytics và xuất ra các biểu đồ (Dashboard) báo cáo kinh doanh trực quan thông qua Amazon QuickSight.
* **AI/Machine Learning:** Tiếp cận nền tảng Amazon SageMaker, hiểu được vòng đời (Lifecycle) của một dự án học máy trên môi trường đám mây từ khâu chuẩn bị dữ liệu đến khi deploy model.