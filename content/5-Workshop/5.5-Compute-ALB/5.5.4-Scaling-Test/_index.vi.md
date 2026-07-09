---
title: "Kiểm thử Tính sẵn sàng cao & Tự động co giãn"
date: 2026-07-09
weight: 4
chapter: false
pre: " <b> 5.5.4. </b> "
---

Để xác thực cơ chế tự động co giãn (Auto Scaling) hoạt động đúng như thiết kế khi hệ thống chịu tải cao, chúng ta sẽ tiến hành giả lập một cuộc tấn công vắt kiệt tài nguyên CPU (CPU Stress) ngay trên một máy chủ EC2 đang hoạt động.

#### Bước 1: Truy cập vào một máy chủ EC2 Backend
Sử dụng **AWS Systems Manager Session Manager** để kết nối an toàn vào một trong các máy chủ EC2 do Auto Scaling Group (ASG) sinh ra mà không cần mở cổng SSH (port 22) ra internet công cộng.

#### Bước 2: Cài đặt công cụ giả lập tải `stress`
Chạy các lệnh sau trên terminal của máy chủ để cài đặt công cụ ép tải CPU trên môi trường Amazon Linux 2023:

```bash
sudo apt update
sudo apt install -y stress
```

#### Bước 3: Tiến hành ép tải CPU lên 100%
Chạy công cụ `stress` để vắt kiệt tài nguyên của 2 nhân CPU trong vòng 600 giây (10 phút):

```bash
stress --cpu 2 --timeout 600s
```
*(Bạn có thể mở một tab Session Manager khác và chạy lệnh `top` để thấy CPU của máy chủ lập tức nhảy lên mức 100%).*

#### Bước 4: Kiểm tra kết quả nghiệm thu trên AWS Console
1. **Kiểm tra CloudWatch Alarms:** Chờ từ 2 - 3 phút, số liệu CPU truyền về CloudWatch vượt ngưỡng 80%. Chuông cảnh báo sẽ chuyển từ trạng thái `OK` sang **`In alarm`** (Màu đỏ).
2. **Kiểm tra Auto Scaling Group (ASG):** Truy cập vào mục ASG > **Activity history**. Bạn sẽ thấy một bản ghi tự động xuất hiện với nội dung: *"Launching a new EC2 instance..."*. ASG đã tự động kích hoạt thêm máy chủ mới thành công để chia tải.
3. **Hạ tải hệ thống:** Bấm `Ctrl + C` trên terminal để tắt tiến trình `stress`. Sau thời gian cooldown (thời gian giảm nhiệt), kiểm tra mục Activity history của ASG để đảm bảo hệ thống tự động xóa bỏ máy chủ thừa (**Scale-in**), đưa hạ tầng về trạng thái tối ưu chi phí ban đầu.


![Kết quả test Auto Scaling](/images/asg-test-result.png)