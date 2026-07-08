---
title : "Thiết lập Cân bằng tải"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

#### 1. Khởi tạo Target Group (Nhóm đích)
Trước khi tạo bộ cân bằng tải, chúng ta cần định nghĩa một nhóm logic chứa các máy chủ nhận lưu lượng và cách thức kiểm tra sức khỏe (Health Check) của chúng.

1. Tại EC2 Dashboard, cuộn xuống mục **Load Balancing** ---> chọn **Target Groups** ---> **Create target group**.
2. **Target type:** Chọn **Instances**.
3. **Target group name:** `pawverse-app-tg`.
4. **Protocol & Port:** Chọn **HTTP** và điền Port tương ứng của ứng dụng (Ví dụ: `8080`).
5. **VPC:** Chọn `pawverse-vpc`.
6. **Health checks:** Giữ nguyên giao thức HTTP, đường dẫn kiểm tra sức khỏe mặc định là `/` hoặc chỉnh sửa theo API thực tế (Ví dụ: `/health`). Nhấn **Next**.
7. Bỏ qua bước đăng ký máy chủ thủ công (Vì Auto Scaling Group sẽ tự động đăng ký sau). Nhấn **Create target group**.

#### 2. Khởi tạo Application Load Balancer (ALB)
ALB đóng vai trò là chốt chặn đầu tiên tại lớp Public, hứng toàn bộ yêu cầu của khách hàng từ Internet rồi thông minh phân phối xuống cụm máy chủ Backend an toàn phía sau.

1. Chọn mục **Load Balancers** bên dưới thanh menu ---> Bấm **Create load balancer**.
2. Chọn loại **Application Load Balancer** ---> Bấm **Create**.
3. **Load balancer name:** `pawverse-prod-alb`.
4. **Scheme:** Chọn **Internet-facing** *(Đón nhận lưu lượng công cộng từ ngoài Internet)*.
5. **Network mapping:**
   + Chọn VPC: `pawverse-vpc`.
   + **Mappings (Phân vùng mạng):** Tích chọn 2 vùng Availability Zone và chọn chính xác **2 Public Subnets** đã chia. Điều này đảm bảo ALB có thể giao tiếp với Internet bên ngoài.

![Cấu hình Mạng cho ALB](/images/5-Workshop/5.5-Compute-ALB/alb.png)
*Hình 5.5.2.1: Ánh xạ cấu hình định tuyến cho Application Load Balancer vào các Public Subnets.*

6. **Security Groups:** Chọn nhóm Security Group của ALB, cho phép mở Port công cộng công khai (Mở HTTP Port `80` và HTTPS Port `443` ra toàn thế giới `0.0.0.0/0`).
7. **Listeners and routing:** Tại Listener HTTP:80, chọn hành động chuyển tiếp (Forward to) đến Target Group **`pawverse-app-tg`** vừa thiết lập ở bước trên.
8. Cuộn xuống cuối và nhấn **Create load balancer**.