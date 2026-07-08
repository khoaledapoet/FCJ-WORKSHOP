---
title : "Nhật ký Tập trung "
date : 2026-07-08
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

#### Truy xuất Log Ứng dụng từ xa
Khi hệ thống có nhiều máy ảo chạy song song (Auto Scaling), việc kết nối SSH vào từng máy để xem lỗi là bất khả thi. Thay vào đó, CloudWatch Agent cài đặt sẵn sẽ hút toàn bộ Log của Spring Boot và đẩy về một nơi lưu trữ duy nhất.

1. Tại thanh menu trái của CloudWatch, mở rộng mục **Logs** ---> Chọn **Log groups**.
2. Tìm kiếm nhóm Log Group có tên cấu hình từ SSM (Ví dụ: `/aws/ec2/pawverse-backend` hoặc tên tương ứng khai báo trong file cấu hình CloudWatch Agent).
3. Nhấp vào Log Group, bạn sẽ thấy danh sách các **Log streams** - mỗi stream đại diện cho một con máy ảo EC2 đang chạy.
4. Bấm vào một Log stream bất kỳ. Tại đây, toàn bộ màn hình Console của Docker và Spring Boot (Bao gồm lịch sử khởi động, thông tin kết nối Database, và các lỗi 403, 500 nếu có) đều hiển thị rõ ràng theo trình tự thời gian.

![CloudWatch Logs](/images/5-Workshop/5.7-Monitoring/cw-logs.png)
*Hình 5.7.2.1: Truy xuất và phân tích mã lỗi từ ứng dụng Spring Boot thông qua hệ thống quản lý nhật ký tập trung.*