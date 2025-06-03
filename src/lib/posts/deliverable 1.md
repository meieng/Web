---
title: "Deliverable 1: Website"
date: "2025-5-11"
updated: "2025-5-11"
categories:
  - "sveltekit"
  - "markdown"
coverImage: "https://digitalis.io/wp-content/uploads/2020/12/Elastic600x340.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Deliverable 1
---

## 1. Đề tài:
Ứng dụng ElasticSearch trong xây dựng hệ thống tìm kiếm phân tán cho website bán trà trực tuyến

## 2. Mô tả vấn đề cần giải quyết:
Trong các website bán trà trực tuyến, khách hàng thường tìm kiếm các loại trà theo tên, mô tả, hương vị, giá, xuất xứ... Với số lượng sản phẩm đa dạng và dữ liệu lớn, hệ thống tìm kiếm truyền thống (dựa trên SQL, LIKE query) thường chậm và không chính xác khi xử lý tìm kiếm full-text, tìm kiếm gần đúng hoặc truy vấn phức tạp.

Ngoài ra, khi lượng truy cập tăng lên đột biến (ví dụ các mùa khuyến mãi, sự kiện), hệ thống cần phải đảm bảo tốc độ phản hồi nhanh, không bị nghẽn hoặc downtime. Do đó, hệ thống tìm kiếm cần phải:

Xử lý nhanh các truy vấn tìm kiếm full-text, hỗ trợ phân tán dữ liệu.

Mở rộng linh hoạt khi dữ liệu và người dùng tăng lên.

Đảm bảo độ chính xác, khả năng lọc nâng cao, phân tích dữ liệu để gợi ý sản phẩm.

## 3. Lý do chọn đề tài:
ElasticSearch là thư viện tìm kiếm phân tán mã nguồn mở hàng đầu, tối ưu cho dữ liệu lớn, full-text, phi cấu trúc.

Thư viện hỗ trợ phân tán (cluster), tự động cân bằng dữ liệu, mở rộng quy mô dễ dàng, rất phù hợp với hệ thống thương mại điện tử có lưu lượng truy cập lớn.

Qua đề tài, ta có thể vận dụng kiến thức về hệ thống phân tán (cluster, sharding, replication), đồng thời hiểu sâu về hoạt động, ưu điểm và nhược điểm của ElasticSearch.

Giúp cải thiện trải nghiệm người dùng bằng công cụ tìm kiếm chính xác và nhanh chóng trên website bán trà.

## 4. Bản chất thư viện ElasticSearch
4.1. Nguyên lý hoạt động
ElasticSearch lưu trữ dữ liệu dưới dạng index (giống như bảng trong CSDL), mỗi index chia thành nhiều shard để phân tán dữ liệu trên nhiều node.

Dữ liệu trong index được lưu dưới dạng document (bản ghi JSON).

Tìm kiếm sử dụng công nghệ full-text search dựa trên Apache Lucene, hỗ trợ phân tích cú pháp, tokenization, stemming, fuzziness...

Hỗ trợ các loại truy vấn đa dạng: full-text, term query, range query, aggregation, geo, suggesters...

Cluster ElasticSearch tự động quản lý việc cân bằng dữ liệu, replication đảm bảo dự phòng.

4.2. Điểm mạnh
Hiệu năng cao: Tìm kiếm trong mili giây, xử lý hàng triệu document.

Phân tán dữ liệu: Dữ liệu tự động phân tán và đồng bộ giữa các node.

Khả năng mở rộng: Thêm/bớt node dễ dàng, không ảnh hưởng tới hoạt động hệ thống.

Tính năng phong phú: Tìm kiếm full-text, phân tích nâng cao, gợi ý, lọc, phân nhóm dữ liệu.

REST API: Dễ dàng tích hợp với mọi ứng dụng web, mobile.

4.3. Điểm yếu
Quản trị phức tạp: Cần kiến thức để cấu hình, tối ưu cluster.

Tốn tài nguyên: RAM và CPU tiêu tốn khá nhiều, đặc biệt với chỉ mục lớn.

Không thay thế CSDL quan hệ: Không hỗ trợ các truy vấn JOIN phức tạp.

Khó đồng bộ dữ liệu 2 chiều: Cần thiết kế kỹ để đồng bộ dữ liệu với hệ thống nguồn (DB).
## Kế hoạch dự kiến
Tuần 1: Tìm hiểu ElasticSearch và chuẩn bị môi trường
Nghiên cứu tổng quan về ElasticSearch:

Tìm hiểu về kiến trúc, các khái niệm như index, shard, replica, cluster, query DSL.

Đánh giá điểm mạnh, điểm yếu và các trường hợp ứng dụng thực tế của ElasticSearch.

Cài đặt môi trường ElasticSearch:

Cài đặt ElasticSearch (bản chính thức hoặc Docker).

Thiết lập cluster đơn giản (1-3 node) để làm quen.

Cài đặt công cụ hỗ trợ: Kibana để quản lý và truy vấn dữ liệu.

Kiểm tra hoạt động của ElasticSearch cluster và kết nối với Kibana.

Tuần 2: Xây dựng ứng dụng web mẫu (Node.js/Express hoặc Django)
Chọn framework phù hợp cho backend (Node.js/Express hoặc Django).

Tạo cấu trúc dự án web cơ bản.

Xây dựng các chức năng cơ bản:

Quản lý sản phẩm trà (CRUD).

Đăng ký, đăng nhập người dùng.

Hiển thị danh sách sản phẩm và profile người dùng.

Kiểm tra hoạt động ứng dụng web, đảm bảo các chức năng chạy ổn định.

Tuần 3: Tích hợp ElasticSearch vào ứng dụng web
Thiết kế mapping index cho sản phẩm trong ElasticSearch (định nghĩa các trường, kiểu dữ liệu, analyzer).

Xây dựng cơ chế đồng bộ dữ liệu giữa cơ sở dữ liệu chính (SQL/NoSQL) và ElasticSearch:

Khi thêm/sửa/xóa sản phẩm, cập nhật dữ liệu trong ElasticSearch.

Tích hợp module tìm kiếm ElasticSearch trong backend:

Xây dựng API tìm kiếm sử dụng query DSL của ElasticSearch (full-text, filter, pagination).

Kiểm tra và đảm bảo dữ liệu được lưu và truy vấn đúng trong ElasticSearch.

Tuần 4: Đo hiệu năng và so sánh
Thiết lập các kịch bản đo hiệu năng tìm kiếm trên ứng dụng web:

Tìm kiếm theo tên, mô tả, filter theo giá, category...