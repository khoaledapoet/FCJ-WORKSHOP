---
title: "Báo cáo Tuần 11"
date: 2026-07-05
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:
* Triển khai Tầng Biên (Edge Layer) nhằm phân phối giao diện web tĩnh ra toàn cầu.
* Giải quyết triệt để lỗi CORS bằng kiến trúc Proxy của CDN.
* Thiết lập hệ thống tường lửa lớp ứng dụng để bảo vệ chống mã độc.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Lưu trữ tĩnh (S3 Hosting):**<br>- Cấu hình Amazon S3 Bucket chứa mã nguồn Frontend PawVerse.<br>- Khóa chặt toàn bộ truy cập công cộng (Block all public access). | 29/06/2026 | 29/06/2026 | Amazon S3 Security Standards |
| **Ba** | **Phân phối CDN (CloudFront):**<br>- Khởi tạo CloudFront Distribution làm mạng phân phối nội dung toàn cầu.<br>- Cấu hình Origin Access Control (OAC) cấp quyền cho CloudFront đọc dữ liệu từ S3. | 30/06/2026 | 30/06/2026 | Amazon CloudFront CDN Setup |
| **Tư** | **Định tuyến thông minh:**<br>- Bổ sung ALB làm Origin thứ 2 trong CloudFront.<br>- Thiết lập Behaviors để chia luồng mạng: /api/* điều hướng về ALB, luồng mặc định về S3. | 01/07/2026 | 01/07/2026 | CloudFront Dynamic Routing |
| **Năm** | **Bảo mật Tầng Biên (WAF):**<br>- Kích hoạt tính năng bảo mật AWS WAF gắn kèm CloudFront.<br>- Bổ sung các tập luật (Managed Rules) của AWS để chặn IPs độc hại. | 02/07/2026 | 02/07/2026 | AWS WAF Rule Groups |
| **Sáu** | **Bảo vệ CSDL:**<br>- Tinh chỉnh cấu hình WAF, thêm lá chắn SQL Injection để bảo vệ tối đa tầng RDS nằm sâu bên trong. | 03/07/2026 | 03/07/2026 | OWASP Mitigation on AWS |

### Kết quả đạt được:
* **Tối ưu tốc độ tải trang:** Giao diện Frontend được phân phối qua các điểm Edge Location của CloudFront giúp giảm thiểu độ trễ tối đa cho người dùng toàn cầu.
* **Bảo mật tuyệt đối:** Kiến trúc chặn hoàn toàn truy cập trực tiếp vào S3 và EC2. Hệ thống WAF hoạt động hiệu quả như một tấm khiên soi chiếu từng gói tin, chặn đứng các cuộc tấn công SQL Injection nhằm vào cơ sở dữ liệu.