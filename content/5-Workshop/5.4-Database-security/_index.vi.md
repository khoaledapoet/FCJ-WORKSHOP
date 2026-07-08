---
title : "Lưu trữ & Bảo mật Credentials"
date : 2026-07-07
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Tầng Dữ liệu và Bảo mật Lõi (Data & Security Layer)

Dữ liệu là tài sản quý giá nhất của mọi nền tảng e-commerce. Việc cấu hình sai tầng dữ liệu, để lộ máy chủ ra Internet, hoặc lưu trữ thông tin kết nối (Credentials) trực tiếp trong mã nguồn là những rủi ro bảo mật chí mạng mà một kỹ sư Cloud Operations phải tuyệt đối phòng tránh.

Trong chương này, chúng ta sẽ thiết lập "trái tim" của hệ thống PawVerse. Mục tiêu cốt lõi là xây dựng một tầng lưu trữ **vô hình trước Internet**, **tối ưu tốc độ truy xuất** và **bảo mật thông tin bằng mã hóa phân quyền**.

Chúng ta sẽ lần lượt thực hiện 5 bước sau:
1. **Khởi tạo két sắt bảo mật (AWS Secrets Manager):** Loại bỏ hoàn toàn việc "Hard-code" mật khẩu vào mã nguồn.
2. **Triển khai Cơ sở dữ liệu (Amazon RDS):** Khởi tạo cụm cơ sở dữ liệu quan hệ MySQL đặt sâu trong Private Subnet.
3. **Khởi tạo Bộ đệm (Amazon ElastiCache):** Tích hợp Redis để giảm thiểu lên tới 80% truy vấn trực tiếp xuống Database, tăng khả năng chịu tải.
4. **Mô phỏng tính cô lập (DNS Simulation):** Kiểm chứng bằng dòng lệnh để đảm bảo AWS Route 53 chỉ phân giải Private IP cho cơ sở dữ liệu.
5. **Kiểm soát Truy cập (IAM & KMS):** Gắn quyền đặc quyền tối thiểu cho EC2 và đảm bảo dữ liệu được mã hóa (Encryption at rest) bằng khóa KMS mặc định.