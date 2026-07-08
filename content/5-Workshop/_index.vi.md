---
title: "Workshop"
date: 2026-07-07
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Thực hành Triển khai Hạ tầng Đám mây PawVerse

#### Tổng quan (Overview)

Trong môi trường thương mại điện tử hiện đại, việc duy trì một hệ thống ổn định, chịu tải tốt và bảo vệ nghiêm ngặt dữ liệu người dùng là yếu tố sống còn. 

Trong bài Lab này, bạn sẽ tự tay thực hành thiết kế, cấu hình và triển khai toàn bộ hạ tầng đám mây AWS cho nền tảng **PawVerse**. Hệ thống được xây dựng theo kiến trúc đa tầng (Multi-tier) phân tán, tích hợp mạng phân phối nội dung toàn cầu, hệ thống tường lửa, cụm bộ đệm lưu trữ tĩnh và cơ chế tự động co giãn tài nguyên linh hoạt.

Đặc biệt, bài thực hành nhấn mạnh vào tư duy vận hành mạng (Cloud Operations) và bảo mật cốt lõi thông qua việc áp dụng triệt để nguyên tắc Đặc quyền tối thiểu (Least Privilege), ẩn giấu hoàn toàn tài nguyên vào mạng nội bộ (Private Subnets) và tự động hóa mã hóa thông tin mật.

#### Các Dịch vụ Trọng tâm (Core Services Utilized)
+ **Networking & Security:** Amazon VPC, NAT/IGW Gateway, S3 Gateway Endpoint, AWS IAM, AWS KMS, AWS Secrets Manager.
+ **Compute & Scaling:** Amazon EC2, EC2 Launch Templates, Auto Scaling Group, Application Load Balancer (ALB).
+ **Storage & Database:** Amazon RDS (MySQL), Amazon ElastiCache (Redis), Amazon S3.
+ **Edge Delivery & Protection:** Amazon CloudFront, AWS WAF.
+ **Observability & Management:** Amazon CloudWatch, AWS CloudTrail, Amazon SNS.

#### Lộ trình Thực hành (Workshop Content)

1. **[Tổng quan Workshop](5.1-Workshop-overview/):** Tìm hiểu bài toán thực tế và phân tích Sơ đồ kiến trúc giải pháp.
2. **[Điều kiện tiên quyết](5.2-Prerequiste/):** Chuẩn bị môi trường AWS, IAM Role, khu vực triển khai và mã nguồn.
3. **[Hạ tầng VPC & Mạng](5.3-vpc-network/):** Xây dựng bộ khung mạng nội bộ, định tuyến Public/Private và tối ưu hóa băng thông bằng Gateway Endpoint.
4. **[Lưu trữ & Bảo mật Credentials](5.4-Database-Security/):** Triển khai két sắt Secrets Manager, Amazon RDS, ElastiCache và kiểm toán tính cô lập mạng (DNS Simulation).
5. **[Máy chủ & Cân bằng tải](5.5-Compute-ALB/):** Viết kịch bản tự động hóa khởi động (User Data), thiết lập ALB và cấu hình Auto Scaling Group.
6. **[Tầng Biên (CloudFront & WAF)](5.6-EdgeLayer/):** Đưa giao diện Frontend lên S3, phân phối CDN toàn cầu và thiết lập tường lửa web.
7. **[Giám sát & Cảnh báo](5.7-Monitoring/):** Cấu hình đặc vụ CloudWatch Agent thu thập logs/metrics, thiết lập chuông cảnh báo SNS và truy vết kiểm toán hệ thống bằng CloudTrail.
8. **[Dọn dẹp tài nguyên](5.8-Cleanup/):** Phá hủy hạ tầng an toàn theo đúng trình tự FinOps để triệt tiêu chi phí phát sinh ngoài ý muốn.