---
title: "Báo cáo Tuần 2"
date: 2026-05-01
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu Tuần 2:

* Nắm vững cách quản trị AWS CLI trực tiếp trên EC2 và tối ưu chi phí với Amazon Lightsail.
* Triển khai lưu trữ website tĩnh (S3), cơ sở dữ liệu quan hệ (RDS), thiết lập tự động co giãn (Auto Scaling), giám sát hệ thống (CloudWatch) và phân giải tên miền (Route 53).

### Công việc đã thực hiện:

| Thứ | Công việc đã làm | Ngày BĐ | Ngày HT | Tài liệu tham khảo |
| :--- | :--- | :--- | :--- | :--- |
| **Hai** | **Storage & Compute Optimization:**<br>- Thực hành cấu hình và lưu trữ trang web tĩnh trên Amazon S3 (Hosting static website with Amazon S3).<br>- Tìm hiểu và triển khai máy chủ ảo tối ưu chi phí cho dự án nhỏ với Amazon Lightsail. | 27/04/2026 | 27/04/2026 | [Link 1](https://000057.awsstudygroup.com/)<br>[Link 2](https://000045.awsstudygroup.com/) |
| **Ba** | **CLI & Automation on EC2:**<br>- Cài đặt và thao tác với AWS CLI trực tiếp trên máy chủ Amazon EC2 (Windows/Ubuntu) (Using AWS CLI on Amazon EC2).<br>- Áp dụng IAM Role cho EC2 để thực thi các lệnh CLI an toàn mà không cần cấu hình Access Key cứng. | 28/04/2026 | 28/04/2026 | [Link 1](https://000011.awsstudygroup.com/) |
| **Tư** | **Managed Database Services:**<br>- Khởi tạo và cấu hình cơ sở dữ liệu quan hệ có độ sẵn sàng cao trên Amazon RDS (Create a database on Amazon RDS).<br>- Thiết lập kết nối mạng nội bộ an toàn (Security Groups) từ máy chủ EC2 vào RDS. | 29/04/2026 | 29/04/2026 | [Link 1](https://000005.awsstudygroup.com/) |
| **Năm** | **Auto Scaling & Monitoring:**<br>- Thiết lập hệ thống giám sát tài nguyên với Amazon CloudWatch (Create System Monitor with Amazon Cloudwatch).<br>- Cấu hình nhóm tự động co giãn máy chủ dựa trên số liệu giám sát (Automate Application Scaling with Amazon EC2 Autoscaling). | 30/04/2026 | 30/04/2026 | [Link 1](https://000008.awsstudygroup.com/)<br>[Link 2](https://000006.awsstudygroup.com/) |
| **Sáu** | **Advanced Networking (DNS):**<br>- Thiết lập hệ thống phân giải tên miền (DNS) lai tích hợp giữa môi trường Local (On-premise) và Amazon VPC bằng Amazon Route53 (Set up an integrated hybrid DNS system with Amazon Route53). | 01/05/2026 | 01/05/2026 | [Link 1](https://000010.awsstudygroup.com/) |

### Kết quả đạt được:

* **Lưu trữ tĩnh & Quản trị máy chủ:** Cấu hình thành thạo AWS CLI ngay bên trong hệ điều hành của EC2 (Windows/Ubuntu). Nắm vững cơ chế quyền (Bucket Policy) để public một trang web tĩnh host trên Amazon S3 và hiểu cách tối ưu chi phí điện toán bằng Lightsail.
* **Cơ sở dữ liệu đám mây:** Tự tay khởi tạo thành công Amazon RDS, giải quyết được bài toán kết nối bảo mật nội bộ giữa backend (EC2) và database (RDS) mà không đưa database ra ngoài public internet.
* **Tự động hóa & Giám sát:** Vận dụng thành công sự kết hợp giữa CloudWatch (giám sát metric, tạo cảnh báo) và EC2 Auto Scaling. Hệ thống đã có khả năng tự động "đẻ" thêm máy chủ khi tải cao và xóa bớt đi khi tải thấp.
* **Kiến trúc mạng DNS:** Hiểu rõ cách cấu hình Route 53, thiết lập các Hosted Zones và giải quyết bài toán giao tiếp lai (Hybrid DNS) giữa hạ tầng Local và môi trường VPC trên Cloud.