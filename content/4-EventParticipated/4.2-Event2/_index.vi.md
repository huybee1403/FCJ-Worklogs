---
title: "Event 2"
date: 2026-05-30
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# BÀI THU HOẠCH: GIỚI THIỆU HERA — WORKSHOP VOICE AGENT TRÊN AWS
---
> [!IMPORTANT]
> ### 🎯 Mục tiêu & Tổng quan Workshop
> **Workshop Hera** là tài liệu thực hành chi tiết hướng dẫn triển khai **Bilingual Voice Agent** (Trợ lý giọng nói song ngữ) thời gian thực sử dụng **Amazon Bedrock AgentCore Runtime** và mô hình âm thanh **Amazon Nova 2 Sonic**.


## 1. Voice AI & Dự án Hera là gì?

### Voice Agent

Voice Agent là dịch vụ trí tuệ nhân tạo (AI) hoạt động theo cơ chế **truyền phát âm thanh hai chiều theo thời gian thực** (*real-time bidirectional audio streaming*).

Luồng hoạt động:

1. Người dùng nói vào microphone.
2. Âm thanh được truyền tới mô hình speech-to-speech.
3. Mô hình xử lý và tạo phản hồi bằng giọng nói.
4. Âm thanh phản hồi được phát lại trên trình duyệt.

Toàn bộ chu kỳ diễn ra với độ trễ dưới **1 giây**.

### Hera

Hera sử dụng **Amazon Nova 2 Sonic**, mô hình speech-to-speech trên **Amazon Bedrock**, triển khai tại vùng **ap-northeast-1 (Tokyo)**.

Các khả năng nổi bật:

- Giao tiếp bằng giọng nói theo thời gian thực.
- Hỗ trợ gọi công cụ (*Tool Use*).
- Có thể truy vấn **Amazon Bedrock Knowledge Base** ngay trong cùng một luồng streaming.

---

## 2. Lý do lựa chọn Tech Stack

Workshop Hera được xây dựng dựa trên sự kết hợp của các công nghệ sau.

### Amazon Nova 2 Sonic

- Mô hình speech-to-speech thuần AWS.
- Độ trễ thấp từ Việt Nam.
- Tính phí theo phút sử dụng.
- Hỗ trợ Tool Use tự nhiên với Bedrock Knowledge Base.

### Amazon Bedrock AgentCore Runtime

- Managed runtime.
- Không cần cấu hình VPC, ALB hoặc NAT Gateway.
- Hỗ trợ ARM64.
- Bảo mật thông qua IMDSv2.
- Dễ debug và vận hành.

### Pipecat (v1.1.0)

Pipecat đóng vai trò điều phối (*orchestrator*) cho voice pipeline.

Đặc điểm:

- Tích hợp sẵn `AWSNovaSonicLLMService`.
- Tự động xử lý giới hạn stream tối đa **8 phút** của Nova Sonic.
- Quản lý toàn bộ voice loop.

### S3 Vectors + Titan v2

Giải pháp RAG chi phí thấp:

- Khoảng **0.10 USD/tháng** với dữ liệu nhỏ.
- Rẻ hơn đáng kể so với OpenSearch Serverless (**200–400 USD/tháng**).

### Terraform + AWS CDK (Python)

Kết hợp Infrastructure as Code:

| Công cụ | Vai trò |
|---------|----------|
| Terraform | Quản lý Bedrock Knowledge Base |
| AWS CDK (Python) | Triển khai AgentCore Runtime |

---

## 3. Kiến trúc tổng thể

Quy trình xử lý giọng nói diễn ra như sau.

### Bước 1. Yêu cầu kết nối

Trình duyệt yêu cầu một **WebSocket URL (WSS)** đã được ký bằng **AWS SigV4**, có thời hạn khoảng **300 giây** từ **Presigner Lambda**.

### Bước 2. Kết nối

Browser kết nối tới **AgentCore Runtime** (container Pipecat) thông qua WebSocket và truyền âm thanh **16 kHz**.

### Bước 3. Tool Use

AgentCore Runtime chuyển tiếp audio tới Nova 2 Sonic.

Khi Sonic phát hiện câu hỏi cần tra cứu dữ liệu, nó sẽ gọi công cụ:

```text
lookup_product
```

### Bước 4. RAG Retrieval

AgentCore Runtime gọi:

```text
bedrock-agent-runtime.retrieve
```

để truy vấn **Bedrock Knowledge Base**.

Knowledge Base trả về:

- Top 3 kết quả
- Từ S3 Vectors

Sau đó AgentCore Runtime gửi kết quả trở lại Nova Sonic trong cùng luồng streaming.

