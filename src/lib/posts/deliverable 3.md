---
title: "Tóm tắt tiến độ dự án"
date: "2025-5-11"
updated: "2025-5-11"
categories:
  - "sveltekit"
  - "markdown"
coverImage: "https://digitalis.io/wp-content/uploads/2020/12/Elastic600x340.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Check out how heading links work with this starter in this post.
---
## 1.Tóm tắt tiến độ dự án
Hệ thống bán trà trực tuyến hiện đã hoàn thành phần giao diện người dùng với HTML, CSS và JavaScript, cùng backend Node.js kết nối với Elasticsearch chạy trong Docker Desktop.

Các tính năng đã hoàn thành:
Triển khai thành công chức năng tìm kiếm sản phẩm:

Người dùng nhập từ khóa trên giao diện → hệ thống gửi yêu cầu tới server.js → kết quả tìm kiếm được trả về từ Elasticsearch và hiển thị ngay lập tức.

Kết nối backend Node.js với Elasticsearch qua REST API.

Thiết lập cluster Elasticsearch đơn node để kiểm tra ban đầu.

Đang phát triển:
Mở rộng Elasticsearch thành cluster nhiều node (replica, sharding).

Tối ưu hóa giao diện kết quả tìm kiếm.

Bổ sung chức năng lọc theo loại trà, giá tiền.

Một số vấn đề đã gặp:
Khó khăn ban đầu khi kết nối Elasticsearch trong Docker với Node.js do sai host → đã khắc phục bằng cách sử dụng host.docker.internal.

Cấu hình CORS để frontend có thể gọi API từ backend.

## 2.Demo hoạt động của hệ thống 
Hệ thống tìm kiếm sản phẩm trà đã được triển khai thành công. Người dùng có thể nhập từ khóa vào ô tìm kiếm trên giao diện web, và kết quả sẽ được hiển thị ngay lập tức.

## 3.Mã nguồn(Code Snippets)

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Tea Search</title>
</head>
<body>
  <h1>Search for Tea Products</h1>
  <input type="text" id="searchInput" placeholder="Enter keyword..." />
  <div id="result"></div>

  <script>
    document.getElementById('searchInput').addEventListener('input', async (e) => {
      const res = await fetch(`/search?q=${e.target.value}`);
      const data = await res.json();

      const html = data.map(item =>
        `<div><strong>${item._source.name}</strong> - ${item._source.description}</div>`
      ).join('');

      document.getElementById('result').innerHTML = html;
    });
  </script>
</body>
</html>

## 4.Danh sách tính năng đã hoàn thành
Tìm kiếm sản phẩm qua Elasticsearch
-Đã triển khai thành công tính năng tìm kiếm tên sản phẩm thông qua Elasticsearch.

-Backend Node.js sử dụng thư viện @elastic/elasticsearch để giao tiếp với Elasticsearch cluster chạy trong Docker.

-Giao diện HTML đơn giản cho phép người dùng nhập từ khóa và nhận kết quả tức thời thông qua fetch().

Ví dụ hoạt động:

-Khi người dùng gõ từ “trà xanh” vào ô tìm kiếm, hệ thống gửi request đến /search?q=tra xanh.

-Server thực hiện match query trên trường name của chỉ mục teas.

-Elasticsearch trả về danh sách sản phẩm có tên phù hợp, sau đó hiển thị ngay trên trình duyệt.
Kết nối hệ thống với Elasticsearch Cluster trong Docker
Cấu hình client kết nối đến node tại localhost:9200, nơi Elasticsearch container đang chạy.

-Server có khả năng phản hồi lỗi khi kết nối không thành công hoặc query không hợp lệ.

Giao tiếp giữa các thành phần hệ thống
-Frontend ↔ Backend: Giao tiếp qua HTTP (fetch() API).

-Backend ↔ Elasticsearch: Giao tiếp thông qua Elasticsearch REST API.

Xử lý lỗi cơ bản
-Khi query lỗi hoặc không có kết nối với Elasticsearch, backend sẽ log lỗi và gửi phản hồi lỗi đến frontend.

Giúp người dùng biết khi nào có vấn đề và tránh crash server.

## 5.Kế hoạch tiếp theo
*Các bước tiếp theo trong dự án:
Hoàn thiện dữ liệu mẫu

-Nhập thêm nhiều dữ liệu sản phẩm vào chỉ mục teas để hệ thống có khả năng tìm kiếm đa dạng hơn.

-Có thể tích hợp giao diện nhập liệu hoặc tạo script để tự động thêm dữ liệu.

Phân trang kết quả tìm kiếm

-Thêm chức năng phân trang kết quả (pagination) khi có nhiều kết quả phù hợp với từ khóa.

Cải tiến giao diện tìm kiếm

-Sử dụng CSS để nâng cấp UI: làm đẹp ô tìm kiếm, kết quả trả về, responsive trên điện thoại.

-Hiển thị thêm hình ảnh, giá sản phẩm nếu có dữ liệu tương ứng.

Tối ưu hiệu năng tìm kiếm

-Cấu hình lại số lượng shard và replica phù hợp trong Elasticsearch.

-Dùng thêm analyzer hoặc autocomplete để cải thiện độ chính xác và trải nghiệm người dùng.

*Những vấn đề cần giải quyết:
Thiếu dữ liệu thực tế: Hiện tại chỉ có dữ liệu mẫu hoặc rất ít sản phẩm → cần thêm dữ liệu để test thực tế.

Giới hạn giao diện: Giao diện đơn giản chưa đủ trực quan → cần cải thiện UX/UI.

Chưa có chức năng thêm/sửa/xóa sản phẩm: Hệ thống hiện chỉ có tìm kiếm → cần bổ sung CRUD trong giai đoạn tiếp theo.

Chưa kiểm thử với nhiều node Elasticsearch: Mới test trên 1 node → cần triển khai cluster nhiều node để kiểm tra khả năng phân tán thực sự.

