---
title: "I. Kiến thức về hệ thống phân tán"
date: "2023-10-26"
updated: "2023-10-26"
categories:
  - "sveltekit"
  - "markdown"
coverImage: "/images/jefferson-santos-fCEJGBzAkrU-unsplash.jpg"
coverWidth: 16
coverHeight: 9
excerpt: Trong kỷ nguyên số hiện nay, hệ thống phân tán không còn là khái niệm xa lạ. Chúng âm thầm vận hành phía sau những nền tảng mà chúng ta sử dụng mỗi ngày — từ mạng xã hội, ứng dụng ngân hàng cho đến các dịch vụ phát trực tuyến. Vậy hệ thống phân tán là gì? Những khái niệm nào cần nắm vững? Cùng mình tìm hiểu trong bài blog này nhé!

# 1. Hệ thống phân tán là gì?
Hệ thống phân tán (Distributed System) là một tập hợp nhiều máy tính độc lập về phần cứng, phần mềm và địa lý, nhưng phối hợp chặt chẽ với nhau để hoàn thành các nhiệm vụ chung. Người dùng hoặc chương trình ứng dụng sẽ nhìn nhận toàn bộ hệ thống như một thực thể thống nhất, mặc dù các thành phần này phân tán ở nhiều nơi khác nhau.

Các đặc trưng nổi bật:

Các thành phần hoạt động song song, phối hợp với nhau qua mạng máy tính.

Các lỗi cục bộ không làm ảnh hưởng toàn bộ hệ thống.

Dữ liệu và tài nguyên có thể được chia sẻ và nhân bản.

Mục tiêu thiết kế:

Minh bạch hoạt động (Transparency).

Mở rộng linh hoạt (Scalability).

Độ tin cậy và tính sẵn sàng cao (Fault Tolerance & Availability).


# 2. Các ứng dụng của hệ thống phân tán.
Hệ thống phân tán ngày càng đóng vai trò quan trọng trong nhiều lĩnh vực của đời sống hiện đại. Với khả năng mở rộng linh hoạt, xử lý đồng thời khối lượng lớn yêu cầu từ người dùng và đảm bảo tính sẵn sàng cao, hệ thống phân tán đã trở thành nền tảng cho rất nhiều dịch vụ mà chúng ta sử dụng hàng ngày. Dưới đây là một số lĩnh vực tiêu biểu:

a. Mạng xã hội
Các nền tảng mạng xã hội như Facebook, Twitter, Instagram sử dụng hệ thống phân tán để phục vụ hàng tỷ người dùng trên toàn thế giới. Mỗi giây có hàng triệu lượt đăng bài, chia sẻ, nhắn tin và tương tác diễn ra. Hệ thống phân tán giúp lưu trữ dữ liệu người dùng tại nhiều trung tâm dữ liệu khác nhau, đồng thời đảm bảo rằng người dùng có thể truy cập thông tin nhanh chóng bất kể họ đang ở đâu. Ngoài ra, nó còn giúp xử lý các thuật toán gợi ý nội dung (recommendation) trong thời gian thực.

b. Lưu trữ đám mây
Dịch vụ lưu trữ đám mây như Google Drive, Dropbox, OneDrive cho phép người dùng lưu trữ, chia sẻ và truy cập tài liệu từ bất kỳ thiết bị nào, ở bất cứ đâu có kết nối Internet. Hệ thống phân tán đảm bảo rằng dữ liệu được sao lưu tự động ở nhiều địa điểm khác nhau để phòng ngừa mất mát do sự cố phần cứng hoặc thiên tai, đồng thời tối ưu hóa tốc độ truy cập bằng cách sử dụng các máy chủ gần nhất với người dùng.

c. Thương mại điện tử
Các "gã khổng lồ" thương mại điện tử như Amazon, Shopee, Lazada sử dụng hệ thống phân tán để xử lý hàng triệu đơn hàng, giao dịch và truy vấn mỗi ngày. Vào những dịp đặc biệt như Black Friday, 11.11, hệ thống phải chịu tải cực kỳ lớn. Nhờ các kỹ thuật phân tán như cân bằng tải, nhân bản dịch vụ (replication) và mở rộng hệ thống theo chiều ngang (horizontal scaling), các nền tảng này có thể hoạt động ổn định mà không bị gián đoạn.

