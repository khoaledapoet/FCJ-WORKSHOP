---
title : "Tổng quan Workshop"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Giới thiệu bài toán thực tế
Hệ thống cũ của nền tảng thương mại điện tử thú cưng **PawVerse** thường xuyên đối mặt với rủi ro sập mạng mỗi khi chạy chương trình khuyến mãi (Flash Sale) do hạ tầng cố định, không chịu được tải cao và lưu trữ thông tin nhạy cảm trực tiếp trong mã nguồn. 

Workshop này sẽ hướng dẫn bạn từng bước (step-by-step) cách xây dựng một giải pháp điện toán đám mây phân tán, có khả năng tự động co giãn, bảo mật nhiều lớp và tối ưu chi phí trên AWS để giải quyết triệt để bài toán trên.

#### Sơ đồ Kiến trúc (Architecture Diagram)
Hệ thống PawVerse được thiết kế với kiến trúc 3-Tier (3 Tầng) trên nhiều vùng sẵn sàng (Multi-AZ), đảm bảo tính sẵn sàng cao (High Availability) và phân tách rõ ràng luồng dữ liệu.

![Sơ đồ kiến trúc PawVerse](/images/5-Workshop/5.1-Workshop-overview/diagram.png)
*Hình 5.1: Sơ đồ luồng dữ liệu kiến trúc PawVerse trên AWS.*

#### Giải thích các thành phần lõi
+ **Tầng Biên (Edge Layer):** AWS WAF và CloudFront bảo vệ chống tấn công DDoS, SQL Injection và tăng tốc phân phối giao diện tĩnh từ Amazon S3 (được khóa bảo mật bằng OAC).
+ **Tầng Xử lý (Compute Layer):** Application Load Balancer (ALB) phân phối tải động xuống cụm EC2. Auto Scaling Group tự động co giãn số lượng máy chủ dựa trên chỉ số CPU thực tế.
+ **Tầng Dữ liệu (Data Layer):** Amazon ElastiCache (Redis) làm bộ đệm giảm tải 80% truy vấn trực tiếp xuống cơ sở dữ liệu quan hệ Amazon RDS (MySQL).
+ **Tầng Bảo mật (Security Layer):** EC2 tự động lấy mật khẩu từ AWS Secrets Manager thông qua quyền IAM Role mà không cần hard-code vào source code.

#### Lộ trình thực hành Step-by-Step
Để hoàn thành hạ tầng này, chúng ta sẽ đi qua 5 bước chính trong Workshop:
1. **Mạng lưới (VPC & Network):** Thiết lập Private/Public Subnets, NAT Gateway và VPC Endpoints.
2. **Dữ liệu & Bảo mật (Database & Security):** Khởi tạo RDS, ElastiCache và két sắt Secrets Manager.
3. **Xử lý tính toán (Compute & ALB):** Cấu hình EC2 Launch Template, Auto Scaling và Load Balancer.
4. **Phân phối nội dung (Edge Layer):** Triển khai giao diện lên S3, kết nối CloudFront và WAF.
5. **Dọn dẹp (Clean-up):** Tiêu hủy tài nguyên an toàn để tối ưu chi phí sau khi Lab kết thúc.