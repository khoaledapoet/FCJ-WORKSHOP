---
title : "Triển khai Cơ sở dữ liệu"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.4.2. </b> "
---

#### 1. Khởi tạo DB Subnet Group
Để cơ sở dữ liệu có tính dự phòng cao và nằm hoàn toàn trong vùng mạng cô lập, chúng ta cần nhóm các Private Subnet chuyên dụng lại với nhau.

1. Mở dịch vụ **Amazon RDS**, chọn **Subnet groups** từ menu bên trái ---> **Create DB subnet group**.
2. **Name:** `pawverse-db-subnet-group`.
3. **VPC:** Chọn đúng mạng `pawverse-vpc`.
4. **Availability Zones:** Chọn 2 vùng `ap-southeast-1a` và `ap-southeast-1b`.
5. **Subnets:** Tích chọn chính xác 2 dải CIDR thuộc phân vùng `Private DB Subnet` đã phân chia ở chương trước.

![Tạo RDS Subnet Group](/images/5-Workshop/5.4-Database-Security/rds-subnet.png)
*Hình 5.4.2.1: Nhóm các lớp mạng Private DB Subnet độc lập để cô lập tầng dữ liệu lõi.*

6. Bấm **Create**.

#### 2. Khởi tạo Amazon RDS MySQL
1. Di chuyển sang mục **Databases** --> **Create database**.
2. **Database creation method:** Chọn **Standard create**.
3. **Engine options:** Chọn **MySQL**.
4. **Templates:** Chọn **Free Tier** hoặc **Dev/Test** để tối ưu hóa chi phí vận hành Lab.
5. **Settings:**
   + **DB instance identifier:** `pawverse-mysql-db`.
   + **Master username:** `pawverse`.
   + **Master password:** `pawverse123Secret` *(Phải trùng khớp hoàn toàn với thông tin trong Secrets Manager)*.
6. **Instance configuration:** Chọn dòng burstable classes `db.t3.micro`.
7. **Connectivity:**
   + Chọn mạng `pawverse-vpc`.
   + **DB Subnet group:** Chọn `pawverse-db-subnet-group` vừa tạo.
   + **Public access:** Tích chọn **No** *(Ngăn chặn tuyệt đối mọi kết nối từ bên ngoài Internet)*.
8. Cuộn xuống cuối và nhấn **Create database**. Tiến trình khởi tạo sẽ mất từ 3 đến 5 phút.