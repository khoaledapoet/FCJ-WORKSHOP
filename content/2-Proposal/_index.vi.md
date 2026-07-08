---
title : "Đề xuất dự án "
date : 2026-07-07
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

#### 1. Tóm tắt dự án
Dự án PawVerse được thiết kế nhằm giải quyết bài toán về hiệu suất mạng và bảo mật hạ tầng cho một nền tảng thương mại điện tử chuyên cung cấp sản phẩm thú cưng. Hệ thống được xây dựng với kiến trúc Multi-AZ trên AWS, kết hợp các quy chuẩn quản trị mạng chặt chẽ. Nền tảng ứng dụng Auto Scaling để tự động mở rộng cụm máy chủ EC2 khi lưu lượng truy cập tăng đột biến, tích hợp Amazon ElastiCache để tối ưu truy xuất thông tin sản phẩm và phân tách luồng dữ liệu bảo mật trong Private Subnet. PawVerse đảm bảo High Availability (Tính sẵn sàng cao), độ trễ thấp và tối ưu hóa chi phí vận hành.

#### 2. Vấn đề hiện tại
Các nền tảng e-commerce cơ bản thường triển khai hạ tầng tĩnh và lưu trữ mã nguồn chung với thông tin bảo mật (hard-code credentials). Khi có các đợt khuyến mãi, lượng truy cập tăng vọt gây cạn kiệt tài nguyên CPU/RAM và quá tải kết nối cơ sở dữ liệu. Đồng thời, việc thiếu vắng mạng phân phối nội dung (CDN) và tường lửa lớp ứng dụng khiến trang web tải chậm ở nhiều khu vực và dễ trở thành mục tiêu của các cuộc tấn công DDoS hoặc botnet, gây thiệt hại nghiêm trọng về doanh thu.

#### 3. Giải pháp & Tỷ suất hoàn vốn
**Giải pháp:** Nền tảng triển khai kiến trúc 3-Tier trên AWS VPC. Lưu lượng truy cập được phân phối bởi Application Load Balancer (ALB) đến Auto Scaling Group. Nội dung tĩnh được phân phối toàn cầu qua CloudFront, trong khi dữ liệu sản phẩm được lưu đệm tại Amazon ElastiCache (Redis) để giảm tải cơ sở dữ liệu. Amazon RDS đóng vai trò lưu trữ lõi. Đặc biệt, AWS WAF và Secrets Manager được tích hợp sâu để chặn luồng truy cập độc hại và quản lý hoàn toàn tự động các chuỗi kết nối (connection strings).
**ROI:** Giải pháp mang lại mô hình chi phí Pay-as-you-go đích thực: chỉ trả tiền cho tài nguyên sinh thêm vào thời điểm tải cao. Việc tự động hóa giám sát và ẩn giấu thông tin bảo mật giúp giảm thiểu tối đa rủi ro vận hành, đáp ứng hoàn hảo các tiêu chuẩn khắt khe nhất của môi trường Enterprise Cloud Operations.

#### 4. Solution Architecture (Kiến trúc giải pháp)
Hệ thống áp dụng kiến trúc phân tán Multi-AZ. Yêu cầu của người dùng trước tiên được kiểm duyệt qua WAF và tăng tốc bởi CloudFront. Các luồng gọi API đi qua Internet Gateway để vào Virtual Private Cloud (VPC), sau đó được ALB điều hướng. Năng lực xử lý (Compute) tự động mở rộng dựa trên các chỉ số giám sát từ CloudWatch. Toàn bộ máy chủ và dữ liệu lõi được bảo vệ nghiêm ngặt bên trong Private Subnet, giao tiếp nội bộ qua VPC Endpoint và kết nối ra ngoài qua NAT Gateway.

![diagram](/images/2-Proposal/diagram.png)

