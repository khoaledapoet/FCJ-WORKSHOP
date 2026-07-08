---
title: "Event 1"
date: 2026-07-08
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “FCAJ Community Day - Conference Call”

### Mục Đích Của Sự Kiện
- Chia sẻ kiến thức chuyên sâu về điện toán đám mây và Trí tuệ nhân tạo (AI/GenAI) từ các chuyên gia hàng đầu.
- Hướng dẫn xây dựng hệ thống quản lý kiến thức (Second Brain) và phân tích dữ liệu thông minh.
- Phân tích kỹ thuật về mạng phân phối nội dung (CloudFront) và cơ chế hoạt động của Mô hình ngôn ngữ lớn (LLM).
- Giao lưu và học hỏi kinh nghiệm thực chiến từ cuộc thi Hackathon của đội ngũ kỹ sư ngân hàng VIB.

### Danh Sách Diễn Giả
- **Anh Tịnh** - Chủ đề: Build second brain
- **Hải Anh** - Chủ đề: Friendly AI Assistant with Amazon QuickSight
- **Thịnh** - Chủ đề: From Edge To Origin: CloudFront as Your Foundation
- **Team VIB** - Chủ đề: 36 hrs with LotusHacks – Building UTMorpho from ideal to Reality
- **Đào Đức** - Chủ đề: Deep dive talk: How LLM actually works?
- **Cát Vy** - Chủ đề: Enterprise-Grade Multi-Agent System

### Nội Dung Nổi Bật

#### Kiến trúc Cloud & Phân phối nội dung
- **Từ Edge đến Origin (Diễn giả Thịnh):** Phân tích sâu về nền tảng mạng phân phối nội dung AWS CloudFront. Hiểu rõ đường đi của gói tin từ Tầng Biên (Edge Location) về đến máy chủ gốc (Origin), cách tối ưu bộ nhớ đệm (Caching) và bảo mật đường truyền.
- **Quản lý kiến thức (Diễn giả Anh Tịnh):** Phương pháp xây dựng "Bộ não thứ hai" (Second Brain) để tổ chức và lưu trữ kiến thức công nghệ một cách có hệ thống.

#### AI, LLM & Hệ thống Đa tác vụ (Multi-Agent)
- **Bản chất của LLM (Diễn giả Đào Đức):** Phân tích chuyên sâu (Deep dive) về cách các Mô hình ngôn ngữ lớn hoạt động "dưới nắp capo", giải mã sự bất định và cách thiết lập tham số kiểm soát AI.
- **Enterprise-Grade Multi-Agent (Diễn giả Cát Vy):** Kiến trúc xây dựng hệ thống đa tác vụ AI (Multi-Agent) cấp độ doanh nghiệp, nơi nhiều AI model phối hợp xử lý các quy trình phức tạp.
- **Trợ lý AI với QuickSight (Diễn giả Hải Anh):** Ứng dụng AI tích hợp vào Amazon QuickSight để phân tích dữ liệu kinh doanh và tạo biểu đồ trực quan một cách thân thiện.

#### Case Study Thực Chiến
- **36 giờ với LotusHacks (Team VIB):** Đội ngũ kỹ sư VIB chia sẻ kinh nghiệm thực tế khi tham gia cuộc thi hackathon, cách xây dựng giải pháp thần tốc dưới áp lực thời gian và các tiêu chuẩn khắt khe của hệ thống tài chính.

### Những Gì Học Được

#### Tư Duy Thiết Kế
- **Tối ưu hóa Tầng Biên:** Nắm vững triết lý đưa dữ liệu và bảo mật ra sát người dùng nhất có thể (Edge-optimized) thông qua CloudFront, thay vì dồn toàn bộ tải về máy chủ lõi.
- **Tư duy tích hợp AI:** Thay vì dùng AI một cách đơn lẻ, tôi học được tư duy hệ thống hóa qua kiến trúc Multi-Agent, để các luồng AI tự động giao tiếp và giải quyết bài toán lớn.

#### Kiến Trúc Kỹ Thuật
- **Data Analytics & BI:** Hiểu được sức mạnh của Amazon QuickSight khi kết hợp với AI, cho phép truy vấn dữ liệu bằng ngôn ngữ tự nhiên thay vì viết SQL phức tạp.
- **Cơ chế hoạt động của AI/LLM:** Nắm được bản chất toán học và xác suất của LLM, từ đó biết cách tinh chỉnh (tuning) các prompt hiệu quả và giảm thiểu ảo giác (hallucination).

### Ứng Dụng Vào Công Việc
- **Tối ưu hóa kiến trúc PawVerse:** Ứng dụng trực tiếp kiến thức từ bài trình bày của diễn giả Thịnh để cấu hình AWS CloudFront cho Tầng Biên của dự án, giải quyết triệt để lỗi CORS và tăng tốc độ tải trang tĩnh từ S3.
- **Tổ chức tài liệu dự án:** Áp dụng phương pháp "Second Brain" của diễn giả Anh Tịnh để hệ thống hóa toàn bộ source code, kiến trúc và tài liệu Workshop một cách khoa học.
- **Ứng dụng AI vào vận hành:** Dùng hiểu biết về LLM (từ phần chia sẻ của anh Đào Đức) để kiểm soát và ra lệnh chính xác cho trợ lý AWS Kiro trong việc viết các script tự động hóa hạ tầng.

### Trải nghiệm trong event

Tham gia **AWS Vietnam Community Day** là một trải nghiệm tuyệt vời, giúp tôi kết nối với cộng đồng những người đam mê Cloud và Trí tuệ nhân tạo. 

#### Học hỏi từ các diễn giả có chuyên môn cao
- Các diễn giả đều là những chuyên gia thực chiến. Việc nghe phân tích "Deep dive" về LLM hay kiến trúc CloudFront mang lại chiều sâu kỹ thuật mà những tài liệu lý thuyết thông thường khó truyền tải được.

#### Trải nghiệm kỹ thuật thực tế
- Ấn tượng nhất là kiến trúc Multi-Agent cấp doanh nghiệp và cách Team VIB xây dựng sản phẩm chỉ trong 36 giờ. Điều này truyền cảm hứng mạnh mẽ về tốc độ triển khai và khả năng làm việc dưới áp lực.

#### Bài học rút ra
- Điện toán đám mây và AI đang hội tụ mạnh mẽ. Là một kỹ sư mạng/hệ thống, việc chỉ biết về hạ tầng (VPC, EC2) là chưa đủ; việc tích hợp các giải pháp AI và hiểu cách LLM hoạt động sẽ là kỹ năng sống còn trong tương lai.

#### Một số hình ảnh khi tham gia sự kiện
*(Thêm các hình ảnh của sự kiện, slide hoặc hình chụp check-in của bạn tại đây)*

> Tổng thể, sự kiện không chỉ giải đáp các vướng mắc về cấu hình hạ tầng AWS mà còn mở ra tầm nhìn chiến lược về cách ứng dụng AI và phân tích dữ liệu vào các hệ thống doanh nghiệp thực thụ.