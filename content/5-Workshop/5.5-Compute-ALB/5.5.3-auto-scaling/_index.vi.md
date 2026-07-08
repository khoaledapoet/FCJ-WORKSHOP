---
title : "Cấu hình Auto Scaling"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

#### Triển khai Cụm máy chủ tự co giãn (Auto Scaling Group)
Auto Scaling Group (ASG) là công cụ chịu trách nhiệm duy trì sức sống ổn định cho ứng dụng. Nó theo dõi sức khỏe của EC2, tự động tạo mới máy chủ thay thế nếu có máy bị sập, và co giãn số lượng máy dựa theo nhu cầu thực tế của người dùng.

1. Tại EC2 Dashboard, chọn mục **Auto Scaling Groups** dưới cùng thanh menu trái ---> **Create Auto Scaling group**.
2. **Auto Scaling group name:** `pawverse-app-asg`.
3. **Launch template:** Chọn đúng bản mẫu `pawverse-app-template` đã làm ở bài 5.5.1. Nhấn **Next**.
4. **Network settings:**
   + **VPC:** Chọn `pawverse-vpc`.
   + **Availability Zones and subnets:** Tích chọn chính xác **2 Private EC2 Subnets** (Tuyệt đối không chọn Public Subnet hay DB Subnet). Điều này đảm bảo toàn bộ máy chủ Backend chạy mã nguồn sẽ ẩn mình an toàn trước Internet. Nhấn **Next**.
5. **Configure advanced options:**
   + Tại mục **Load balancing**, tích chọn **Attach to an existing load balancer**.
   + Chọn nhóm Target Group của bạn: `pawverse-app-tg`.
   + Tại mục **Health checks**, tích chọn thêm **Elastic Load Balancing (ELB)** để ASG nhận diện máy sập nếu ALB báo lỗi health check. Nhấn **Next**.
6. **Configure group size and scaling policies:**
   + **Desired capacity (Số lượng mong muốn):** `2` *(Đảm bảo luôn luôn có 2 máy chạy song song chia tải)*.
   + **Minimum capacity (Số lượng tối thiểu):** `2`.
   + **Maximum capacity (Số lượng tối đa):** `5` *(Giới hạn ngưỡng nở tối đa khi bị tấn công hoặc quá tải để bảo vệ ngân sách)*.

![Cấu hình Quy mô ASG](/images/5-Workshop/5.5-Compute-ALB/asg-capacity.png)
*Hình 5.5.3.1: Thiết lập cấu hình số lượng quy mô co giãn an toàn cho cụm máy chủ dự án PawVerse.*

7. Nhấn **Next** liên tục qua các bước Tag và nhấn **Create Auto Scaling group**. Hệ thống sẽ ngay lập tức dựa trên cấu hình để tự động sinh ra 2 máy ảo EC2 đầu tiên.