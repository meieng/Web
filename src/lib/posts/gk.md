---
title: "Bài nộp giữa kì"
date: "2025-6-2"
updated: "2025-6-2"
categories:
  - "sveltekit"
  - "markdown"
coverImage: "https://digitalis.io/wp-content/uploads/2020/12/Elastic600x340.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Bài nộp giữa kì
---
## 1. Các đường link nộp bài giữa kì.
- Link github: https://github.com/Maim2728/teanode
- Link Drive(pdf): https://drive.google.com/drive/folders/1dnIE8kJ56wEvwy4wlGTCtd2z_eKZy1FT?usp=drive_link


## 2. Nhận xét.
1. Fault Tolerance với Elasticsearch
Elasticsearch tự bản thân nó đã hỗ trợ fault tolerance bằng cách:

Replication: Elasticsearch cho phép bạn tạo các bản sao (replica shards) cho mỗi shard dữ liệu. Nếu 1 node chứa shard chính bị lỗi, shard replica trên node khác sẽ tự động được kích hoạt.

Cluster: Elasticsearch chạy theo cụm (cluster) nhiều node, mỗi node có thể lưu một phần dữ liệu.

Nếu 1 node trong cluster bị lỗi, cluster vẫn hoạt động bình thường, dữ liệu vẫn truy xuất được qua các node còn lại.

Bạn cần cấu hình Elasticsearch cluster gồm nhiều node (trong Docker, có thể chạy nhiều container Elasticsearch trên các host hoặc cổng khác nhau).

2. Distributed Communication
Elasticsearch sử dụng giao thức HTTP REST API để giao tiếp giữa các node và client.

Mỗi node Elasticsearch trong cluster giao tiếp với nhau qua mạng.

Ứng dụng của bạn sẽ gọi API Elasticsearch qua HTTP.

3. Replication hoặc Sharding
Elasticsearch mặc định chia dữ liệu thành nhiều shard (sharding) và tạo replica (sao chép) cho mỗi shard.

Bạn có thể cấu hình số lượng shard và số lượng replica cho index trong Elasticsearch.

Dữ liệu sẽ được phân phối trên các node theo shard và replica này.

Bạn không cần tự tay làm replication hay sharding mà chỉ cần cấu hình và quản lý cluster Elasticsearch đúng cách.

4. Simple Monitoring / Logging
Elasticsearch hỗ trợ nhiều công cụ để giám sát như:

API / _cluster/health trả về trạng thái cluster.

Elasticsearch có thể tích hợp với Kibana (giao diện web) để xem log, trạng thái cluster, các chỉ số.

Bạn cũng có thể đơn giản viết code gọi API health và log trạng thái cluster.

Trong ứng dụng, bạn nên log lại các thao tác gọi Elasticsearch và trạng thái phản hồi.

5. Basic Stress Test
Elasticsearch Rally (tool benchmark chính thức của Elasticsearch)

Sau khi gửi câu lệnh:
 docker run --rm elastic/rally race --pipeline=benchmark-only --track=geonames --target-hosts=host.docker.internal:9200 --test-mode  
Kết quả  
Sau khi chạy, Rally đã thực hiện các bước:

Xóa chỉ mục (nếu có).

Tạo mới chỉ mục và thiết lập mapping.
Ghi dữ liệu mẫu (~1.000 documents).

Thực hiện các truy vấn phổ biến như:

Term query,pphrase query, aggregation (cached và uncached), script scoring (painless_static, painless_dynamic) , sort theo nhiều cách khác nhau, ffunction score queries, sscroll query

Mặc dù chỉ test với dữ liệu nhỏ, kết quả cho thấy:

- Elasticsearch phản hồi truy vấn rất nhanh với độ trễ thấp (dưới 5 ms).

- Tốc độ ghi dữ liệu ~3.500 documents/s.

- Đây là dấu hiệu tốt cho thấy Elasticsearch hoạt động ổn định trong môi trường hiện tại.
