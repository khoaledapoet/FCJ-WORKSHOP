---
title : "Định tuyến & Associations"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.3.3. </b> "
---

#### Bước 1: Cấu hình Routing (Định tuyến)
Chúng ta khai báo các "đích đến" cho từng bảng định tuyến.

1. **Public Route Table (`pawverse-rtb-public`):**
   + Tab **Routes** -> **Edit routes** -> Thêm `0.0.0.0/0` trỏ tới **Internet Gateway**.
   ![Định tuyến Public](/images/5-Workshop/5.3-vpc-network/public-route.png)
   *Hình 5.3.3.1: Định tuyến lưu lượng Public ra ngoài qua Internet Gateway.*

2. **Private Route Table (`pawverse-rtb-private`):**
   + Tab **Routes** -> **Edit routes** -> Thêm `0.0.0.0/0` trỏ tới **NAT Gateway**.
   ![Định tuyến Private](/images/5-Workshop/5.3-vpc-network/private-route.png)
   *Hình 5.3.3.2: Định tuyến lưu lượng Private ra ngoài qua NAT Gateway.*

#### Bước 2: Cấu hình Subnet Associations
Sau khi đã có đường đi, ta cần "gắn" (Associate) các Subnet vào các bảng định tuyến tương ứng.

1. **Public Subnet Association:**
   + Trong `pawverse-rtb-public` -> Tab **Subnet associations** -> **Edit subnet associations**.
   + Tích chọn 2 **Public Subnets**.
   ![Gắn Public Subnet](/images/5-Workshop/5.3-vpc-network/public-assoc.png)
   *Hình 5.3.3.3: Gắn các Public Subnet vào bảng định tuyến Public.*

2. **Private Subnet Association:**
   + Trong `pawverse-rtb-private` -> Tab **Subnet associations** -> **Edit subnet associations**.
   + Tích chọn toàn bộ 4 **Private Subnets**.
   ![Gắn Private Subnet](/images/5-Workshop/5.3-vpc-network/private-assoc.png)
   *Hình 5.3.3.4: Gắn toàn bộ các Private Subnet vào bảng định tuyến Private.*

> **💡 Lưu ý:** Nếu thiếu các bước c này, các Subnet sẽ sử dụng bảng định tuyến mặc định của VPC (Main Route Table), gây sai lệch cấu hình mạng nghiêm trọng!