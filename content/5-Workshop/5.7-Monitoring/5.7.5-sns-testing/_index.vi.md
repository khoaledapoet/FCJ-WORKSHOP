---
title : "Kiểm thử Cảnh báo (SNS)"
date : 2026-07-08
weight : 5
chapter : false
pre : " <b> 5.7.5. </b> "
---

#### Kiểm thử Hệ thống Phản hồi Sự cố
Để đảm bảo hệ thống chuông báo động (CloudWatch Alarm) và gửi tin nhắn (SNS) hoạt động chính xác khi có sự cố thật, chúng ta sẽ thực hiện một bài kiểm thử chủ động (Fault Injection) bằng cách ép trạng thái của Alarm thay vì phải tấn công DDOS làm sập máy chủ.

1. Truy cập giao diện **AWS CloudShell** (Biểu tượng Terminal ở góc trên cùng bên phải màn hình AWS Console).
2. Sử dụng công cụ AWS CLI để giả lập một sự kiện quá tải CPU, ép Alarm `PawVerse-High-CPU-Alert` chuyển ngay sang trạng thái báo động (ALARM) bằng lệnh sau:
   ```bash
   aws cloudwatch set-alarm-state \
       --alarm-name "PawVerse-High-CPU-Alert" \
       --state-value ALARM \
       --state-reason "Testing SNS email integration for PawVerse Project"
   ```
3. **Kết quả kỳ vọng:** + Ngay lập tức, trạng thái của Alarm trên bảng điều khiển CloudWatch sẽ chuyển sang màu đỏ **(In alarm)**.
   + Kiểm tra hộp thư Email đã đăng ký ở bước trước. Bạn sẽ nhận được một email khẩn cấp từ `AWS Notifications` với tiêu đề báo động về việc vi phạm ngưỡng CPU của hệ thống PawVerse.
   + Bài kiểm thử thành công, chứng minh luồng tự động hóa phản hồi sự cố (Incident Response) đã sẵn sàng bảo vệ hệ thống 24/7.

![Xác nhận Email SNS](/images/5-Workshop/5.7-Monitoring/sns-email.png)
*Hình 5.7.5.1: Cảnh báo tự động được kích hoạt và gửi thành công đến hòm thư quản trị viên thông qua dịch vụ AWS SNS.*