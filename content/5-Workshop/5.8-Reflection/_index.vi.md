---
title : "Live Demo & Đúc kết kinh nghiệm (Reflection)"
date : 2026-07-12
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

Để khép lại hành trình triển khai hạ tầng Đám mây, dưới đây là những hình ảnh thực tế chứng minh sự thành công của dự án PawVerse. Cùng với đó là những đúc kết quan trọng về mặt kỹ thuật mà đội ngũ đã rút ra được trong suốt quá trình vận hành hệ thống trên AWS.

### 1. Chiêm ngưỡng sản phẩm thực tế (Live Showcase)

Hệ thống PawVerse hiện đang vận hành trơn tru 100% trên môi trường Đám mây, phân phối qua tên miền toàn cầu của CloudFront với độ trễ cực thấp.

**Trang Chủ (Home) & Giỏ Hàng (Cart) - Trải nghiệm tốc độ Tầng Biên:**
Giao diện tĩnh và các logic tính toán (Client-side) được phản hồi gần như ngay lập tức. Khách hàng có thể trải nghiệm mua sắm, thêm vào giỏ hàng và áp dụng mã giảm giá mượt mà nhờ sức mạnh Edge Caching.

![Trang chủ PawVerse](/images/home.png)
*Hình 5.8.1: Trang chủ PawVerse với tốc độ tải trang tiệm cận 0 nhờ Amazon S3 & CloudFront.*

![Trang Giỏ hàng PawVerse](/images/cart.png)
*Hình 5.8.2: Giao diện Giỏ hàng xử lý logic tính toán siêu tốc ngay tại trình duyệt.*

**Cổng Quản trị (Admin Gate & Dashboard) - Sức mạnh Tầng Tính toán:**
Không chỉ dừng lại ở giao diện tĩnh, phân hệ Quản trị chứng minh luồng dữ liệu API động hoạt động hoàn hảo. Dữ liệu sản phẩm, biểu đồ doanh thu và số lượng đơn hàng được kéo trực tiếp từ Database lên thông qua kiến trúc Load Balancer (ALB) và EC2.

![Trang Quản lý Sản phẩm](/images/product.png)
*Hình 5.8.3: Phân hệ Quản lý sản phẩm load data thực tế từ RDS Database.*

![Trang Dashboard Admin](/images/dashboard.png)
*Hình 5.8.4: Dashboard thể hiện tổng quan hoạt động kinh doanh (Gọi API Backend thành công).*

---

### 2. Đúc kết kinh nghiệm (Reflection)

Trong quá trình xây dựng kiến trúc từ con số 0 đến một hệ thống Production hoàn chỉnh, chúng tôi đã đối mặt với nhiều bài toán kỹ thuật thực tế và tìm ra hướng giải quyết triệt để.

#### Khó khăn gặp phải
1. **Lỗi bảo mật chéo miền (CORS Error):** Khi Frontend (nằm trên S3) cố gắng gọi API lấy dữ liệu từ Backend (nằm trên ALB), trình duyệt lập tức chặn lại do khác nguồn gốc (Origin), khiến toàn bộ dữ liệu trang Admin không thể hiển thị.
2. **Cơ chế Cache lưu trữ lâu của CDN:** Khi cập nhật phiên bản code Frontend mới lên Amazon S3, người dùng vẫn nhìn thấy giao diện cũ. Lý do là CloudFront lưu bản sao (Cache) tại các điểm biên (Edge Locations) lên đến 24 giờ.
3. **Cấu hình Tường lửa (AWS WAF):** Gặp khó khăn trong việc xác định đúng khu vực (Region) của WAF khi gắn vào CloudFront, dẫn đến việc tường lửa không hoạt động trong những lần kiểm thử đầu tiên.

#### Cách giải quyết
1. **Quy hoạch định tuyến thông minh (Behaviors):** Thay vì mở CORS lỏng lẻo, chúng tôi sử dụng CloudFront làm Proxy trung gian. Thiết lập luồng `/api/*` trỏ về Backend (ALB) và `Default (*)` trỏ về Frontend (S3). Cả hai dùng chung một tên miền, qua đó giải quyết triệt để lỗi CORS một cách bảo mật nhất.
2. **Chủ động vô hiệu hóa Cache (Invalidation):** Tạo thói quen sử dụng lệnh `Create Invalidation /*` trên giao diện CloudFront ngay sau khi upload mã nguồn mới lên S3, ép hệ thống phải xóa bộ nhớ đệm và cập nhật giao diện ngay lập tức cho người dùng.
3. **Tuân thủ nguyên tắc Global:** Nắm vững kiến thức hệ thống, đảm bảo Web ACL của AWS WAF bắt buộc phải được khởi tạo tại khu vực **Global (Asia Pacific - Singapore)** thì mới có thể tích hợp thành công làm khiên chắn cho CloudFront.

#### Hướng phát triển trong tương lai
Hệ thống hiện tại đã đáp ứng tốt các tiêu chuẩn cơ bản (High Availability, Security). Tuy nhiên, để sẵn sàng cho quy mô Doanh nghiệp lớn hơn, dự án hướng tới các nâng cấp sau:
* **Tự động hóa CI/CD:** Tích hợp GitHub Actions để mỗi khi lập trình viên đẩy code mới, hệ thống tự động build và upload lên S3/EC2, đồng thời tự động chạy lệnh Invalidation trên CloudFront.
* **Hiện đại hóa Ứng dụng (Containerization):** Chuyển đổi mã nguồn Backend từ việc chạy trực tiếp trên EC2 sang đóng gói Docker và quản lý bằng **Amazon ECS** hoặc **Amazon EKS**, giúp tối ưu hóa tài nguyên hơn nữa.
