---
title: "Bản đề xuất"
date: 2024-07-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Hệ thống Go Flashsale cho Môi trường E-Commerce
## Giải pháp AWS tự động co giãn và chịu tải cao cho sự kiện bán hàng chớp nhoáng

### 1. Tóm tắt điều hành
Hệ thống Go Flashsale được thiết kế để giải quyết bài toán nghẽn cổ chai hạ tầng mạng và máy chủ trong các sự kiện thương mại điện tử có lượng truy cập tăng vọt (spike traffic). Nền tảng được xây dựng với Backend sử dụng ngôn ngữ Golang, kết hợp cùng kiến trúc Multi-AZ trên AWS. Hệ thống sử dụng cơ chế Auto Scaling để tự động mở rộng từ 2 lên hàng chục máy chủ EC2 khi tải tăng, Amazon ElastiCache để tối ưu truy xuất thông tin sản phẩm, và cơ sở dữ liệu Amazon RDS hoạt động theo cơ chế phân tách đọc/ghi. Nền tảng đảm bảo tính sẵn sàng cao (High Availability), độ trễ thấp và tối ưu chi phí vận hành.

### 2. Vấn đề hiện tại
Các hệ thống thương mại điện tử truyền thống thường sử dụng hạ tầng tĩnh (cố định số lượng máy chủ). Khi diễn ra sự kiện Flash Sale, lượng truy cập và yêu cầu mua hàng tăng đột biến trong vài phút, dẫn đến tình trạng cạn kiệt tài nguyên CPU/RAM, quá tải kết nối cơ sở dữ liệu và sập hệ thống. Khách hàng không thể truy cập, gây thiệt hại nghiêm trọng về doanh thu và uy tín.

### 3. Giải pháp & Hoàn vốn đầu tư (ROI)
*   **Giải pháp:** Nền tảng triển khai kiến trúc 3 lớp (3-Tier) trên AWS VPC. Giao thông mạng được phân phối bởi Application Load Balancer (ALB) đến nhóm Auto Scaling Group. Dữ liệu tĩnh và thông tin sản phẩm được đưa vào Amazon ElastiCache (Redis) để giảm tải cho cơ sở dữ liệu. Amazon RDS được thiết lập cấu hình Primary và Read Replica để tách biệt luồng ghi đơn hàng và luồng đọc sản phẩm. WAF và Secrets Manager được tích hợp để chống tấn công bằng bot và bảo mật thông tin.
*   **ROI:** Giải pháp mang lại mô hình chi phí Pay-as-you-go thực sự: doanh nghiệp chỉ trả tiền cho phần tài nguyên mở rộng trong đúng 1-2 giờ diễn ra Flash Sale. Tự động hóa hoàn toàn quy trình mở rộng giúp giảm tải công việc giám sát thủ công, đáp ứng hoàn hảo các tiêu chuẩn của môi trường Cloud Operation.

### 4. Kiến trúc giải pháp
Nền tảng áp dụng kiến trúc phân tán đa vùng (Multi-AZ) để quản lý luồng dữ liệu lớn. Yêu cầu của người dùng được kiểm duyệt qua WAF trước khi vào mạng riêng ảo (VPC). Khả năng tính toán được tự động mở rộng theo metric giám sát CPU. Dữ liệu được bảo vệ nghiêm ngặt ở các mạng nội bộ (Private Subnets).

![Flash Sale Architecture](/images/2-Proposal/flashsale_architecture.jpeg)

### 5. Dịch vụ AWS sử dụng
*   **Amazon EC2 & Auto Scaling:** Xử lý logic nghiệp vụ bằng Golang.
*   **Application Load Balancer (ALB):** Điều phối luồng truy cập.
*   **Amazon RDS:** Quản lý giao dịch, chia luồng Đọc/Ghi.
*   **Amazon ElastiCache:** Lưu cache dữ liệu sản phẩm.
*   **AWS WAF & CloudFront:** Phân phối nội dung và chặn Bot.
*   **AWS Secrets Manager:** Quản lý chuỗi kết nối.
*   **Amazon CloudWatch & SNS:** Giám sát và cảnh báo.
*   **NAT & Internet Gateway:** Quản lý định tuyến VPC.

### 6. Triển khai kỹ thuật
Dự án được chia thành 4 giai đoạn chính:
1.  **Thiết kế mạng & Bảo mật:** Cấu hình VPC, chia Public/Private Subnets, thiết lập Security Groups (Tuần 1-3).
2.  **Triển khai CSDL & Caching:** Triển khai RDS, ElastiCache, thiết lập Secrets Manager (Tuần 4-6).
3.  **Cấu hình Compute & Load Balancing:** Đưa mã nguồn lên EC2, thiết lập ALB và Auto Scaling Group (Tuần 7-9).
4.  **Kiểm thử & Tự động hóa:** Bắn request giả lập Flash Sale, cấu hình CloudWatch (Tuần 10-12).

**Yêu cầu kỹ thuật:** Hiểu biết về Subnetting (CIDR), tự động hóa EC2 bằng User Data, và sử dụng công cụ load-test (tối thiểu 5000 requests/second).

### 7. Lộ trình & Mốc triển khai
*   **Tháng 0:** Phân tích mã nguồn Golang, thiết kế sơ đồ kiến trúc.
*   **Tháng 1:** Triển khai khung mạng VPC, cấu hình WAF và Database.
*   **Tháng 2:** Tích hợp ElastiCache, triển khai EC2 và ALB.
*   **Tháng 3:** Cấu hình Auto Scaling, Load Testing và viết báo cáo.

### 8. Ước tính ngân sách
Quá trình thực hành chủ yếu tận dụng AWS Free Tier (EC2 t2.micro, RDS t3.micro). Chi phí ngoài Free Tier dự kiến:
*   **NAT Gateway:** ~0,045 USD/giờ.
*   **ALB:** ~0,0225 USD/giờ.
*   **AWS WAF:** ~5,00 USD/tháng.
*   **AWS Secrets Manager:** 0,40 USD/secret/tháng.
*   **Tổng ngân sách Lab:** Khoảng 15 USD - 20 USD/tháng (kiểm soát chặt chẽ bằng cách xóa tài nguyên sau khi Load Test).

### 9. Đánh giá rủi ro
*   **Rủi ro:** Lộ lọt dữ liệu bảo mật (Xác suất thấp nhờ Secrets Manager). Quá ngân sách do Auto Scaling (Xác suất cao nếu quên giới hạn Max).
*   **Giảm thiểu:** Áp dụng nguyên tắc quyền hạn tối thiểu. Đóng cổng SSH (22). Cài đặt giới hạn cứng (Max instance = 5) cho Auto Scaling. Thiết lập AWS Billing Alarm.

### 10. Kết quả kỳ vọng
Hệ thống phản hồi hàng ngàn yêu cầu đồng thời mà không bị treo. Xử lý triệt để bài toán thắt cổ chai nhờ việc tách luồng Đọc/Ghi cơ sở dữ liệu và lưu Cache. Xây dựng một Use-case thực tế có giá trị cao, thể hiện rõ tư duy thiết kế hệ thống và năng lực vận hành Cloud.