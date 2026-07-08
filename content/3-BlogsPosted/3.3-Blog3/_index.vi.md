---
title: "Blog 3"
date: 2026-07-08
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


# CRESCONET ĐÃ TỐI ƯU KIẾN TRÚC VÀ GIẢM HƠN 40% CHI PHÍ AWS NHƯ THẾ NÀO?

Một trong những bài toán lớn nhất khi vận hành hệ thống trên AWS là làm sao để cân bằng giữa chi phí, hiệu năng và khả năng mở rộng. Khi hệ thống phát triển, chỉ một vài cấu hình chưa tối ưu cũng có thể khiến hóa đơn AWS tăng lên đáng kể.

CrescoNet – một trong những đơn vị cung cấp giải pháp công tơ điện thông minh hàng đầu tại Úc – đã đối mặt với bài toán này khi hệ thống của họ xử lý hơn 4,5 tỷ bản ghi dữ liệu công tơ mỗi ngày. Thay vì cắt giảm tài nguyên, CrescoNet lựa chọn tối ưu kiến trúc hệ thống và cách sử dụng các dịch vụ AWS.

Kết quả đạt được rất ấn tượng: giảm hơn 40% tổng chi phí AWS, đồng thời giảm tới 80% chi phí của pipeline xử lý dữ liệu meter-to-cash, nhưng vẫn đảm bảo hiệu năng, khả năng mở rộng và độ ổn định của hệ thống.

Những điểm mấu chốt đáng chú ý nhất trong giải pháp này:
Phân tích dữ liệu chi phí trước khi tối ưu

Thay vì tối ưu theo cảm tính, CrescoNet sử dụng AWS Cost and Usage Report (CUR) kết hợp với Amazon QuickSight, Prometheus và Grafana để xác định chính xác dịch vụ nào đang tiêu tốn nhiều chi phí nhất.

Việc dựa trên dữ liệu thực tế giúp mọi quyết định tối ưu đều có cơ sở và dễ dàng đánh giá hiệu quả sau khi triển khai.

Chuyển từ AWS Glue sang Amazon EMR on EKS

AWS Glue là lựa chọn phù hợp ở giai đoạn đầu nhờ khả năng xử lý ETL theo mô hình serverless.

Tuy nhiên, khi khối lượng dữ liệu ngày càng lớn, CrescoNet chuyển sang Amazon EMR trên Amazon EKS để tận dụng khả năng tối ưu của Apache Spark, kết hợp với Amazon EC2 Spot Instances nhằm giảm đáng kể chi phí tính toán.

Chỉ riêng thay đổi này đã giúp doanh nghiệp tiết kiệm hơn 50.000 USD mỗi tháng cho các tác vụ ETL.

Giảm chi phí Amazon S3 bằng Apache Iceberg

Chi phí lưu trữ trên Amazon S3 vốn không quá cao, nhưng CrescoNet nhận thấy chi phí phát sinh từ các thao tác GET và PUT lại lớn hơn rất nhiều do hệ thống tạo ra hàng triệu tệp dữ liệu nhỏ.

Bằng cách áp dụng Apache Iceberg và cơ chế Compaction, nhiều tệp nhỏ được gộp thành các tệp lớn hơn, giúp:

Giảm 27 lần chi phí request trên Amazon S3.
Tăng tốc độ truy vấn dữ liệu.
Cải thiện hiệu năng của toàn bộ pipeline.
Tối ưu AWS Lambda

Hệ thống của CrescoNet xử lý hơn 110 triệu lượt gọi AWS Lambda mỗi tháng.

Thông qua Amazon CloudWatch, họ phát hiện nhiều Lambda đang được cấp phát tài nguyên dư thừa hoặc vẫn sử dụng các phiên bản Python cũ.

Sau khi nâng cấp từ Python 3.8/3.9 lên Python 3.11 và điều chỉnh dung lượng bộ nhớ phù hợp, thời gian thực thi Lambda giảm khoảng 30%, kéo theo chi phí vận hành cũng giảm đáng kể.

