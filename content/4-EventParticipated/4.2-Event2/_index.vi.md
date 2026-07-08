---
title: "Event 2"
date: 2026-07-08
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch “Mini Meetup 06/06”

### Mục Đích Của Sự Kiện
- Cập nhật các công nghệ lõi về ảo hóa (Containerization) và kiến trúc dữ liệu đồ thị (Graph Database).
- Phân tích sự kết hợp giữa Bảo mật đám mây và Machine Learning trong việc phát hiện xâm nhập.
- Chia sẻ kinh nghiệm thực chiến về lộ trình thăng tiến trong ngành IT và các kỹ năng làm việc nhóm hiệu quả.
- Mở rộng kiến thức về lập trình mạng (Networking) thông qua ứng dụng giao thức WebSocket.

### Danh Sách Diễn Giả
- **Bảo Huỳnh** - Chủ đề: Docker - A containerization technology
- **Lê Hoàng Gia Đại** - Chủ đề: Combining AWS WAF with Machine Learning for Cyber Attack Detection on AWS
- **Việt Phát** - Chủ đề: AWS Neptune for Building a Graph Knowledge Base for GraphRAG
- **Nguyễn Quốc Bảo** - Chủ đề: Godot WebSocket
- **Vinh Trần** - Chủ đề: Từ IT Helpdesk lên Senior Sysadmin: Hành trình tự học và Lộ trình dịch chuyển sang Cloud/DevOps
- **Trương Phước** - Chủ đề: Cách làm việc nhóm hiệu quả

### Nội Dung Nổi Bật

#### Hạ Tầng Khởi Tạo & Đám Mây (Cloud & Infrastructure)
- **Công nghệ Docker (Diễn giả Bảo Huỳnh):** Làm rõ khái niệm Containerization, cách đóng gói ứng dụng với các thư viện phụ thuộc để giải quyết triệt để vấn đề "chạy được trên máy tôi nhưng lỗi trên máy server".
- **Lập trình mạng (Diễn giả Nguyễn Quốc Bảo):** Khám phá giao thức WebSocket trong Godot, cách thiết lập kết nối hai chiều liên tục (full-duplex) với độ trễ thấp, ứng dụng mạnh mẽ cho các hệ thống thời gian thực.

#### AI & Bảo Mật Nâng Cao (AI & Advanced Security)
- **Phòng chống Tấn công mạng (Diễn giả Lê Hoàng Gia Đại):** Giải pháp đột phá khi kết hợp tường lửa AWS WAF với các mô hình Machine Learning. Mô hình học máy giúp phân tích hành vi bất thường, từ đó tự động chặn các cuộc tấn công Zero-day hiệu quả hơn nhiều so với việc chỉ dùng tập luật (rule-based) tĩnh.
- **Cơ sở dữ liệu Đồ thị (Diễn giả Việt Phát):** Giới thiệu AWS Neptune và kiến trúc GraphRAG. Phương pháp sử dụng cơ sở dữ liệu đồ thị để xây dựng kho tri thức (Knowledge Base) giúp các mô hình AI truy xuất thông tin phức tạp và có tính liên kết cao một cách chính xác.

#### Định Hướng Nghề Nghiệp & Kỹ Năng Mềm
- **Lộ trình Cloud/DevOps (Diễn giả Vinh Trần):** Câu chuyện truyền cảm hứng và bản đồ chỉ đường (Roadmap) thực tế để chuyển mình từ một IT Helpdesk tiến lên vị trí Senior Sysadmin và kỹ sư Cloud/DevOps.
- **Kỹ năng Làm việc nhóm (Diễn giả Trương Phước):** Các phương pháp giao tiếp, giải quyết xung đột và quản lý công việc chéo để tối ưu hóa năng suất khi làm việc trong các team dự án công nghệ.

### Những Gì Học Được

#### Tư Duy Thiết Kế & Kỹ Thuật
- **Container-first:** Nhận thức rõ ràng việc phải luôn đóng gói ứng dụng (Dockerize) ngay từ đầu để đảm bảo tính nhất quán giữa các môi trường (Dev, Staging, Production).
- **Proactive Security:** Chuyển đổi từ tư duy bảo mật phòng ngự thụ động sang chủ động bằng cách ứng dụng Machine Learning vào WAF để phân tích và dự đoán mối đe dọa.
- **Graph-based Thinking:** Hiểu được cách tổ chức dữ liệu theo dạng đồ thị (Nodes và Edges) thay vì dạng bảng truyền thống, tối ưu cực tốt cho các tác vụ AI phân tích mối quan hệ dữ liệu.

#### Phát Triển Bản Thân
- Nắm bắt được lộ trình học tập rõ ràng để tiến sâu vào mảng Cloud Operations và DevOps.
- Hiểu được tầm quan trọng của các "Soft skills" như giao tiếp và quy trình làm việc nhóm (Agile/Scrum), những yếu tố quyết định thành bại của một dự án thực tế.

### Ứng Dụng Vào Công Việc
- **Triển khai hạ tầng PawVerse:** Ứng dụng ngay kiến thức Docker của anh Bảo Huỳnh để viết kịch bản User Data tự động cài đặt và chạy Container trên các máy chủ EC2 (Week 5 & Week 10).
- **Thiết lập Tường lửa:** Vận dụng nguyên lý hoạt động của AWS WAF (từ phần chia sẻ của anh Đại) để cấu hình lớp rào chắn bảo mật Tầng Biên cho hệ thống kết hợp với CloudFront.
- **Giao tiếp trong Team:** Chủ động áp dụng kỹ năng làm việc nhóm để trao đổi rõ ràng, báo cáo tiến độ minh bạch với các mentor (anh Nguyễn Gia Hưng) trong suốt kỳ thực tập.

### Trải nghiệm trong event

Tham gia buổi **FCAJ Tech Sharing** mang lại cho tôi những kiến thức vô cùng đa chiều. Khác với các buổi học thuần lý thuyết, đây là diễn đàn của những kinh nghiệm đúc kết từ máu và nước mắt.

#### Học hỏi từ các diễn giả có chuyên môn cao
- Các chủ đề được lựa chọn vô cùng sát với thực tế công việc hiện nay. Từ hạ tầng cốt lõi (Docker) đến bảo mật tiên tiến (WAF + ML), các diễn giả đã bóc tách vấn đề phức tạp thành những khái niệm dễ tiếp thu.

#### Trải nghiệm kỹ thuật thực tế
- Được nghe câu chuyện thực chiến của anh Vinh Trần là một liều thuốc tinh thần rất lớn. Nó giúp tôi, một sinh viên sắp tốt nghiệp, nhìn thấy rõ con đường mình cần đi, những chứng chỉ cần học và những kỹ năng thực tế cần trau dồi để trở thành một Kỹ sư Hệ thống thực thụ.

#### Bài học rút ra
- Công nghệ thay đổi từng ngày, những hệ thống hiện đại không chỉ đòi hỏi kiến thức mạng máy tính đơn thuần mà còn phải tích hợp AI, Machine Learning để tăng cường bảo mật. Hơn thế nữa, kỹ năng làm việc nhóm và thái độ học hỏi liên tục chính là chìa khóa để tiến xa trong ngành.

#### Một số hình ảnh khi tham gia sự kiện
*(Thêm các hình ảnh chụp màn hình buổi thuyết trình hoặc ảnh check-in tại đây)*

> Buổi Tech Sharing không chỉ trang bị thêm cho tôi những "vũ khí" kỹ thuật sắc bén mà còn định hướng rõ ràng con đường phát triển sự nghiệp trong hệ sinh thái Cloud/DevOps.