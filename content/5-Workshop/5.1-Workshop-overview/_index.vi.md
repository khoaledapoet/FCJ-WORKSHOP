---
title: "Tổng quan Workshop"
date: 2026-07-07
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Giới thiệu bài toán thực tế
Hệ thống cũ của nền tảng thương mại điện tử thú cưng **PawVerse** thường xuyên đối mặt với rủi ro sập mạng mỗi khi chạy chương trình khuyến mãi (Flash Sale) do hạ tầng cố định, không chịu được tải cao và lưu trữ thông tin nhạy cảm trực tiếp trong mã nguồn. 

Workshop này sẽ hướng dẫn bạn từng bước cách xây dựng một giải pháp điện toán đám mây phân tán, có khả năng tự động co giãn, bảo mật nhiều lớp và tối ưu chi phí trên AWS để giải quyết triệt để bài toán vận hành trên.

#### Sơ đồ Kiến trúc (Architecture Diagram)
Hệ thống PawVerse được thiết kế với kiến trúc đa tầng (Multi-tier Architecture) trên nhiều vùng sẵn sàng (Multi-AZ), đảm bảo tính sẵn sàng cao (High Availability) và phân tách rõ ràng luồng dữ liệu.

![Sơ đồ kiến trúc PawVerse](/images/5-Workshop/5.1-Workshop-overview/diagram.png)
*Hình 5.1.1: Sơ đồ luồng dữ liệu kiến trúc PawVerse trên AWS.*

#### Giải thích các thành phần lõi
* **Tầng Biên (Edge Layer):** AWS WAF và CloudFront bảo vệ chống tấn công DDoS, SQL Injection và tăng tốc phân phối giao diện tĩnh từ Amazon S3 (được khóa bảo mật bằng Origin Access Control - OAC).
* **Tầng Xử lý (Compute Layer):** Application Load Balancer (ALB) phân phối lưu lượng truy cập động xuống cụm máy chủ EC2. Auto Scaling Group tự động co giãn số lượng máy chủ dựa trên chỉ số tiêu thụ CPU thực tế.
* **Tầng Dữ liệu (Data Layer):** Amazon ElastiCache (Redis) làm bộ đệm nhằm giảm tải truy vấn trực tiếp xuống cơ sở dữ liệu quan hệ Amazon RDS (MySQL).
* **Tầng Bảo mật (Security Layer):** Máy chủ EC2 tự động truy xuất thông tin xác thực từ AWS Secrets Manager thông qua quyền hạn IAM Role, triệt tiêu hoàn toàn rủi ro lộ lọt cấu hình (Hard-coded Credentials).

#### Lộ trình thực hành chi tiết
Để hoàn thành kiến trúc trên, quy trình triển khai được chia thành các giai đoạn chuyên sâu, tương ứng với cấu trúc của dự án:
1. **Chuẩn bị môi trường:** Thiết lập điều kiện tiên quyết và mã nguồn.
2. **Hạ tầng Mạng (VPC):** Quy hoạch dải IP, thiết lập Private/Public Subnets và tối ưu hóa kết nối nội bộ.
3. **Lưu trữ & Dữ liệu:** Khởi tạo Amazon RDS, ElastiCache và thiết lập cơ chế bảo mật Secrets Manager.
4. **Tầng Tính toán (Compute):** Đóng gói kịch bản khởi động (User Data), thiết lập ALB và Auto Scaling Group.
5. **Phân phối & Tường lửa:** Đưa giao diện tĩnh lên S3, tích hợp CDN CloudFront và lớp phòng thủ AWS WAF.
6. **Giám sát hệ thống:** Triển khai CloudWatch, hệ thống kiểm toán CloudTrail và dịch vụ thông báo cảnh báo SNS.
7. **Nghiệm thu & Đúc kết:** Đánh giá hiệu năng thực tế (Live Demo) và phân tích các bài học kỹ thuật.
8. **Dọn dẹp hệ thống:** Phá hủy tài nguyên theo tiêu chuẩn tối ưu hóa chi phí (FinOps).