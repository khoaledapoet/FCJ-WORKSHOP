---
title : "Khởi tạo Bộ đệm Redis"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.4.3. </b> "
---

#### Tối ưu Hiệu năng với Amazon ElastiCache Redis
Trong các sự kiện Flash Sale thương mại điện tử, lượng người dùng cùng lúc xem danh mục sản phẩm sẽ tạo ra hàng ngàn truy vấn lặp đi lặp lại. Việc bắt RDS quét ổ cứng liên tục sẽ làm nghẽn cổ chai hệ thống. Chúng ta triển khai một cụm bộ đệm trên RAM (In-memory Cache) sử dụng Redis đặt trong Private Subnet để xử lý bài toán tải cao này.

1. Truy cập dịch vụ **Amazon ElastiCache**, chọn **Redis OSS clusters** ---> **Create Redis OSS cluster**.
2. **Cluster deployment option:** Chọn **Design your own cluster** và cấu hình tùy chọn **Cluster mode enabled** để tối ưu hóa khả năng mở rộng dữ liệu và phân mảnh linh hoạt.
3. **Cluster info:** Đặt tên cụm là `pawverse-redis`.
4. **Location:** Chọn đám mây AWS Cloud, lựa chọn thế hệ Node type tối ưu hiệu năng và chi phí là `cache.t4g.micro`.
5. **Connectivity (Mạng lưới):**
   + Chọn VPC: `pawverse-vpc`.
   + Chọn Subnet Group bao gồm các phân vùng **Private Subnet** nội bộ của hệ thống.
6. Để bảo vệ dữ liệu trên đường truyền nội bộ, tính năng Mã hóa khi truyền tải (Encryption in transit) được kích hoạt nhằm đáp ứng tiêu chuẩn an toàn thông tin doanh nghiệp.

![Cụm ElastiCache Redis](/images/5-Workshop/5.4-Database-Security/elasticache-redis.png)
*Hình 5.4.3.1: Hệ thống lưu trữ bộ đệm Redis đã khởi tạo thành công với trạng thái Available.*

7. Nhấn **Create**. Khi cụm đổi sang trạng thái màu xanh **Available**, sao chép lại địa chỉ **Configuration Endpoint** (chuỗi địa chỉ tổng quan dùng để định tuyến cho toàn cụm khi bật Cluster mode). Chuỗi địa chỉ này sẽ được nạp động vào biến môi trường của máy chủ EC2 Backend ở bước tiếp theo để kích hoạt tính năng lưu đệm dữ liệu.