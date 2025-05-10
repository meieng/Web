---
title: "Truyền Thông"
date: "2025-04-29"
categories:
  - "Hệ thống phân tán"
  - "Đa luồng & đa tiến trình"
coverImage: "/images/ảnhtt.jpg"
excerpt: truyền thông 

---
 ## Bài tập 1: Tìm hiểu RabbitMQ - Dịch vụ truyền thông điệp

## 1. Giới thiệu về RabbitMQ:
RabbitMQ là một message broker được sử dụng để truyền thông tin giữa các hệ thống phân tán. Nó hỗ trợ các giao thức như AMQP, MQTT, STOMP, v.v. RabbitMQ cho phép các ứng dụng giao tiếp với nhau mà không cần biết trực tiếp về nhau.

## 2. Cơ chế hoạt động:

Producer: Gửi message.

Exchange: Nhận message từ producer và quyết định chuyển message đi đâu.

Queue: Hàng đợi chờ message.

Consumer: Nhận message từ queue.

Message đi từ Producer → Exchange → Queue → Consumer. Việc truyền thông là không đồng bộ, giúp giảm độ phụ thuộc giữa các thành phần.

## 3. Lợi ích:

Tách biệt các hệ thống.

Giao tiếp linh hoạt, dễ mở rộng.

Quản lý message tin cậy (ACK, retry, dead-letter).

## 4. Cài đặt RabbitMQ trên macOS:

```bash
brew install rabbitmq
brew services start rabbitmq
open http://localhost:15672
```

## 5. Cấu trúc cơ bản của RabbitMQ:

Direct exchange: route theo tên routing key.

Fanout exchange: broadcast tới tất cả queues.

Topic exchange: match theo mẫu chuỗi.

Headers exchange: route theo thuộc tính header.

## 6. Tình huống sử dụng RabbitMQ:

Hệ thống thanh toán.

Hệ thống gửi email/sms.

Truyền thông sự kiện trong microservices.

## 7. Tổng kết:
RabbitMQ là một lựa chọn phổ biến trong các hệ thống phân tán vì tính tin cậy, dễ triển khai và linh hoạt. Việc tìm hiểu RabbitMQ là cần thiết để thiết kế các hệ thống quy mô lớn hoặc xử lý song song.

---
## Bài tập 2: Code hệ thống đơn giản dùng RabbitMQ
## Gửi và nhận tin nhắn giữa 2 thành phần Python.

## Mã nguồn Producer (send.py)

``` python
import pika

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()

channel.queue_declare(queue='hello')

channel.basic_publish(exchange='',
                      routing_key='hello',
                      body='Hello RabbitMQ!')
print(" [x] Sent 'Hello RabbitMQ!'")
connection.close()
```

## Mã nguồn Consumer (receive.py)
``` python
import pika

def callback(ch, method, properties, body):
    print(f" [x] Received {body}")

connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()

channel.queue_declare(queue='hello')

channel.basic_consume(queue='hello',
                      on_message_callback=callback,
                      auto_ack=True)

print(' [*] Waiting for messages. To exit press CTRL+C')
channel.start_consuming()
```
## Cách chạy hệ thống

Mở hai terminal:

Terminal 1: python receive.py

Terminal 2: python send.py

---
## Bài tập 3: RPC với định dạng JSON
Ngoài xmlrpc, có thư viện như json-rpc hoặc gRPC với JSON.

Gợi ý: Sử dụng jsonrpcserver và requests

## Server (server.py):
``` python
from jsonrpcserver import method, serve

@method
def add(x, y):
    return x + y

serve("localhost", 5000)
```

## Client (client.py):

``` python
import requests
import json

payload = {
    "jsonrpc": "2.0",
    "method": "add",
    "params": {"x": 5, "y": 3},
    "id": 1
}
response = requests.post("("http://localhost:5000", json=payload)
print(response.json())
```
---
## Kết luận:

Bài tập đã giúp em hiểu rõ về người trung gian truyền thông trong hệ thống phân tán (như RabbitMQ) và cách RPC giúp hai ứng dụng gọi-hồi giá trị trực tiếp như hàm cùng host.

Bài demo đơn giản nhưng đủ để thể hiện được ý tưởng thiết kế và triển khai các hệ thống backend linh hoạt, tự động.