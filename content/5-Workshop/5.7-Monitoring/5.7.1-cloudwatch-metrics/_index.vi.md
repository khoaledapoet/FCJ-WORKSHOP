---
title : "Theo dõi Chỉ số "
date : 2026-07-08
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

#### Trực quan hóa Dữ liệu Hệ thống
Metrics cung cấp cái nhìn tổng quan về mức độ tiêu thụ tài nguyên theo thời gian thực. Chúng ta sẽ gom các chỉ số quan trọng nhất của hệ thống vào chung một Dashboard để dễ dàng kiểm soát.

1. Truy cập dịch vụ **Amazon CloudWatch**, chọn **Dashboards** ---> **Create dashboard**.
2. Đặt tên là `PawVerse-Production-Dashboard`.
3. Nhấn **Add widget** ---> Chọn **Line** chart ---> **Metrics**.
4. **Theo dõi CPU EC2 chuyên sâu (Qua CWAgent):**
   + Thay vì dùng chỉ số EC2 mặc định, chúng ta sử dụng dữ liệu từ CloudWatch Agent đã cài đặt ở bước 5.5.
   + Tại danh sách Custom Namespaces, chọn `CWAgent` ---> `AutoScalingGroupName, InstanceId, cpu`.
   + Tích chọn chỉ số `cpu_usage_active` của cụm `pawverse-app-asg`. Biểu đồ này cung cấp độ phân giải cực cao về trạng thái tiêu thụ nhân tính toán. Nhấn **Create widget**.
5. **Theo dõi Lưu lượng Cân bằng tải (ALB):**
   + Thêm widget mới ---> Bấm vào chữ **All** (Quay lại thư mục gốc) ---> `ApplicationELB` ---> `Per AppELB Metrics`.
   + Chọn Load Balancer `pawverse-prod-alb` và tích vào chỉ số `RequestCount` (Thống kê số lượng người dùng đang truy cập).
6. **Theo dõi Cơ sở dữ liệu (RDS):**
   + Thêm widget mới ---> `RDS` ---> `Per-Database Metrics`.
   + Chọn Database `pawverse-mysql-db`, tích vào `DatabaseConnections` (Đảm bảo số lượng kết nối DB luôn ở mức an toàn).

![CloudWatch Dashboard](/images/5-Workshop/5.7-Monitoring/cw-metrics.png)
*Hình 5.7.1.1: Bảng điều khiển giám sát tập trung, tích hợp dữ liệu hệ điều hành chuyên sâu từ CWAgent và các dịch vụ mạng.*