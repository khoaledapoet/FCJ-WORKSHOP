---
title : "Cấu hình Cảnh báo "
date : 2026-07-08
weight : 3
chapter : false
pre : " <b> 5.7.3. </b> "
---

#### Đánh thức Đặc vụ Ứng cứu
Để Auto Scaling Group biết lúc nào cần sinh thêm máy ảo mới, hoặc để Kỹ sư hệ thống kịp thời phát hiện sự cố lúc nửa đêm, chúng ta thiết lập hệ thống cảnh báo (Alarms) kích hoạt bằng AWS SNS (Simple Notification Service).

1. Chuyển sang mục **Alarms** trên CloudWatch ---> Chọn **All alarms** ---> **Create alarm**.
2. **Select metric:** Chọn `EC2` ---> `By Auto Scaling Group` ---> Chọn `CPUUtilization` của `pawverse-app-asg`.
3. **Conditions (Điều kiện kích hoạt):**
   + Thiết lập ngưỡng (Threshold type): **Static**.
   + Điều kiện: **Greater/Equal (>=)**
   + Nhập giá trị: `80` (Cảnh báo khi CPU toàn cụm vượt mức 80%).
4. **Configure actions (Hành động phản hồi):**
   + Tại mục **Notification**, chọn *Create new topic*.
   + Đặt tên Topic: `PawVerse-Alerts`.
   + **Email endpoints:** Nhập địa chỉ Email cá nhân của bạn để nhận tin nhắn báo động.
   + Bấm *Create topic*. (Lưu ý: Bạn phải mở Email và xác nhận Subscribe để SNS kích hoạt gửi tin).
5. Cuộn xuống nhấn **Next**, đặt tên Alarm là `PawVerse-High-CPU-Alert`.
6. Nhấn **Create alarm**. Kể từ lúc này, kiến trúc PawVerse đã hoàn toàn tự động hóa quy trình giám sát và phản hồi sự cố!

![CloudWatch Alarm Config](/images/5-Workshop/5.7-Monitoring/cw-alarm.png)
*Hình 5.7.3.1: Hệ thống cảnh báo tự động gửi thông báo đến Email quản trị viên khi cụm máy chủ vượt ngưỡng tải an toàn.*