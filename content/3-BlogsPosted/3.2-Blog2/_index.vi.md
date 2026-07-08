---
title: "Blog 2"
date: 2026-07-05
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


# LỰA CHỌN ĐÚNG AWS DATABASE CHO GAME BACKEND – KHÔNG PHẢI DATABASE NÀO CŨNG PHÙ HỢP VỚI MỌI BÀI TOÁN

Một trong những sai lầm phổ biến khi thiết kế backend game là cố gắng giải quyết mọi bài toán chỉ bằng một loại cơ sở dữ liệu. Điều này có thể hoạt động ở giai đoạn đầu, nhưng khi lượng người chơi tăng lên, các tính năng như bảng xếp hạng, matchmaking hay chat thời gian thực sẽ nhanh chóng trở thành điểm nghẽn.

AWS đưa ra một hướng tiếp cận khác: Purpose-built Database, tức là sử dụng đúng loại database cho đúng workload thay vì "một database cho tất cả".

Những điểm mấu chốt đáng chú ý nhất trong giải pháp này:

Leaderboards (Bảng xếp hạng)

Leaderboards cần xử lý các yêu cầu như xếp hạng của người chơi, top người chơi hoặc những người chơi xung quanh một thứ hạng nhất định với độ trễ rất thấp.

AWS khuyến nghị sử dụng Amazon ElastiCache hoặc Amazon MemoryDB nhờ Redis Sorted Set, giúp:

Tính toán thứ hạng với độ phức tạp O(log N).
Cập nhật điểm số theo thời gian thực.
Hỗ trợ leaderboard theo mùa hoặc theo khoảng thời gian bằng TTL.

Đối với những leaderboard đơn giản hơn (theo khu vực hoặc theo màn chơi), Amazon DynamoDB cũng có thể đáp ứng, tuy nhiên không tối ưu cho việc xác định chính xác thứ hạng của từng người chơi.

Matchmaking

Ghép trận là bài toán yêu cầu xử lý số lượng lớn thao tác đọc và ghi trong thời gian rất ngắn, dựa trên các tiêu chí như kỹ năng, độ trễ mạng, khu vực hoặc số lượng thành viên trong đội.

AWS đề xuất:

Amazon ElastiCache nếu dữ liệu hàng đợi chỉ mang tính tạm thời.
Amazon MemoryDB nếu cần đảm bảo dữ liệu vẫn tồn tại khi node gặp sự cố.

Redis Sorted Set giúp quản lý hàng đợi theo MMR, trong khi Pub/Sub hỗ trợ gửi thông báo ngay khi người chơi tìm được trận.

Nếu hệ thống matchmaking không quá phức tạp, Amazon DynamoDB kết hợp với AWS Lambda và DynamoDB Streams cũng là một lựa chọn đáng cân nhắc.

Chat và Messaging

Hệ thống chat trong game yêu cầu độ trễ thấp, tin nhắn đúng thứ tự và hỗ trợ nhiều hình thức như chat cá nhân, chat nhóm hoặc guild.

AWS khuyến nghị sử dụng Amazon ElastiCache hoặc Amazon MemoryDB với Redis Streams để lưu trữ và phân phối tin nhắn theo đúng thứ tự.

Trong trường hợp cần lưu lịch sử chat lâu dài hoặc phục vụ việc kiểm duyệt nội dung, Amazon DynamoDB sẽ đảm nhận vai trò lưu trữ dữ liệu bền vững.

Social Graph (Friends, Guilds, Clans)

Các chức năng như danh sách bạn bè, guild, clan hoặc gợi ý kết bạn thực chất là các bài toán về đồ thị, trong đó người chơi là các nút và mối quan hệ là các cạnh.

Amazon Neptune được thiết kế dành riêng cho Graph Database nên có thể:

Truy vấn quan hệ chỉ với một lần truy vấn.
Hỗ trợ Gremlin Query Language.
Tích hợp Machine Learning để gợi ý bạn bè.
Có sẵn các thuật toán như PageRank, Similarity và Community Detection.

Nếu chỉ cần các thao tác cơ bản như thêm, xóa hoặc liệt kê bạn bè thì Amazon DynamoDB vẫn là một lựa chọn phù hợp.

Game Analytics và Player Behavior

Việc phân tích hành vi người chơi, doanh thu, A/B Testing hoặc dữ liệu telemetry thường yêu cầu xử lý khối lượng dữ liệu rất lớn.

AWS cung cấp nhiều lựa chọn phù hợp với từng nhu cầu:

Amazon Athena cho phép truy vấn trực tiếp dữ liệu trên Amazon S3 mà không cần quản lý hạ tầng.
Amazon Redshift phù hợp với các hệ thống Data Warehouse và dashboard phân tích dữ liệu quy mô lớn.
Amazon Timestream được tối ưu cho dữ liệu chuỗi thời gian như độ trễ, FPS, thời lượng phiên chơi hoặc số lượng người chơi theo từng thời điểm.

Góc nhìn thực tế:

Dưới góc độ phát triển Game Backend, việc lựa chọn đúng loại cơ sở dữ liệu quan trọng không kém việc tối ưu thuật toán hay hạ tầng.

Thay vì cố gắng lưu toàn bộ dữ liệu vào một Relational Database, việc kết hợp nhiều dịch vụ theo đúng mục đích sử dụng sẽ giúp hệ thống đạt hiệu năng cao hơn, dễ mở rộng hơn và giảm đáng kể các điểm nghẽn khi số lượng người chơi tăng lên.

Ví dụ:

Leaderboard sử dụng Amazon ElastiCache hoặc Amazon MemoryDB.
Matchmaking sử dụng Amazon MemoryDB.
Chat thời gian thực sử dụng Redis Streams.
Quan hệ bạn bè và guild sử dụng Amazon Neptune.
Phân tích dữ liệu sử dụng Amazon Athena hoặc Amazon Redshift.

Đây là cách tiếp cận mà nhiều studio game hiện nay áp dụng để xây dựng các hệ thống backend có khả năng mở rộng và đáp ứng tốt lượng truy cập lớn.

Link bài viết gốc:

https://aws.amazon.com/.../aws-cloudtrail-lake-import.../

Kết luận:
Không tồn tại một loại database có thể đáp ứng tối ưu cho mọi tính năng trong game. AWS hướng đến mô hình Purpose-built Database, trong đó mỗi workload sẽ được ghép với dịch vụ phù hợp nhất.

Việc lựa chọn đúng database ngay từ giai đoạn thiết kế không chỉ giúp tối ưu hiệu năng, giảm chi phí vận hành mà còn tăng khả năng mở rộng và đơn giản hóa việc bảo trì khi hệ thống phát triển. Đây là một hướng tiếp cận rất đáng tham khảo đối với các dự án Game Backend hiện đại.

![ Blog 2](/images/Blog2.jpg)