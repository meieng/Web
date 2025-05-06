---
title: "Tiến trình và luồng"
date: "2023-01-05"
updated: "2023-01-05"
categories:
  - "sveltekit"
  - "web"
  - "css"
  - "markdown"
coverImage: "/images/linus-nylund-Q5QspluNZmM-unsplash.jpg"
coverWidth: 16
coverHeight: 9
excerpt: This post shows you how syntax highlighting works here.
---
## 1. Kiểm tra CPU, GPU, RAM – Hiệu năng máy tính

*Đánh giá hiệu năng máy tính - MacBook Pro (13-inch, 2020)

## Thông tin phần cứng
- **Model**: MacBook Pro (13-inch, 2020)
- **CPU**: Intel Core i5 1.4GHz (4 nhân, 8 luồng)
- **GPU**: Intel Iris Plus Graphics 645 (1536MB)
- **RAM**: 8GB LPDDR3 2133MHz
- **Hệ điều hành**: macOS Sequoia 15.4

---

## 🔍 Đánh giá hiệu năng

### CPU
![CPU](/images/anh2.png)
- 1.4GHz Quad-Core i5 là dòng tiết kiệm điện, hiệu năng trung bình.
- Phù hợp với: học tập, lập trình cơ bản, xử lý văn bản, duyệt web.
- Không lý tưởng cho: biên dịch lớn, máy ảo nặng, AI training.

### GPU
- Intel Iris Plus 645 là GPU tích hợp.
- Dùng được cho: xem video, thiết kế nhẹ, frontend.
- Không phù hợp: game, dựng hình 3D, machine learning.

### RAM
![RAM](/images/ảnh3.png)
- 8GB LPDDR3 tốc độ 2133MHz.
- Phù hợp: sử dụng hàng ngày, đa nhiệm cơ bản.
- Giới hạn: chạy nhiều ứng dụng nặng, Docker, VM.

---

## 2. 12 bài toán phổ biến sử dụng đa luồng/đa tiến trình

| STT | Bài toán                              | Sử dụng đa luồng/tiến trình                         |   
|-----|----------------------------------------|----------------------------------------------------|
| 1   | Web server (Nginx, Apache)            | Mỗi request = 1 thread/process                     |
| 2   | Trình duyệt (Chrome, Firefox)         | Tab = process, render = thread                    |
| 3   | Trình biên dịch (Compiler)            | Biên dịch file song song                          |
| 4   | Game                                  | Thread riêng cho hình ảnh, âm thanh, input        |
| 5   | Chat app real-time                    | Thread riêng gửi/nhận tin nhắn                    |
| 6   | Xử lý ảnh                              | Chia ảnh thành block, xử lý song song             |
| 7   | Web scraping                          | Mỗi website = 1 thread/process                    |
| 8   | Hệ điều hành                          | Process quản lý app, thread xử lý I/O             |
| 9   | Huấn luyện AI                         | Đa tiến trình xử lý dữ liệu song song             |
| 10  | Giả lập (VM, emulator)                | VM = process, có nhiều thread phụ                 |
| 11  | Cơ sở dữ liệu                         | Connection pool = thread                          |
| 12  | Streaming video                       | Thread decode, buffer, render riêng               |

---

## 3. Khi nào dùng Thread? Khi nào dùng Process?


![A](/images/ẢNH1.jpg)


---

## 4. ChatGPT và hệ thống phân tán khi huấn luyện

### Mô hình ChatGPT sử dụng hệ thống phân tán:
- **Data Parallelism:** chia batch dữ liệu cho nhiều GPU cùng xử lý
- **Model Parallelism:** chia tầng của mạng neural ra nhiều GPU
- **Pipeline Parallelism:** phân tầng thành các giai đoạn để xử lý nối tiếp

### Công nghệ sử dụng:
- GPU cluster tốc độ cao (NVIDIA A100, TPU)
- Kết nối InfiniBand
- Framework: PyTorch Distributed, DeepSpeed, Megatron-LM

### Tài liệu tham khảo:
- [EleutherAI GPT-3 Training Blog](https://blog.eleuther.ai/gpt3-model-training/)
- [NVIDIA - Scaling Deep Learning](https://developer.nvidia.com/blog/large-language-model-training-gpu-clusters/)
- [Microsoft DeepSpeed](https://www.microsoft.com/en-us/research/project/deepspeed/)

---