#### 5. Các dịch vụ AWS sử dụng
+ **Amazon EC2 & Auto Scaling:** Xử lý logic ứng dụng và tự động co giãn.
+ **Application Load Balancer (ALB):** Phân phối lưu lượng truy cập động.
+ **Amazon RDS:** Quản lý cơ sở dữ liệu quan hệ lõi.
+ **Amazon ElastiCache:** Lưu trữ bộ đệm dữ liệu sản phẩm.
+ **AWS WAF & CloudFront:** Phân phối nội dung toàn cầu và chặn tấn công.
+ **Amazon S3:** Lưu trữ tĩnh mã nguồn giao diện (Frontend).
+ **AWS Secrets Manager & KMS:** Quản lý và mã hóa mật khẩu tự động.
+ **Amazon CloudWatch, CloudTrail & SNS:** Giám sát, kiểm toán và cảnh báo hệ thống.
+ **VPC, NAT & Internet Gateway:** Quản trị phân luồng mạng và Subnet.

#### 6. Triển khai kỹ thuật
Dự án được chia làm 4 giai đoạn chính:
+ **Network & Security Design:** Cấu hình VPC, phân vùng Public/Private Subnets, thiết lập Security Groups và VPC Endpoint.
+ **DB & Caching Deployment:** Khởi tạo Amazon RDS, ElastiCache và thiết lập két sắt AWS Secrets Manager.
+ **Compute & Load Balancing Config:** Thiết lập EC2 Launch Template (tích hợp User Data tự động hóa giải mã Secrets), cấu hình ALB và Auto Scaling.
+ **Edge Layer & Monitoring:** Triển khai S3, CloudFront (kèm OAC), kích hoạt WAF, thiết lập giám sát CloudWatch và cảnh báo SNS.

#### 7. Lộ trình & Cột mốc
+ **Tháng 1:** Phân tích yêu cầu, thiết kế sơ đồ kiến trúc tổng thể và triển khai mạng lưới VPC cốt lõi.
+ **Tháng 2:** Khởi tạo tầng cơ sở dữ liệu, bộ đệm bảo mật và triển khai cụm EC2 cùng bộ cân bằng tải ALB.
+ **Tháng 3:** Cấu hình CDN toàn cầu (CloudFront), tường lửa WAF và thiết lập hệ thống Auto Scaling.
+ **Tháng 4:** Kiểm thử sức chịu tải (Load Testing), kiểm toán bảo mật và viết báo cáo nghiệm thu kỹ thuật.

#### 8. Ước tính ngân sách
Quá trình thực hành tối đa hóa việc sử dụng tài nguyên AWS Free Tier. Chi phí ước tính cho các dịch vụ ngoài Free Tier:
+ **NAT Gateway:** ~0.045 USD/giờ.
+ **Application Load Balancer:** ~0.0225 USD/giờ.
+ **AWS WAF:** ~5.00 USD/tháng.
+ **AWS Secrets Manager:** ~0.40 USD/secret/tháng.
**Tổng ngân sách Lab:** Khoảng 10 - 15 USD (Được kiểm soát nghiêm ngặt bằng việc xóa tài nguyên lập tức sau khi Demo và Testing).

#### 9. Đánh giá rủi ro
+ **Rủi ro:** Lỗ hổng giao tiếp mạng khiến các thành phần không thể kết nối (Cao); Vượt quá ngân sách do Auto Scaling tự động mở rộng ngoài tầm kiểm soát (Trung bình).
+ **Khắc phục:** Áp dụng nguyên tắc Đặc quyền tối thiểu (Least Privilege) cho IAM Role và Security Groups. Chặn toàn bộ cổng SSH (22) từ bên ngoài. Thiết lập giới hạn cứng (Max capacity) cho Auto Scaling Group và cài đặt AWS Billing Alarm qua Email.

#### 10. Kết quả mong đợi
Hệ thống xử lý mượt mà hàng ngàn yêu cầu đồng thời mà không bị sập. Khắc phục triệt để rào cản bảo mật bằng cách không hard-code bất kỳ mật khẩu nào vào mã nguồn. Trình bày được một Use-case thực tiễn có giá trị cao, thể hiện rõ tư duy thiết kế hệ thống, quản trị mạng lưới và khả năng vận hành Cloud chuyên nghiệp.