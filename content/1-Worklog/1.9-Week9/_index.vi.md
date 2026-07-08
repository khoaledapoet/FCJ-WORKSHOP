---
title: "Báo cáo Tuần 9"
date: 2026-06-21
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu Tuần 9:
* Bắt đầu giai đoạn 2: Triển khai dự án thực tế PawVerse.
* Thiết lập hoàn chỉnh kiến trúc mạng lõi (VPC) đảm bảo tiêu chuẩn High Availability và cô lập mạng.
* Cấu hình tầng Dữ liệu bảo mật (Database) ẩn sau mạng Private và mã hóa thông tin xác thực.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Phân tích Kiến trúc:**<br>- Nhận requirements dự án PawVerse từ Mentor.<br>- Lên bản vẽ sơ đồ kiến trúc hạ tầng mạng 5 lớp. | 15/06/2026 | 15/06/2026 | PawVerse System Architecture Docs |
| **Ba** | **Xây dựng Mạng lõi (VPC):**<br>- Khởi tạo PawVerse-VPC với dải CIDR chuẩn.<br>- Phân bổ Public và Private Subnets trên 2 Availability Zones. | 16/06/2026 | 16/06/2026 | AWS VPC Documentation |
| **Tư** | **Định tuyến mạng & Gateway:**<br>- Gắn Internet Gateway cho Public Subnet.<br>- Triển khai NAT Gateway cấp Internet cho Private Subnet.<br>- Thiết lập S3 Gateway Endpoint tối ưu băng thông. | 17/06/2026 | 17/06/2026 | AWS VPC Routing Guide |
| **Năm** | **Tường lửa & Quản lý bí mật:**<br>- Viết các quy tắc Security Groups cho Tầng Web và Tầng Database.<br>- Khởi tạo két sắt AWS Secrets Manager lưu trữ mật khẩu DB an toàn. | 18/06/2026 | 18/06/2026 | AWS Security Groups, Secrets Manager |
| **Sáu** | **Triển khai Database:**<br>- Cấu hình Amazon RDS MySQL bên trong Private Subnet.<br>- Khởi tạo cụm ElastiCache Redis tăng tốc độ truy xuất. | 19/06/2026 | 19/06/2026 | Amazon RDS & ElastiCache Docs |

### Kết quả đạt được:
* **Hạ tầng Mạng Vững chắc:** Thiết lập thành công VPC theo chuẩn Best Practices, cách ly hoàn toàn môi trường mạng bên ngoài và bên trong, đồng thời đảm bảo dự phòng (Multi-AZ).
* **Bảo mật Dữ liệu:** Database được ẩn giấu thành công trong Private Subnet. Giải quyết triệt để rủi ro rò rỉ mã nguồn bằng cách sử dụng AWS Secrets Manager thay vì ghi hardcode mật khẩu vào file cấu hình.  