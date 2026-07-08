---
title: "Báo cáo Tuần 4"
date: 2026-05-17
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:
* Nắm vững tự động hóa và quản trị tài nguyên thông qua AWS Systems Manager và Infrastructure as Code (CloudFormation).
* Thiết lập rào cản bảo mật nghiêm ngặt cho hệ thống (IAM Boundary, WAF, KMS, Security Hub, SSO).
* Xây dựng kiến trúc liên kết mạng linh hoạt (Transit Gateway, VPC Peering) và kế hoạch dự phòng đạt chuẩn AWS Backup.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Resource Governance:**<br>- Quản lý tài nguyên theo nhóm thông qua Tag và Resource Groups.<br>- Quản lý quyền truy cập dịch vụ EC2 bằng Tag thông qua IAM. | 11/05/2026 | 11/05/2026 | [Tham khảo 1](https://000027.awsstudygroup.com/)<br>[Tham khảo 2](https://000028.awsstudygroup.com/) |
| **Ba** | **Management & Automation:**<br>- Quản lý dịch vụ và tự động hóa tác vụ bằng AWS Systems Manager.<br>- Làm việc với AWS Systems Manager - Session Manager.<br>- Khởi tạo Infrastructure as Code với AWS CloudFormation. | 12/05/2026 | 12/05/2026 | [Tham khảo 1](https://000031.awsstudygroup.com/)<br>[Tham khảo 2](https://000058.awsstudygroup.com/)<br>[Tham khảo 3](https://000037.awsstudygroup.com/) |
| **Tư** | **Identity Security:**<br>- Giới hạn quyền người dùng với IAM Permission Boundary.<br>- Giới hạn điều kiện chuyển đổi quyền (Limiting Role Transfer). | 13/05/2026 | 13/05/2026 | [Tham khảo 1](https://000030.awsstudygroup.com/)<br>[Tham khảo 2](https://000044.awsstudygroup.com/) |
| **Năm** | **Advanced Security:**<br>- Đánh giá bảo mật tự động bằng AWS Security Hub.<br>- Bảo vệ ứng dụng web và API với AWS WAF.<br>- Quản lý khóa mã hóa bằng AWS KMS. | 14/05/2026 | 14/05/2026 | [Tham khảo 1](https://000018.awsstudygroup.com/)<br>[Tham khảo 2](https://000026.awsstudygroup.com/)<br>[Tham khảo 3](https://000033.awsstudygroup.com/) |
| **Sáu** | **Reliability & Networking:**<br>- Triển khai kế hoạch sao lưu toàn hệ thống với AWS Backup.<br>- Liên kết các mạng ảo thông qua VPC Peering.<br>- Quản lý kết nối mạng tập trung bằng AWS Transit Gateway. | 15/05/2026 | 15/05/2026 | [Tham khảo 1](https://000013.awsstudygroup.com/)<br>[Tham khảo 2](https://000019.awsstudygroup.com/)<br>[Tham khảo 3](https://000020.awsstudygroup.com/) |

### Kết quả đạt được:
* **Quản trị tự động hóa (IaC):** Thành thạo AWS CloudFormation để khởi tạo hạ tầng. Sử dụng Session Manager để kết nối an toàn vào hệ thống.
* **Bảo mật và Phân quyền (Security):** Thiết lập giới hạn quyền lực bằng IAM Boundary và SSO. Tự bảo vệ ứng dụng bằng AWS WAF và quản lý mã hóa dữ liệu với KMS.
* **Tính khả dụng và Sao lưu (Reliability):** Triển khai thành công kế hoạch sao lưu tự động với AWS Backup, đảm bảo khả năng phục hồi dữ liệu.
* **Kiến trúc mạng (Networking):** Xây dựng liên kết mạng phức tạp, kết nối chéo thông qua VPC Peering và tập trung định tuyến qua Transit Gateway.