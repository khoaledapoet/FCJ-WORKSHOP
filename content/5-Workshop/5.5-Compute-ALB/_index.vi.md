---
title : "Máy chủ & Cân bằng tải"
date : 2026-07-07
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Tầng Tính toán và Điều phối Lưu lượng (Compute & Load Balancing Layer)
Sau khi đã thiết kế xong hệ thống mạng an toàn và tầng dữ liệu cô lập, đây là lúc chúng ta triển khai tầng xử lý logic của ứng dụng (Backend Application). 

Để đáp ứng các tiêu chuẩn khắt khe về tính sẵn sàng cao (High Availability), khả năng tự phục hồi (Self-healing) và tự động co giãn khi lượng truy cập tăng đột biến, hệ thống tính toán của PawVerse sẽ không sử dụng các máy chủ đơn lẻ cố định. Thay vào đó, chúng ta sẽ kết hợp sức mạnh của 3 dịch vụ cốt lõi: Launch Templates, Application Load Balancer (ALB) và Auto Scaling Group (ASG).

Trong chương này, chúng ta sẽ lần lượt thực hiện 4 bước triển khai thực tế:
1. **Khởi tạo Launch Template:** Định nghĩa cấu hình phần cứng mẫu và viết kịch bản tự động hóa khởi tạo máy chủ (User Data).
2. **Thiết lập Application Load Balancer:** Cấu hình bộ cân bằng tải đặt tại Public Subnet để điều phối lưu lượng truy cập từ Internet.
3. **Cấu hình Auto Scaling Group:** Thiết lập cụm máy chủ co giãn linh hoạt đặt ẩn sâu trong Private Subnet.
