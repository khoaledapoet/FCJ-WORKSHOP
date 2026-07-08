---
title : "Khởi tạo Launch Template"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

#### Thiết lập Bản mẫu Khởi chạy (Launch Template)
Launch Template đóng vai trò như một khuôn mẫu đúc sẵn. Khi hệ thống cần mở rộng hoặc thay thế một máy chủ bị lỗi, Auto Scaling Group sẽ nhìn vào khuôn mẫu này để nhân bản các máy chủ mới một cách đồng nhất.

1. Truy cập **EC2 Dashboard**, chọn **Launch Templates** từ menu bên trái ---> **Create launch template**.
2. **Launch template name:** `pawverse-app-template`.
3. **Application and OS Images (AMI):** Chọn **Amazon Linux 2023 AMI** (Bản phân phối Linux tối ưu và bảo mật nhất trên AWS).
4. **Instance type:** Lựa chọn `t3.micro` hoặc `t4g.micro` phụ thuộc vào kiến trúc chip để tối ưu chi phí tài khoản thực hành.
5. **Key pair:** Chọn khóa Key pair có sẵn của bạn để dự phòng trường hợp cần gỡ lỗi trực tiếp.
6. **Network settings:**
   + Chọn **Don't include in launch template** đối với Subnet (Vì vị trí Subnet sẽ do cụm Auto Scaling chỉ định sau).
   + **Security Groups:** Chọn nhóm Security Group chuyên dụng của EC2, cấu hình chỉ cho phép Port mạng của ứng dụng (Ví dụ: `8080` hoặc `3000`) nhận traffic chuyển tiếp duy nhất từ Application Load Balancer.
7. **Advanced Details (Cấu hình nâng cao):**
   + **IAM instance profile:** Chọn chính xác thực thể **`lab`** mà chúng ta đã kiểm toán ở chương trước. Đây là chìa khóa để EC2 có quyền lấy thông tin bảo mật.
   + **User data:** Dán đoạn mã script tự động hóa dưới đây vào khung văn bản. Đoạn script này sẽ tự động chạy dưới quyền `root` ngay khi máy ảo vừa được bật lên:

```bash
#!/bin/bash
# 1. Cập nhật hệ điều hành và cài đặt các công cụ cần thiết
dnf update -y
dnf install -y jsonfilter jq awscli wget

# 2. Tải và cấu hình ứng dụng Backend PawVerse
mkdir -p /app && cd /app
# Giả lập tải mã nguồn ứng dụng production đã đóng gói
wget -O pawverse-backend [https://github.com/thienluhoan/fcj-workshop/raw/main/artifacts/backend-app](https://github.com/thienluhoan/fcj-workshop/raw/main/artifacts/backend-app)
chmod +x pawverse-backend

# 3. Kéo thông tin Credentials động từ AWS Secrets Manager
REGION="ap-southeast-1"
SECRET_RAW=$(aws secretsmanager get-secret-value --secret-id pawverse-prod-secrets --region $REGION --query SecretString --output text)

# Giải mã cấu hình json và xuất thành biến môi trường hệ thống
export DB_USER=$(echo $SECRET_RAW | jq -r '.DB_USER')
export DB_PASS=$(echo $SECRET_RAW | jq -r '.DB_PASS')
export JWT_SECRET=$(echo $SECRET_RAW | jq -r '.JWT_SECRET')

# Điền thông tin Host Endpoint của RDS và ElastiCache thực tế vào đây
export DB_HOST="pawverse-mysql.cpseu6iqs3oe.ap-southeast-1.rds.amazonaws.com"
export REDIS_HOST="clustercfg.pawverse-redis.ckq3fs.apse1.cache.amazonaws.com"

# 4. Khởi chạy tiến trình Backend chạy ngầm
nohup ./pawverse-backend > /var/log/pawverse.log 2>&1 &
```

![Cấu hình Launch Template](/images/5-Workshop/5.5-Compute-ALB/launch-template.png)
*Hình 5.5.1.1: Giao diện đính kèm IAM Role 'lab' và nạp mã lệnh tự động hóa User Data.*

8. Nhấn **Create launch template** để hoàn tất bản thiết kế máy chủ mẫu.