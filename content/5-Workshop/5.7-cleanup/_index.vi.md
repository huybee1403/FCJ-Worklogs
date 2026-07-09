---
title: "Dọn dẹp tài nguyên"
date: 2026-07-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

<div class="lms">

Sau khi hoàn thành, xóa tài nguyên để tránh phát sinh chi phí.

{{% notice warning %}}
Hãy **xóa tài nguyên theo đúng thứ tự phụ thuộc** (ASG → ALB/Target group → EC2 → DocumentDB → VPC) để tránh lỗi. DocumentDB có bật *Deletion protection* nên cần tắt bảo vệ trước khi xóa.
{{% /notice %}}

**Xóa AWS Amplify — ứng dụng frontend đã triển khai.**
![Tổng quan ứng dụng Amplify](/images/Screenshot%202026-07-09%20233448.png)

**Xóa ACM — chứng chỉ SSL đang được sử dụng.**
![Tổng quan chứng chỉ ACM](/images/Screenshot%202026-07-09%20233547.png)

**Xóa DocumentDB — cluster đang hoạt động (Healthy).**
![Tổng quan cluster DocumentDB](/images/Screenshot%202026-07-09%20233627.png)

**Xóa Auto Scaling Group đang duy trì.**
![Tổng quan Auto Scaling Group](/images/Screenshot%202026-07-09%20233709.png)

**Xóa Application Load Balancer đang Active.**
![Tổng quan Application Load Balancer](/images/Screenshot%202026-07-09%20233727.png)

**Chọn tất cả EC2 → Instance state → Terminate (delete) instance.**
![Chọn terminate các instance](/images/Screenshot%202026-07-09%20233854.png)

**Xác nhận thu hồi (terminate) toàn bộ instance.**
![Xác nhận terminate instance](/images/Screenshot%202026-07-09%20233859.png)

**Vào VPC → Actions → Delete VPC.**
![Chọn xóa VPC](/images/Screenshot%202026-07-09%20234028.png)

**Nhập "delete" để xác nhận xóa VPC cùng các tài nguyên phụ thuộc (Internet Gateway, Route Table, Security Group...).**
![Xác nhận xóa VPC](/images/Screenshot%202026-07-09%20234544.png)

---

## Kết luận

Qua workshop này, hệ thống **LMS-Management-System** đã được triển khai hoàn chỉnh trên AWS với đầy đủ các lớp: mạng (VPC), bảo mật (Security Group, ACM), tính toán (EC2 + Auto Scaling), cân bằng tải (ALB), cơ sở dữ liệu (DocumentDB Multi-AZ), giao diện (Amplify), giám sát (CloudWatch, CloudTrail) và cảnh báo (SNS). Kiến trúc đảm bảo **tính sẵn sàng cao**, **tự động mở rộng theo tải** và **dễ giám sát**, phù hợp cho một nền tảng học tập trực tuyến thực tế.

</div>