d. Ngân hàng số và dịch vụ tài chính
Trong lĩnh vực ngân hàng số, hệ thống phân tán đảm bảo rằng các giao dịch tài chính diễn ra an toàn, chính xác và liên tục 24/7. Ví dụ như Momo, ZaloPay, hay các ngân hàng như Techcombank, Vietcombank đều sử dụng các hệ thống phân tán để xử lý giao dịch chuyển tiền, thanh toán hóa đơn, và quản lý tài khoản khách hàng. Ngoài ra, các giải pháp phân tán còn giúp tăng cường bảo mật và phục hồi nhanh chóng khi có sự cố xảy ra.

e. Game online
Các trò chơi trực tuyến quy mô lớn như PUBG, Valorant, Liên Quân Mobile, League of Legends yêu cầu hệ thống có khả năng xử lý đồng thời hàng triệu người chơi từ khắp nơi trên thế giới. Hệ thống phân tán giúp phân phối các phiên chơi (game sessions) qua nhiều máy chủ, giảm độ trễ mạng (latency), đồng thời đảm bảo rằng trò chơi diễn ra mượt mà, công bằng, và ổn định bất kể số lượng người chơi tăng đột biến.

f. Internet of Things (IoT)
Trong thế giới của các thiết bị thông minh, hệ thống phân tán là nền tảng không thể thiếu. Các thiết bị IoT như cảm biến thời tiết, đồng hồ thông minh, xe tự lái, hệ thống nhà thông minh (smart home) liên tục trao đổi dữ liệu với các trung tâm xử lý phân tán. Điều này cho phép thu thập, xử lý và phản hồi dữ liệu theo thời gian thực, phục vụ các ứng dụng từ chăm sóc sức khỏe, giao thông thông minh cho đến công nghiệp sản xuất.




# 3. Các khái niệm chính của hệ thống phân tán.
Để hiểu sâu hơn, hãy cùng tìm hiểu từng khái niệm quan trọng:

Scalability (Khả năng mở rộng): Hệ thống có thể tăng khả năng xử lý khi tải tăng, bằng cách nâng cấp phần cứng (vertical scaling) hoặc thêm máy mới (horizontal scaling).

Fault Tolerance (Khả năng chịu lỗi): Khi một số thành phần hỏng hóc, hệ thống vẫn duy trì hoạt động bình thường.

Availability (Tính sẵn sàng): Hệ thống luôn sẵn sàng phục vụ yêu cầu người dùng bất kể thời gian nào.

Transparency (Tính minh bạch):

Access transparency: Người dùng không cần biết dữ liệu nằm ở đâu.

Location transparency: Người dùng truy cập mà không cần quan tâm máy chủ vật lý nào.

Replication transparency: Người dùng không thấy quá trình nhân bản dữ liệu.

Concurrency (Xử lý đồng thời): Hệ thống hỗ trợ nhiều tiến trình chạy song song mà không làm nghẽn tài nguyên chung.

Parallelism (Xử lý song song): Một nhiệm vụ lớn được chia nhỏ thành các phần có thể chạy cùng lúc, tăng tốc độ xử lý.

Openness (Tính mở): Hệ thống có thể giao tiếp với các hệ thống khác dễ dàng thông qua giao thức và chuẩn chung.

Vertical Scaling (Mở rộng dọc): Nâng cấp phần cứng máy chủ đơn lẻ (thêm CPU, RAM).

Horizontal Scaling (Mở rộng ngang): Thêm nhiều máy chủ cùng tham gia hệ thống.

Load Balancer (Bộ cân bằng tải): Thiết bị/phần mềm phân phối lưu lượng truy cập tới các máy chủ để tối ưu hiệu suất.

