---
title: "Báo cáo Tuần 4"
date: 2026-05-16
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:

* Nắm vững kỹ năng tự động hóa và quản trị tài nguyên thông qua AWS Systems Manager và Infrastructure as Code (CloudFormation).
* Thiết lập các rào cản bảo mật nghiêm ngặt cho hệ thống (IAM Boundary, WAF, KMS, Security Hub).
* Xây dựng kiến trúc liên kết mạng linh hoạt (Transit Gateway, VPC Peering) và lập kế hoạch dự phòng đạt chuẩn độ tin cậy cao (AWS Backup).

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Resource Governance:**<br>- Quản lý tài nguyên theo nhóm thông qua Tag và Resource Groups.<br>- Thiết lập kiểm soát quyền truy cập dịch vụ EC2 bằng Tag kết hợp với IAM. | 11/05/2026 | 11/05/2026 | AWS Study Group |
| **Ba** | **Management & Automation:**<br>- Quản lý dịch vụ và tự động hóa tác vụ bằng AWS Systems Manager.<br>- Kết nối máy chủ an toàn không cần SSH key qua Systems Manager - Session Manager.<br>- Khởi tạo hạ tầng bằng mã (Infrastructure as Code) với AWS CloudFormation. | 12/05/2026 | 12/05/2026 | AWS Study Group |
| **Tư** | **Identity Security:**<br>- Cài đặt đăng nhập một lần (Single Sign-On / IAM Identity Center) cho toàn tổ chức.<br>- Giới hạn quyền người dùng nâng cao bằng IAM Permission Boundary.<br>- Giới hạn điều kiện chuyển đổi quyền (Limiting Role Transfer by Condition). | 13/05/2026 | 13/05/2026 | AWS Study Group |
| **Năm** | **Advanced Security:**<br>- Quản lý vòng đời khóa mã hóa bằng dịch vụ Key Management Service (AWS KMS).<br>- Bảo vệ ứng dụng web và API khỏi các cuộc tấn công thông dụng bằng Web Application Firewall (AWS WAF).<br>- Đánh giá tự động các tiêu chuẩn bảo mật hệ thống với AWS Security Hub. | 14/05/2026 | 14/05/2026 | AWS Study Group |
| **Sáu** | **System Reliability:**<br>- Tìm hiểu chiến lược bảo vệ dữ liệu trên môi trường đám mây.<br>- Triển khai tự động hóa kế hoạch sao lưu toàn hệ thống với dịch vụ AWS Backup. | 15/05/2026 | 15/05/2026 | AWS Study Group |
| **Bảy** | **Advanced Networking:**<br>- Liên kết giao tiếp giữa các mạng ảo (VPCs) thông qua VPC Peering.<br>- Đơn giản hóa và quản lý kết nối mạng tập trung quy mô lớn bằng AWS Transit Gateway. | 16/05/2026 | 16/05/2026 | AWS Study Group |

### Kết quả đạt được:

* **Quản trị tự động hóa (IaC):** Thành thạo việc không sử dụng giao diện web mà dùng CloudFormation để tự động hóa khởi tạo hạ tầng. Kết hợp Systems Manager (Session Manager) để kết nối máy chủ an toàn mà không cần mở cổng 22 hay dùng SSH key.
* **Bảo mật và Phân quyền (Security):** Hiểu rõ tư duy bảo mật nhiều lớp. Nắm vững cách thiết lập giới hạn quyền lực tối đa bằng IAM Permission Boundary và SSO. Có khả năng tự bảo vệ ứng dụng thực tế bằng tường lửa WAF và mã hóa dữ liệu với KMS.
* **Tính khả dụng và Sao lưu (Reliability):** Vận dụng tính năng thiết lập lịch trình sao lưu tự động của AWS Backup, đảm bảo hệ thống có thể khôi phục lại (Disaster Recovery) khi có sự cố dữ liệu.
* **Kiến trúc mạng diện rộng (Networking):** Thay vì các thiết kế rời rạc, đã có thể xây dựng các liên kết mạng phức tạp, kết nối chéo giữa nhiều VPC thông qua VPC Peering và tập trung hóa routing thông qua Transit Gateway – một kỹ năng nâng cao rất được săn đón.