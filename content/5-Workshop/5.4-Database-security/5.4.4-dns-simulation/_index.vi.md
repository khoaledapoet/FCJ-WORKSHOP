---
title : "Mô phỏng phân giải DNS"
date : 2026-07-07
weight : 4
chapter : false
pre : " <b> 5.4.4. </b> "
---

#### Xác thực tính Cô lập Hạ tầng mạng (Network Isolation Validation)
Để chứng minh cơ sở dữ liệu của PawVerse hoàn toàn vô hình trước môi trường Internet công cộng, chúng ta sẽ đóng vai trò là một kẻ tấn công, thực hiện bài kiểm tra phân giải tên miền (DNS Resolution Audit) từ bên ngoài hệ thống.

1. Lấy Endpoint của Amazon RDS MySQL vừa tạo (VD: `pawverse-mysql.xxx.ap-southeast-1.rds.amazonaws.com`).
2. Mở Terminal trên thiết bị cá nhân (Sử dụng đường truyền Internet bên ngoài VPC) và thực thi lệnh `nslookup`:
   ```bash
   nslookup pawverse-mysql.xxx.ap-southeast-1.rds.amazonaws.com
   ```

![Mô phỏng DNS nslookup](/images/5-Workshop/5.4-Database-Security/dns-nslookup.png)
*Hình 5.4.4.1: Hệ thống DNS từ chối cung cấp địa chỉ IP (No A/AAAA records) cho các truy vấn từ Internet công cộng.*

3. **Phân tích kết quả:** Thay vì trả về một địa chỉ IP như các trang web thông thường, AWS Route 53 đã chặn đứng truy vấn và trả về thông báo lỗi `No internal type for both IPv4 and IPv6 Addresses`.
4. **Kết luận bảo mật:** Cơ chế cô lập mạng đã hoạt động hoàn hảo 100%. AWS nhận diện được luồng truy vấn đến từ bên ngoài VPC nên đã **từ chối giải mã IP** của Database. Một kẻ tấn công dù có biết chính xác Endpoint Name cũng không thể lấy được địa chỉ IP để định tuyến gói tin (Routing), triệt tiêu hoàn toàn các vectơ tấn công trực diện.