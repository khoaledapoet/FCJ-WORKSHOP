---
title : "Lưu trữ Frontend S3"
date : 2026-07-07
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

#### Khởi tạo Không gian Lưu trữ Giao diện (Amazon S3)
Các tệp tĩnh của Frontend như HTML, CSS, JavaScript và hình ảnh không cần năng lực tính toán của EC2. Do đó, lưu trữ chúng trên Amazon S3 là giải pháp an toàn và tiết kiệm chi phí nhất.

1. Truy cập dịch vụ **Amazon S3**, chọn **Create bucket**.
2. **Bucket name:** Nhập tên duy nhất toàn cầu (Ví dụ: `pawverse-frontend-production-bucket`).
3. **AWS Region:** Chọn `ap-southeast-1` (Singapore).
4. **Block Public Access settings for this bucket:** 
+ Trái với các bài hướng dẫn S3 thông thường, chúng ta sẽ **GIỮ NGUYÊN dấu tích "Block all public access"** (Chặn toàn bộ truy cập công cộng). 
   + Lý do: Chúng ta không muốn khách hàng truy cập trực tiếp vào S3. Chỉ có mạng CDN (CloudFront) mới được cấp quyền đọc dữ liệu từ Bucket này để đảm bảo an ninh tuyệt đối.
5. Giữ nguyên các thông số còn lại và bấm **Create bucket**.
6. Vào Bucket vừa tạo, chọn tab **Objects** ---> **Upload**. Tải lên toàn bộ các file thư mục đã được *build* của dự án Frontend PawVerse (gồm tệp tin `index.html`, thư mục `css`, `js`, `assets`).

![Lưu trữ S3 Frontend](/images/5-Workshop/5.6-EdgeLayer/s3-bucket.png)
*Hình 5.6.1.1: Mã nguồn tĩnh được đưa lên S3 trong trạng thái khóa quyền truy cập công cộng (Not Public).*