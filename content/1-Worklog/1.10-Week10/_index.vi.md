---
title: "Báo cáo Tuần 10"
date: 2026-06-28
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:
* Cấu hình tầng máy chủ tính toán (Compute Layer) cho dự án PawVerse.
* Tự động hóa quá trình cài đặt phần mềm bên trong máy chủ.
* Thiết lập hệ thống điều phối lưu lượng và tự động co giãn tài nguyên.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Phân quyền IAM:**<br>- Tạo IAM Role cho phép EC2 đọc dữ liệu từ Secrets Manager và gửi Log lên CloudWatch. | 22/06/2026 | 22/06/2026 | |
| **Ba** | **Chuẩn hóa Server (Launch Template):**<br>- Thiết kế Launch Template, chọn AMI Amazon Linux 2023.<br>- Viết kịch bản Bash Script (User Data) tự động cài đặt Docker, kéo Source Code và cấu hình CloudWatch Agent. | 23/06/2026 | 23/06/2026 |  |
| **Tư** | **Định tuyến nội bộ:**<br>- Khởi tạo Target Group để theo dõi sức khỏe (Health Check) của các máy chủ Backend Spring Boot. | 24/06/2026 | 24/06/2026 |  |
| **Năm** | **Cân bằng tải (ALB):**<br>- Triển khai Application Load Balancer (ALB) hứng traffic từ bên ngoài.<br>- Liên kết ALB với Target Group để phân phối luồng truy cập. | 25/06/2026 | 25/06/2026 |  |
| **Sáu** | **Co giãn linh hoạt (Auto Scaling):**<br>- Tạo Auto Scaling Group gắn với ALB.<br>- Xác thực khả năng hệ thống tự động sinh 2 máy ảo khỏe mạnh (Healthy) và kết nối chéo thành công. | 26/06/2026 | 26/06/2026 |  |

### Kết quả đạt được:
* **Tự động hóa Bootstrap:** Áp dụng thành công kịch bản User Data giúp máy chủ EC2 mới sinh ra có khả năng tự động tải mã nguồn, giải mã secret và khởi động Docker mà không cần can thiệp thủ công.
* **Đảm bảo Tính sẵn sàng cao (HA):** Luồng mạng từ ALB phân phối đồng đều tải xuống các máy chủ EC2. Auto Scaling Group đảm bảo hệ thống PawVerse luôn duy trì trạng thái ổn định ngay cả khi có lượng truy cập đột biến.