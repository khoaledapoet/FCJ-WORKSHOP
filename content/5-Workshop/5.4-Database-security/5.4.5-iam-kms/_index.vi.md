---
title : "Bảo mật IAM & KMS"
date : 2026-07-07
weight : 5
chapter : false
pre : " <b> 5.4.5. </b> "
---

#### 1. Cơ chế Mã hóa Dữ liệu ở Trạng thái Nghỉ (AWS KMS Encryption)
Hệ thống quản lý két sắt Secrets Manager và cơ sở dữ liệu RDS không lưu trữ thông tin dưới dạng văn bản thô. Để bảo vệ dữ liệu chống lại các hành vi xâm nhập vật lý vào trung tâm dữ liệu, cơ chế mã hóa toàn diện (Encryption at rest) được áp dụng.

Khi khởi tạo `pawverse-prod-secrets`, AWS mã hóa toàn bộ thông tin bằng cách kết hợp với dịch vụ **AWS Key Management Service (KMS)**. Hệ thống sử dụng khóa quản lý mặc định `aws/secretsmanager`. Mọi hành động đọc ghi bất hợp pháp từ những thực thể không có quyền tương tác với khóa KMS này sẽ chỉ thu được những chuỗi dữ liệu nhị phân đã bị xáo trộn hoàn toàn.

![Mã hóa KMS](/images/5-Workshop/5.4-Database-Security/kms-key.png)
*Hình 5.4.5.1: Cấu hình mã hóa tự động tích hợp khóa quản lý AWS KMS bảo vệ lớp dữ liệu ẩn.*

#### 2. Định danh Thực thể Máy chủ với IAM Role
Áp dụng nguyên lý Đặc quyền tối thiểu (Least Privilege), máy chủ EC2 khi khởi chạy không được phép nhúng cố định (hard-code) các cặp Access Key / Secret Key dài hạn của tài khoản AWS. Thay vào đó, máy chủ sẽ tự động nhận diện các quyền hạn ngắn hạn bảo mật cao thông qua việc gán một **IAM Role** cụ thể.

Trong phạm vi Workshop thực hành này, chúng ta sử dụng một định danh có sẵn mang tên **`lab`**. Cấu hình kiểm toán thực tế cho thấy Role này sở hữu 4 đặc quyền quản trị mạng cốt lõi:
+ **`SecretsManagerReadWrite`**: Cho phép mã nguồn Backend thực hiện hành động gọi API bảo mật để lấy chuỗi giải mã thông tin Database từ két sắt một cách tự động khi khởi động.
+ **`AmazonSSMManagedInstanceCore`**: Cho phép đội ngũ kỹ sư vận hành Cloud kết nối an toàn vào shell hệ điều hành thông qua Systems Manager Session Manager trên trình duyệt, loại bỏ hoàn toàn việc phải mở cổng cổng SSH truyền thống (Port 22).
+ **`CloudWatchAgentServerPolicy`**: Cấp quyền cho các tiến trình nền chạy trong máy chủ thu thập và gửi các chỉ số hiệu năng (Log hệ thống, % CPU, % dung lượng bộ nhớ RAM) về trung tâm giám sát CloudWatch tập trung.

![IAM Role lab](/images/5-Workshop/5.4-Database-Security/iam-role.png)
*Hình 5.4.5.2: Danh sách các quyền hạn thực thi an toàn (Policies) được đính kèm vào định danh IAM Role 'lab'.*