---
title : "VPC & Internet Gateway"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### 1. Khởi tạo mạng nội bộ (VPC)
Chúng ta sẽ sử dụng công cụ **VPC and more** để tự động hóa việc phác thảo hạ tầng mạng cốt lõi.

1. Truy cập **VPC Dashboard**, chọn **Create VPC** -> Tùy chọn **VPC and more**.
2. **Name tag:** `pawverse`.
3. **IPv4 CIDR block:** `10.0.0.0/16`.
4. **Availability Zones (AZs):** Chọn **2** (`ap-southeast-1a` và `1b`) để đảm bảo dự phòng (High Availability).
5. **Subnets:** Thiết lập **2 Public subnets** (Dành cho ALB) và **4 Private subnets** (Dành cho EC2 và Database).

![Khởi tạo VPC](/images/5-Workshop/5.3-vpc-network/vpc.png)
*Hình 5.3.1.1: Cấu hình dải mạng và chia Subnet cho dự án PawVerse.*

#### 2. Kiểm tra Internet Gateway (IGW)
Internet Gateway là "cánh cửa" duy nhất cho phép mạng VPC giao tiếp với Internet bên ngoài. Mặc dù công cụ trên đã tạo sẵn, một kỹ sư Cloud luôn phải kiểm tra lại trạng thái gắn kết của nó.

1. Tại menu trái của VPC, chọn **Internet gateways**.
2. Tìm kiếm IGW có tên `pawverse-igw`.
3. Kiểm tra cột **State**, phải đảm bảo trạng thái là **Attached** (Đã gắn) vào VPC `pawverse-vpc`. Nếu trạng thái là Detached, bạn phải chọn *Actions -> Attach to VPC*.

![Kiểm tra IGW](/images/5-Workshop/5.3-vpc-network/igw.png)
*Hình 5.3.1.2: Xác nhận Internet Gateway đã được gắn thành công vào VPC.*