### Bước 5. Phản hồi

Nova Sonic:

- Sinh phản hồi bằng giọng nói 24 kHz.
- Gửi audio về AgentCore Runtime.
- AgentCore Runtime truyền lại trình duyệt.
- Browser phát âm thanh cho người dùng.

> Tổng thời gian xử lý cho một vòng hội thoại (End-to-End Turn) khoảng **3 giây**.

---

## 4. Region triển khai

Region mặc định:

```text
ap-northeast-1 (Tokyo)
```

Lý do:

- Độ trễ thấp nhất tới Việt Nam.
- Hỗ trợ đầy đủ:
  - Amazon Nova 2 Sonic
  - AgentCore Runtime
  - Bedrock Knowledge Base
  - S3 Vectors

Các region khác được hỗ trợ:

- `us-east-1`
- `us-west-2`
- `eu-north-1`

---

## 5. Yêu cầu trước khi bắt đầu

### Tài khoản AWS

Cần chuẩn bị:

- AWS Account
- IAM User
- Quyền `AdministratorAccess`

> Chỉ sử dụng cho workshop, không sử dụng tài khoản Root.

### Kiến thức

Người học nên có kiến thức cơ bản về:

- AWS Console
- IAM
- VPC
- Docker
- Terraform

### Công cụ cần cài đặt

- AWS CLI v2
- Terraform >= 1.9
- uv (Python package manager)
- Docker Desktop (hỗ trợ Buildx Multi-Arch)
- jq
- Chrome / Firefox / Safari (hỗ trợ HTTPS và microphone)

> Workshop sử dụng **uv**, không sử dụng `pip`.

### Chi phí

Ước tính:

- **2–5 USD**
- Cho khoảng **2 giờ** thực hành.

> Sau khi hoàn thành workshop, hãy thực hiện phần **Cleanup** để tránh phát sinh chi phí duy trì tài nguyên.

---

## 6. Quy ước của Workshop

### Mã nguồn

Source code được tổ chức theo từng **Phase** để thuận tiện theo dõi.

### Hình ảnh

Các screenshot đều có:

- Khung màu đỏ
- Mũi tên chỉ dẫn
- Chú thích tại các bước quan trọng trên AWS Console

### Ngôn ngữ

Workshop sử dụng:

- Chatbot: **Tiếng Anh** (Nova Sonic hoạt động tốt nhất với tiếng Anh)
- Tài liệu: **Song ngữ Anh – Việt (vi/en)**

> Hệ thống CI sẽ kiểm tra số lượng trang tiếng Việt và tiếng Anh. Build sẽ thất bại nếu hai ngôn ngữ không đồng bộ.

---

> [!TIP]
> ### 💡 Bài học & Nhận thức chung (Synthesis)
> 
> Qua việc tìm hiểu và thực hành Workshop Hera, tôi đã rút ra được một số nhận thức công nghệ quan trọng:
> 
> 1. **Cuộc cách mạng của Trí tuệ nhân tạo giọng nói thời gian thực (Voice AI)**:
>    * Nhờ có **Amazon Nova 2 Sonic** với kiến trúc speech-to-speech cải tiến, việc giao tiếp hai chiều với AI không còn bị chia cắt thành các bước trung gian (STT -> LLM -> TTS) giúp tối ưu hóa độ trễ xuống dưới 1 giây, đem lại trải nghiệm đàm thoại tự nhiên gần như người thật.
> 2. **Tối ưu hóa thiết kế hạ tầng và chi phí (Serverless & RAG tối giản)**:
>    * Thay vì sử dụng OpenSearch Serverless tốn kém (200-400 USD/tháng), giải pháp tích hợp **S3 Vectors + Titan v2** chỉ tiêu tốn khoảng 0.10 USD/tháng mà vẫn đáp ứng tốt nghiệp vụ RAG.
>    * Sử dụng **Amazon Bedrock AgentCore Runtime** giúp đơn giản hóa việc quản lý vòng đời container của Pipecat mà không cần cấu hình phức tạp các thành phần VPC, ALB hay NAT Gateway, vừa tiết kiệm chi phí vận hành vừa đảm bảo tính bảo mật.
> 3. **Tầm quan trọng của sự đồng bộ trong Infrastructure as Code (IaC)**:
>    * Việc kết hợp song song giữa **Terraform** (cho Bedrock Knowledge Base) và **AWS CDK Python** (cho AgentCore Runtime) tạo nên một luồng triển khai liền mạch, dễ quản lý và dễ dọn dẹp tài nguyên (cleanup) sau khi kết thúc dự án.
