---
title : "Hạ tầng VPC & Mạng"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Tổng quan Mạng lưới PawVerse
Để đảm bảo an ninh tối đa cho dữ liệu người dùng và mã nguồn ứng dụng, hệ thống PawVerse sẽ được triển khai hoàn toàn bên trong một mạng riêng ảo (VPC). 

Mạng lưới này sẽ được chia thành nhiều lớp (Subnets) và kiểm soát luồng giao thông (Traffic) ra/vào chặt chẽ thông qua các cổng mạng (Gateway) và bảng định tuyến (Route Tables). 

Trong phần này, chúng ta sẽ lần lượt thực hiện 3 bước cốt lõi:
1. **Khởi tạo VPC, phân chia Subnet và Internet Gateway.**
2. **Thiết lập NAT Gateway và S3 Endpoint.**
3. **Cấu hình định tuyến và gắn kết (Subnet Associations).**