Sử dụng Time To Live (TTL) cho Amazon DynamoDB

Không phải dữ liệu nào cũng cần được lưu trên DynamoDB với tốc độ truy cập cao trong thời gian dài.

CrescoNet áp dụng Time To Live (TTL) để tự động xóa các dữ liệu cũ ít được sử dụng và chuyển chúng sang Data Lake.

Kết quả đạt được:

Giảm 66% dung lượng lưu trữ trên DynamoDB.
Tiết kiệm khoảng 3.000 USD mỗi tháng.
Giảm khoảng 10% chi phí ghi dữ liệu.
Tối ưu Amazon MSK

Amazon Managed Streaming for Apache Kafka (MSK) là thành phần quan trọng trong hệ thống xử lý dữ liệu thời gian thực của CrescoNet.

Doanh nghiệp đã tối ưu bằng cách:

Sử dụng Tiered Storage để giảm chi phí lưu trữ dữ liệu Kafka.
Gộp nhiều môi trường không phải production vào cùng một cụm Kafka nhằm giảm chi phí vận hành.
Batch nhiều tin nhắn trên Amazon SQS

Thay vì gửi từng tin nhắn riêng lẻ lên Amazon SQS, CrescoNet gom nhiều message thành một request duy nhất.

Thay đổi khá đơn giản này đã giúp giảm hơn 20 lần chi phí sử dụng Amazon SQS.

Sử dụng Amazon RDS Reserved Instances

Sau khi đánh giá mức sử dụng cơ sở dữ liệu trong thời gian dài, CrescoNet triển khai Amazon RDS Reserved Instances với khả năng thay đổi kích thước trong cùng nhóm instance.

Giải pháp này giúp giảm đáng kể chi phí cơ sở dữ liệu nhưng vẫn giữ được sự linh hoạt khi mở rộng hệ thống.

Tự động tắt môi trường Development ngoài giờ làm việc

Không ít doanh nghiệp vẫn để các môi trường Development và Testing hoạt động 24/7 dù không có người sử dụng.

Thông qua AWS Instance Scheduler, CrescoNet tự động tắt các tài nguyên ngoài giờ làm việc và khởi động lại khi cần, từ đó giảm đáng kể chi phí tính toán mà không ảnh hưởng đến quá trình phát triển phần mềm.

Góc nhìn thực tế:

Điểm đáng học hỏi nhất từ CrescoNet là họ không cố gắng cắt giảm dịch vụ AWS, mà tập trung vào việc sử dụng đúng dịch vụ và tối ưu cách vận hành.

Mỗi thay đổi riêng lẻ có thể chỉ tiết kiệm vài phần trăm chi phí, nhưng khi kết hợp tối ưu từ ETL, Lambda, S3, DynamoDB, Kafka, SQS đến RDS, tổng chi phí hạ tầng đã giảm hơn 40%.

Đây cũng là minh chứng cho thấy tối ưu chi phí trên AWS không đồng nghĩa với việc đánh đổi hiệu năng. Nếu được phân tích và triển khai đúng cách, doanh nghiệp hoàn toàn có thể vừa giảm chi phí, vừa cải thiện hiệu suất và khả năng mở rộng của hệ thống.

Link bài viết gốc:

https://aws.amazon.com/blogs/aws-cloud-financial-management/how-cresconet-optimized-their-architecture-and-reduced-their-aws-bill-by-over-40/

Kết luận:

Câu chuyện của CrescoNet cho thấy tối ưu chi phí trên AWS là một quá trình liên tục dựa trên dữ liệu thay vì chỉ đơn giản là giảm tài nguyên.

Việc lựa chọn đúng dịch vụ, theo dõi chi phí thường xuyên và liên tục cải thiện kiến trúc giúp doanh nghiệp vừa tiết kiệm ngân sách, vừa nâng cao hiệu năng và khả năng mở rộng của hệ thống. Đây là một bài học rất đáng tham khảo đối với các tổ chức đang vận hành những hệ thống lớn trên nền tảng AWS.

![ Blog 3](/images/Blog3.png)