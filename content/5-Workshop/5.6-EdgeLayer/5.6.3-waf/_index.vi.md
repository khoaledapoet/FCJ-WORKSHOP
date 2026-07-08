---
title : "Tường lửa Web (WAF)"
date : 2026-07-07
weight : 3
chapter : false
pre : " <b> 5.6.3. </b> "
---

#### Bảo vệ chủ động với AWS WAF
Để đối phó với các đòn tấn công mạng nhằm vào lỗ hổng phần mềm, chúng ta tận dụng tính năng bảo mật tích hợp sẵn (1-click Security) của CloudFront để tự động sinh ra một hệ thống Tường lửa ứng dụng web (WAF).

1. Truy cập dịch vụ **AWS WAF & Shield**, chọn **Web ACLs** và tìm đến Web ACL vừa được CloudFront tự động khởi tạo (Tiền tố `CreatedByCloudFront-...`).
2. Mặc định, AWS đã cung cấp sẵn các tập luật hữu ích như chặn IP xấu (IP Reputation) và chặn input độc hại. Tuy nhiên, để bảo vệ triệt để cho con cơ sở dữ liệu RDS bên dưới, chúng ta cần bổ sung thêm luật chống SQL Injection.
3. Trong giao diện chi tiết của WAF, chọn **Add rule** ---> **Add managed rule groups**.
4. Mở rộng mục **AWS managed rule groups**, bật thêm tập luật **SQL database** (Phân tích và triệt tiêu các mã độc cố tình chèn chuỗi tấn công cơ sở dữ liệu).

![Tập luật WAF Rules](/images/5-Workshop/5.6-EdgeLayer/waf-rules.png)
*Hình 5.6.3.1: Các tập luật bảo mật (Managed Rules) được tinh chỉnh, bổ sung thêm lá chắn SQL Injection để bảo vệ Database lõi.*

5. Nhấn Save để áp dụng cấu hình. Hệ thống tường lửa ngay lập tức được phủ lên tầng Biên toàn cầu, biến kiến trúc PawVerse thành một pháo đài vững chắc chặn đứng mọi gói tin chứa mã độc từ ngoài rìa biên giới.