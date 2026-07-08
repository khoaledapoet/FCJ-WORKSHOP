---
title : "Tạo Két sắt Bảo mật"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.4.1. </b> "
---

#### Loại bỏ Hard-code với AWS Secrets Manager
Để tuân thủ tiêu chuẩn bảo mật doanh nghiệp, mã nguồn Backend tuyệt đối không được chứa bất kỳ thông tin đăng nhập, mật khẩu hay khóa bảo mật nào dưới dạng văn bản thuần túy (Plaintext). Thay vào đó, chúng ta sẽ lưu trữ tập trung các thông tin nhạy cảm này vào két sắt điện tử AWS Secrets Manager.

1. Truy cập **AWS Secrets Manager Console**, chọn **Store a new secret**.
2. Tại mục **Secret type**, chọn **Other type of secret**.
3. Tại mục **Key/value pairs**, lần lượt khai báo các biến môi trường cấu hình động cho ứng dụng:
   + `DB_USER` : `pawverse`
   + `DB_PASS` : `pawverse123Secret`
   + `JWT_SECRET` : `mySecretKeyForJwtTokenInPawVerseApplication2026`

![Tạo AWS Secrets Manager](/images/5-Workshop/5.4-Database-Security/secrets-manager.png)
*Hình 5.4.1.1: Khai báo thông tin kết nối Cơ sở dữ liệu dưới dạng các cặp Key/Value bảo mật.*

4. Nhấn **Next**. Tại mục **Secret name**, đặt tên định danh cho môi trường production là: `pawverse-prod-secrets`.
5. Giữ nguyên các cấu hình mặc định khác, cuộn xuống cuối trang và nhấn **Store** để chính thức khởi tạo két sắt bí mật.