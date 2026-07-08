---
title : "Điều kiện tiên quyết"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### 1. Tài khoản AWS & Quyền hạn (IAM)
Để triển khai đầy đủ các dịch vụ trong kiến trúc PawVerse (VPC, EC2, RDS, CloudFront, WAF...), bạn cần sử dụng tài khoản AWS có quyền quản trị cao nhất (**AdministratorAccess**) hoặc tài khoản thực hành do chương trình FCAJ cung cấp.

![Quyền IAM Administrator](/images/5-Workshop/5.2-Prerequisite/iam.png)
*Hình 5.2.1: Đảm bảo tài khoản AWS có đủ quyền hạn để khởi tạo tài nguyên hạ tầng.*

#### 2. Khu vực triển khai (AWS Region)
Để giảm thiểu độ trễ mạng cho người dùng tại Việt Nam và đảm bảo các dịch vụ hoạt động đồng nhất, toàn bộ tài nguyên cốt lõi (VPC, EC2, RDS) sẽ được triển khai tại Region **Singapore (ap-southeast-1)**. Riêng CloudFront và WAF là dịch vụ toàn cầu (Global).

![Chọn Region Singapore](/images/5-Workshop/5.2-Prerequisite/region.png)
*Hình 5.2.2: Chọn Region ap-southeast-1 (Singapore) trên AWS Console.*

#### 3. Chuẩn bị Mã nguồn Ứng dụng
Hệ thống PawVerse đã được đóng gói sẵn để thuận tiện cho việc triển khai tự động:
+ **Backend:** Mã nguồn Spring Boot/Golang đã được build thành Docker Image và lưu trữ sẵn trên Docker Hub (`khoaledapoet/pawverse-backend:latest`).
+ **Frontend:** Giao diện ReactJS đã được build thành các tệp tĩnh (HTML, CSS, JS) sẵn sàng để tải lên Amazon S3.

#### 4. Công cụ hỗ trợ
+ Một trình duyệt web hiện đại (Chrome, Edge, Firefox).
+ (Tùy chọn) Giao diện dòng lệnh **AWS CLI** đã được cấu hình `aws configure` để hỗ trợ kiểm tra thông tin tự động nếu cần.
+ Công cụ **Apache Benchmark (ab)** hoặc **Postman** cài sẵn trên máy tính để phục vụ quá trình Test chịu tải (Load Testing) ở cuối bài Lab.