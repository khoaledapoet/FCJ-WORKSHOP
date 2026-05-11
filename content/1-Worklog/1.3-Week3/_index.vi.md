---
title: "Báo cáo Tuần 3"
date: 2026-05-08
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

* Tích hợp trợ lý AI (AWS Kiro) vào quy trình phát triển.
* Quản lý, phân bổ và tối ưu hóa chi phí AWS kết hợp với việc đánh dấu tài nguyên (Tag/Resource Groups).
* Thực hành di dời hạ tầng (VM & Database), thiết lập giám sát trực quan với Grafana và tự động hóa quy trình tắt/mở máy chủ.

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Generative AI for Builders:**<br>- Tìm hiểu tác động của Gen AI (AWS Kiro) tới SDLC và phương pháp Spec-driven development.<br>- Làm quen với Kiro IDE, Kiro CLI và hệ sinh thái Kiro Power. | 04/05/2026 | 04/05/2026 | Module 01-03 Gen AI on AWS - Kiro |
| **Ba** | **Cost Optimization & Resource Management:**<br>- Nghiên cứu các chiến lược tối ưu chi phí: Right-sizing, Spot Instances, Reserved/Savings Plans.<br>- Thực hành: Quản lý tài nguyên tập trung và phân bổ chi phí bằng cách sử dụng Tag và Resource Groups. | 05/05/2026 | 05/05/2026 | Module 01-04 Cost optimization on AWS |
| **Tư** | **Infrastructure & Database Migration:**<br>- Di dời máy chủ ảo từ môi trường cục bộ lên đám mây (Migrate virtual servers with AWS VM Import/Export).<br>- Chuyển đổi lược đồ và di dời cơ sở dữ liệu (Database Migration with AWS DMS and SCT). | 06/05/2026 | 06/05/2026 | [Link 1](https://000014.awsstudygroup.com/)<br>[Link 2](https://000043.awsstudygroup.com/) |
| **Năm** | **Advanced System Monitoring:**<br>- Tích hợp dữ liệu CloudWatch vào Grafana để xây dựng bảng điều khiển trực quan.<br>- Thiết lập theo dõi sức khỏe hệ thống theo thời gian thực (Create System Monitor with Amazon Cloudwatch and Grafana). | 07/05/2026 | 07/05/2026 | [Link 1](https://000029.awsstudygroup.com/) |
| **Sáu** | **Cost Optimization via Automation:**<br>- Ứng dụng bài học tối ưu chi phí vào thực tế bằng cách viết hàm tự động tắt máy chủ ngoài giờ làm việc.<br>- Thiết lập cảnh báo và thông báo trạng thái qua Slack (Automated server shutdown and Slack messaging with AWS Lambda). | 08/05/2026 | 08/05/2026 | [Link 1](https://000022.awsstudygroup.com/) |

### Kết quả đạt được:

* **Tích hợp Gen AI:** Hiểu rõ khả năng của AWS Kiro trong việc hỗ trợ viết code, tự động hóa tác vụ CI/CD qua terminal và xây dựng ứng dụng dựa trên đặc tả (Spec).
* **Quản trị & Tối ưu Chi phí:** Áp dụng hiệu quả kiến thức lý thuyết về FinOps (giảm lãng phí tài nguyên) vào thực tiễn. Vận dụng kỹ thuật Tagging để tổ chức lại tài nguyên, giúp việc đo lường chi phí trên AWS Budgets chính xác đến từng dự án/phòng ban.
* **Migration:** Nắm vững quy trình đóng gói máy chủ ảo nội bộ và import thành công lên Amazon EC2. Cấu hình thành công AWS DMS và SCT để đảm bảo dữ liệu toàn vẹn khi chuyển đổi database.
* **Tự động hóa & Giám sát trực quan:** Vượt qua giới hạn của CloudWatch Dashboard bằng cách tích hợp Grafana. Lập trình thành công AWS Lambda kết hợp Webhook để tự động tắt hệ thống EC2 tiết kiệm tiền và báo cáo trực tiếp về ứng dụng chat Slack.