---
title : "NAT Gateway & Endpoint"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

#### 1. Thiết lập NAT Gateway cho Private Subnet
Máy chủ EC2 nằm trong mạng Private không có Public IP, nên nó không thể đi qua Internet Gateway. Để EC2 ra ngoài tải các bản cập nhật an toàn (chỉ đi ra, không cho truy cập vào), ta dùng NAT Gateway.

1. Chọn **NAT Gateways** -> **Create NAT gateway**.
2. Đặt NAT Gateway tại `pawverse-subnet-public1-ap-southeast-1a` (Bắt buộc phải nằm ở Public Subnet).
3. Bấm **Allocate Elastic IP** để cấp phát một địa chỉ IP tĩnh.

![Tạo NAT Gateway](/images/5-Workshop/5.3-vpc-network/nat-gateway.png)
*Hình 5.3.2.1: Khởi tạo NAT Gateway để cấp quyền ra Internet 1 chiều cho máy ảo nội bộ.*

#### 2. Tối ưu bằng S3 Gateway Endpoint
Nếu EC2 đẩy file lên Amazon S3 thông qua NAT Gateway, luồng dữ liệu sẽ đi vòng ra Internet và gây tốn phí băng thông. S3 Gateway Endpoint sẽ tạo một "đường hầm" trực tiếp trong mạng nội bộ AWS.

1. Tại VPC Dashboard, chọn **Endpoints** -> **Create endpoint**.
2. Tên Endpoint: `pawverse-s3-endpoint`.
3. Tìm dịch vụ `s3` và chọn **`com.amazonaws.ap-southeast-1.s3`** (Type: **Gateway**).

![Cấu hình S3 Gateway Endpoint](/images/5-Workshop/5.3-vpc-network/s3-endpoint.png)
*Hình 5.3.2.2: Lựa chọn dịch vụ S3 Gateway Endpoint tại khu vực ap-southeast-1.*

4. Chọn VPC `pawverse-vpc`, tích chọn vào các **Private Route Tables** để tự động định tuyến. Bấm **Create endpoint**.  