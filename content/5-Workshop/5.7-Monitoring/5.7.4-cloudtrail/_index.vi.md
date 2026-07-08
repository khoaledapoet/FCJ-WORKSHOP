---
title : "Kiểm toán CloudTrail"
date : 2026-07-08
weight : 4
chapter : false
pre : " <b> 5.7.4. </b> "
---

#### Truy vết Sự kiện Hệ thống với AWS CloudTrail
Nếu CloudWatch là camera giám sát "sức khỏe" hệ thống, thì CloudTrail chính là camera an ninh ghi lại mọi "hành vi" của con người và hệ thống. CloudTrail ghi lại toàn bộ các lời gọi API, cho phép Kỹ sư vận hành biết chính xác *Ai* đã làm *Gì*, ở *Đâu*, và vào *Lúc nào* trong tài khoản AWS. Đây là tiêu chuẩn bắt buộc (Compliance) trong các dự án doanh nghiệp.

1. Truy cập dịch vụ **AWS CloudTrail**, chọn mục **Trails** từ menu bên trái ---> **Create trail**.
2. **Trail name:** `pawverse-management-trail`.
3. **Storage location:** Chọn *Create new S3 bucket* (Hệ thống sẽ tự động tạo một Bucket S3 chuyên dụng để lưu trữ log kiểm toán an toàn). Giữ nguyên các thiết lập mã hóa KMS mặc định. Nhấn **Next**.
4. **Choose log events:** Tích chọn **Management events** (Ghi lại các thao tác như tạo/xóa EC2, đổi cấu hình Security Group).
5. Cuộn xuống nhấn **Next**, kiểm tra lại thông tin và nhấn **Create trail**.
6. Để xem lịch sử hoạt động, chuyển sang tab **Event history**. Tại đây, mọi thao tác cấu hình từ đầu Workshop đến giờ (như tạo VPC, EC2, thay đổi WAF) đều được ghi nhận chi tiết với đầy đủ địa chỉ IP và tài khoản thực thi.

![Lịch sử sự kiện CloudTrail](/images/5-Workshop/5.7-Monitoring/cloudtrail-logs.png)
*Hình 5.7.4.1: Giao diện CloudTrail Event History ghi nhận toàn bộ dấu vết kiểm toán hạ tầng, đảm bảo tính minh bạch và bảo mật.*