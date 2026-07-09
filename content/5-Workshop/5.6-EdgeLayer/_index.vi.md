---
title : "Tầng Biên & Phân phối"
date : 2026-07-07
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### Tầng Phân phối và Bảo mật Biên (Edge Delivery & Security Layer)

Nếu VPC, EC2 và Database là phần "nội tạng" cốt lõi của PawVerse, thì Tầng Biên (Edge Layer) chính là "lớp da" bảo vệ bên ngoài, là nơi đầu tiên tiếp xúc với hàng triệu khách hàng toàn cầu. 

Trong kiến trúc đám mây hiện đại, chúng ta không bao giờ cho phép người dùng cuối kết nối trực tiếp vào máy chủ xử lý logic (Backend). Thay vào đó, mọi luồng dữ liệu đều phải đi qua Tầng Biên để được tối ưu hóa tốc độ và lọc bỏ các yêu cầu độc hại.

Trong chương cuối cùng của Workshop, chúng ta sẽ thực hiện 3 bước triển khai:
1. **Lưu trữ tĩnh S3:** Tạo không gian lưu trữ mã nguồn giao diện Frontend (React/Vue/HTML) với chi phí cực thấp nhưng độ bền bỉ lên tới 99.999999999%.
2. **Mạng phân phối CloudFront (CDN):** Đưa giao diện đến các điểm hiện diện (Edge Locations) trên toàn thế giới để giảm thiểu độ trễ mạng, đồng thời hợp nhất luồng truy cập Frontend và Backend về chung một tên miền.
3. **Tường lửa Web (AWS WAF):** Thiết lập rào chắn chủ động kiểm tra từng gói tin, chặn đứng các cuộc tấn công DDoS, SQL Injection hay Cross-Site Scripting (XSS) ngay trước khi chúng kịp lọt vào hạ tầng VPC.
