---
title : "Giám sát & Cảnh báo"
date : 2026-07-08
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Giám sát Vận hành với Amazon CloudWatch (Observability Layer)
Một hệ thống Cloud hoàn chỉnh không chỉ cần chạy được, mà còn phải có khả năng tự báo cáo tình trạng sức khỏe. Nếu không có công cụ giám sát, kỹ sư hệ thống sẽ hoàn toàn "mù" trước các sự cố như nghẽn cổ chai CPU, cạn kiệt RAM, hoặc ứng dụng bị lỗi ngầm.

Đó là lý do ở bước khởi tạo EC2 (Phần 5.5), chúng ta đã chủ động nhúng đặc vụ **CloudWatch Agent** vào hệ điều hành. Đặc vụ này đóng vai trò như một camera an ninh, liên tục thu thập nhật ký (Logs) và chỉ số phần cứng (Metrics) gửi về trung tâm điều khiển.

Trong chương cuối này, chúng ta sẽ thiết lập bảng điều khiển theo dõi 3 khía cạnh cốt lõi:
1. **Metrics (Chỉ số đo lường):** Theo dõi sức khỏe của EC2 (CPU, Network), ALB (Lượng Request) và RDS (Kết nối Database).
2. **Logs (Nhật ký tập trung):** Truy xuất log của ứng dụng Backend Spring Boot từ xa mà không cần SSH trực tiếp vào máy chủ.
3. **Alarms (Cảnh báo chủ động):** Cấu hình còi báo động tự động gửi Email/SMS khi CPU vượt ngưỡng hoặc hệ thống có dấu hiệu quá tải.