Replication (Nhân bản dữ liệu): Tạo nhiều bản sao dữ liệu hoặc dịch vụ để đảm bảo tính toàn vẹn, phục hồi nhanh chóng khi xảy ra sự cố.

Ví dụ thực tế và mối liên hệ các khái niệm
Ví dụ: Netflix
Netflix là nền tảng phát trực tuyến số 1 thế giới, với hàng triệu người xem đồng thời.

Khi nhu cầu tăng cao, Netflix thêm nhiều server mới (Horizontal Scaling) để tránh quá tải.

Nếu một trung tâm dữ liệu gặp sự cố, dịch vụ vẫn tiếp tục nhờ các bản sao dự phòng (Fault Tolerance + Replication).

Dữ liệu phim, tài khoản người dùng được phân bố toàn cầu, người xem không biết mình đang được phục vụ từ đâu (Transparency).

Netflix xử lý hàng triệu request streaming và tìm kiếm cùng lúc (Concurrency).

Các video được chia thành các đoạn nhỏ (chunk) và tải đồng thời (Parallelism) để tăng tốc độ phát.

Netflix cung cấp API mở cho smart TV, mobile app, laptop... (Openness).

Trong giai đoạn bùng nổ số lượng người dùng, Netflix vừa nâng cấp phần cứng (Vertical Scaling) vừa xây thêm data center (Horizontal Scaling).

Các Load Balancer phân phối người dùng tới server gần nhất, đảm bảo độ trễ thấp.


# 4. Kiến trúc của hệ thống phân tán
Kiến trúc hệ thống phân tán được phát triển theo nhiều mô hình khác nhau, tùy vào nhu cầu sử dụng:

a. Client-Server Model
Một hoặc nhiều client gửi yêu cầu tới server.

Server xử lý và trả về kết quả.

Ưu điểm: Dễ xây dựng, quản lý.

Nhược điểm: Server dễ trở thành điểm nghẽn.

b. Peer-to-Peer (P2P)
Các nút đều bình đẳng, không cần server trung tâm.

Ví dụ: Torrent, Blockchain.

Ưu điểm: Tính phân tán cao, khó sụp đổ toàn hệ thống.

Nhược điểm: Khó quản lý, đảm bảo chất lượng dịch vụ.

c. Three-Tier Architecture (Ba tầng)
Tầng Presentation: Giao diện người dùng.

Tầng Application: Logic nghiệp vụ.

Tầng Data: Lưu trữ dữ liệu.

Ví dụ: Các hệ thống ngân hàng.

d. Microservices Architecture
Ứng dụng chia thành các dịch vụ nhỏ, độc lập, giao tiếp qua API.

Mỗi service đảm nhiệm một chức năng: giỏ hàng, thanh toán, tìm kiếm...

Ưu điểm: Dễ mở rộng, dễ cập nhật.

Nhược điểm: Quản lý phức tạp.

e. Service-Oriented Architecture (SOA)
Các dịch vụ giao tiếp thông qua một Enterprise Service Bus (ESB).

Phù hợp với các hệ thống lớn cần tích hợp nhiều phần mềm khác nhau.

f. Serverless Architecture (Kiến trúc không máy chủ)
Nhà phát triển chỉ tập trung vào viết code logic.

Vận hành hạ tầng, tự động scale do nhà cung cấp dịch vụ (AWS, Azure) đảm nhận.

Ví dụ về kiến trúc hệ thống phân tán.
Shopee và kiến trúc Microservices:
Khi người dùng truy cập, Load Balancer chọn service nhẹ nhất.

Service tìm kiếm, service đơn hàng, service thanh toán hoạt động độc lập.

Khi có Flash Sale, Shopee dùng Horizontal Scaling để thêm nhiều máy chủ.

Hệ thống Replication đảm bảo đơn hàng không bị mất khi server gặp lỗi.

Người dùng truy cập không nhận thấy quá trình chuyển đổi giữa các node (Transparency).

Nhờ đó, Shopee xử lý hàng triệu giao dịch/giây mà vẫn ổn định và nhanh chóng.


