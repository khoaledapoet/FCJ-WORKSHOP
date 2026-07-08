---
title : "Dọn dẹp Tài nguyên"
date : 2026-07-08
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

#### Quản lý Chi phí và Thu hồi Tài nguyên (FinOps)
Chúc mừng bạn đã hoàn thành xuất sắc kiến trúc AWS! Bước cuối cùng và cũng là nguyên tắc tối thượng khi làm việc với Điện toán đám mây là: **Dọn dẹp (Clean Up)**. Để tránh các khoản phí phát sinh không mong muốn sau khi Workshop kết thúc, bạn phải thu hồi toàn bộ tài nguyên đã tạo.

Vui lòng thực hiện xóa theo đúng trình tự từ ngoài vào trong dưới đây để tránh lỗi phụ thuộc (Dependency Errors):

#### 1. Tầng Biên (Edge Layer)
1. **CloudFront:** Trạng thái của CloudFront mất nhiều thời gian để cập nhật. Bạn phải chọn Distribution ---> nhấn **Disable**. Chờ khoảng 3-5 phút cho trạng thái chuyển sang *Disabled*, sau đó mới có thể nhấn **Delete**.
2. **S3 Bucket:** Vào Amazon S3, chọn Bucket chứa Frontend. Bạn phải nhấn **Empty** (Làm sạch toàn bộ file bên trong) trước, sau đó mới có thể nhấn **Delete** bucket.
3. **WAF:** Vào AWS WAF, chọn Web ACLs ---> Chọn `pawverse-waf-protection` và nhấn **Delete**.

#### 2. Tầng Máy chủ (Compute Layer)
1. **Auto Scaling Group (ASG):** Truy cập EC2 ---> Auto Scaling Groups ---> Chọn `pawverse-app-asg` và nhấn **Delete**. Quá trình này sẽ tự động Terminate toàn bộ các máy ảo EC2 đang chạy.
2. **Load Balancer (ALB):** Vào mục Load Balancers ---> Chọn `pawverse-prod-alb` và nhấn **Delete**. Tiếp tục vào **Target Groups** và xóa `pawverse-tg`.
3. **Launch Templates:** Vào Launch Templates, chọn template đã tạo ---> Actions ---> **Delete template**.

#### 3. Tầng Dữ liệu & Giám sát (Database & Monitoring)
1. **RDS:** Vào Amazon RDS ---> Databases ---> Chọn `pawverse-mysql-db` ---> Actions ---> **Delete**. (Lưu ý: Bỏ tích ô *Create final snapshot* và tích vào *Acknowledge* để xóa vĩnh viễn).
2. **Secrets Manager:** Xóa két sắt `pawverse-prod-secrets` (Nó sẽ được đưa vào trạng thái chờ xóa sau 7 ngày).
3. **CloudWatch & CloudTrail:** Xóa Alarm `CPU overload` trong CloudWatch và xóa Trail `pawverse-management-trail` trong CloudTrail.

#### 4. Tầng Mạng (Network Layer)
1. **VPC:** Truy cập Amazon VPC ---> Your VPCs ---> Chọn `PawVerse-VPC` ---> Actions ---> **Delete VPC**. 
*(Tính năng thông minh của AWS sẽ tự động quét và xóa toàn bộ Subnets, Route Tables, và Internet Gateway đi kèm bên trong VPC này).*

**Hoàn tất!** Bạn đã dọn dẹp sạch sẽ tài khoản và sẵn sàng cho những dự án thực chiến tiếp theo. Hẹn gặp lại trên đỉnh cao Cloud Computing!