---
title : "Phân phối CloudFront"
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

#### Mạng Phân phối Nội dung (CDN) - Trái tim của Tầng Biên
Amazon CloudFront không chỉ giúp trang web tải cực nhanh nhờ bộ nhớ đệm (Cache) trên toàn cầu, mà còn đóng vai trò như một Proxy thông minh. Nó gộp cả luồng Frontend (S3) và Backend (ALB) về chung một tên miền duy nhất, giải quyết hoàn toàn lỗi bảo mật chéo miền (CORS Error).

1. Truy cập **Amazon CloudFront**, bấm **Create Distribution**.
2. **Origin 1 (Nguồn S3 Frontend):**
   + **Origin domain:** Chọn Bucket S3 `pawverse-frontend-production-bucket` vừa tạo.
   + **Origin access:** Chọn **Origin access control settings (OAC)**. Bấm *Create control setting*. Cấu hình này sinh ra Policy đặc biệt để CloudFront "xuyên thủng" qua bức tường Block Public Access của S3.
3. **Default Cache Behavior:**
   + **Viewer protocol policy:** Chọn **Redirect HTTP to HTTPS** (Ép buộc mã hóa bảo mật).
   + **Allowed HTTP methods:** Chọn `GET, HEAD`.
4. Cuộn xuống và bấm **Create Distribution**. Chú ý sao chép *S3 Bucket Policy* mới sinh ra để dán ngược lại vào cấu hình Permissions của S3.
5. **Origin 2 (Nguồn ALB Backend):**
   + Quay lại Distribution vừa tạo, chuyển sang tab **Origins** ---> Bấm **Create origin**.
   + **Origin domain:** Chọn tên miền của Application Load Balancer (`pawverse-prod-alb...`).
   + **Protocol:** Tích chọn `HTTP only` và bấm Create.
6. **Định tuyến thông minh (Behaviors):**
   + Chuyển sang tab **Behaviors** ---> Bấm **Create behavior**.
   + **Path pattern:** Gõ `/api/*`. 
   + **Origin:** Chọn nguồn thứ 2 là con ALB Backend.
   + **Allowed HTTP methods:** Mở rộng thành `GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE`. Bấm Create.

![Định tuyến CloudFront Behaviors](/images/5-Workshop/5.6-EdgeLayer/cloudfront-behaviors.png)
*Hình 5.6.2.1: Cấu hình định tuyến thông minh, tách biệt luồng API về Load Balancer và luồng tĩnh về S3.*