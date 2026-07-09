---
title: "Bản đề xuất"
date: 2026-07-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

<style>
.lms h1{font-size:2.1rem;margin-bottom:.2rem;color:#1c252e}
.lms h2{font-size:1.15rem;font-weight:500;color:#566c88;margin-top:.2rem;border:0;padding:0}
.lms h3{margin-top:2.2rem;padding:.45rem 0 .45rem .9rem;border-left:5px solid #ff9900;color:#233a57;font-size:1.35rem;background:linear-gradient(90deg,rgba(255,153,0,.09),transparent 70%);border-radius:0 6px 6px 0}
.lms p em:only-child{display:inline-block;margin:1rem 0 .35rem;color:#233a57;font-style:normal;font-weight:700;font-size:1.02rem;border-bottom:2px solid #ff9900;padding-bottom:2px}
.lms table{width:100%;border-collapse:collapse;margin:1.1rem 0;font-size:.95rem;box-shadow:0 1px 4px rgba(28,37,46,.1);border-radius:8px;overflow:hidden}
.lms thead th{background:#233a57;color:#fff;font-weight:600;text-align:left;padding:.6rem .8rem}
.lms tbody td{padding:.55rem .8rem;border-top:1px solid #e6ebf2}
.lms tbody tr:nth-child(even){background:#f7f9fc}
.lms tbody tr:last-child{background:rgba(255,153,0,.13);font-weight:600}
.lms img{border-radius:10px;box-shadow:0 4px 14px rgba(28,37,46,.15);border:1px solid #e6ebf2;margin:1.2rem auto;display:block;max-width:100%}
.lms blockquote{border-left:4px solid #ff9900;background:#fff8ef;border-radius:0 8px 8px 0;padding:.7rem 1rem;color:#4a3b23;margin:1.2rem 0}
.lms ul li::marker{color:#ff9900}
.lms ol li::marker{color:#ff9900;font-weight:700}
</style>

<div class="lms">

# LMS-Management-System
## Hệ thống quản lý học tập trực tuyến trên nền tảng AWS với kiến trúc hạ tầng có tính sẵn sàng cao

### 1. Tóm tắt điều hành
LMS-Management-System là hệ thống quản lý học tập trực tuyến (Learning Management System) được xây dựng nhằm cung cấp một nền tảng tập trung cho việc tổ chức khóa học, quản lý người học, phân phối nội dung và theo dõi tiến độ học tập. Hệ thống được triển khai trên AWS theo mô hình hạ tầng có tính sẵn sàng cao (High Availability), sử dụng Application Load Balancer kết hợp Auto Scaling Group phân bổ trên hai vùng khả dụng (Availability Zone) để đảm bảo dịch vụ liên tục ngay cả khi một vùng gặp sự cố. Giao diện web được lưu trữ trên AWS Amplify và phân giải qua CloudFlare, trong khi dữ liệu được lưu trữ an toàn trong Amazon DocumentDB với cơ chế sao chép đa vùng. Toàn bộ hệ thống được giám sát bằng CloudWatch, CloudTrail và cảnh báo qua Amazon SNS, giúp vận hành ổn định và dễ mở rộng.

### 2. Tuyên bố vấn đề
*Vấn đề hiện tại*

Việc dạy và học trực tuyến hiện nay thường phân tán trên nhiều công cụ rời rạc (email, ổ đĩa chia sẻ, ứng dụng chat), gây khó khăn trong việc quản lý khóa học, tài liệu và theo dõi tiến độ người học. Các nền tảng LMS thương mại thường có chi phí bản quyền cao, khó tùy biến và không kiểm soát được dữ liệu. Bên cạnh đó, các hệ thống tự triển khai trên một máy chủ đơn lẻ dễ gặp gián đoạn dịch vụ khi số lượng người dùng tăng cao hoặc khi máy chủ gặp sự cố.

*Giải pháp*

Hệ thống sử dụng kiến trúc web ba lớp (three-tier) trên AWS. Lớp giao diện là ứng dụng web được lưu trữ bởi AWS Amplify, phân giải tên miền và bảo vệ qua CloudFlare, chứng chỉ SSL/TLS do AWS Certificate Manager cấp phát. Lưu lượng người dùng đi qua Internet Gateway đến Application Load Balancer (ALB), sau đó được phân phối tới các máy chủ EC2 nằm trong Auto Scaling Group trải trên hai vùng khả dụng. Dữ liệu ứng dụng được lưu trong Amazon DocumentDB đặt ở các private subnet với cơ chế sao chép Multi-AZ. Amazon CloudWatch thu thập số liệu và nhật ký, kích hoạt cảnh báo qua Amazon SNS gửi email khi có sự cố, còn AWS CloudTrail ghi lại toàn bộ hoạt động phục vụ kiểm toán. Tương tự các LMS phổ biến như Moodle hay Canvas, hệ thống cho phép tạo khóa học, quản lý học viên và tài liệu, nhưng được thiết kế gọn nhẹ, tự chủ về dữ liệu và tối ưu cho quy mô triển khai của nhóm.

*Lợi ích và hoàn vốn đầu tư (ROI)*

Giải pháp cung cấp một nền tảng học tập tập trung, tự chủ về dữ liệu và có khả năng mở rộng theo nhu cầu thực tế. Nhờ Auto Scaling và kiến trúc đa vùng khả dụng, hệ thống duy trì hoạt động liên tục và chỉ trả chi phí theo mức sử dụng thực tế, tránh khoản đầu tư lớn cho bản quyền phần mềm hay máy chủ vật lý. Việc tập trung tài liệu, khóa học và dữ liệu người học vào một hệ thống giúp giảm đáng kể công sức quản lý thủ công, đồng thời tạo tiền đề để mở rộng thêm các tính năng như thi trực tuyến, phân tích học tập hay tích hợp AI. Thời gian hoàn vốn ước tính trong khoảng 6–12 tháng nhờ tiết kiệm chi phí bản quyền và công vận hành.

### 3. Kiến trúc giải pháp
Hệ thống áp dụng kiến trúc hạ tầng có tính sẵn sàng cao trong một Amazon VPC. Người dùng truy cập qua CloudFlare và Internet Gateway, lưu lượng được Application Load Balancer phân phối tới các máy chủ EC2 trong Auto Scaling Group đặt tại public subnet của hai vùng khả dụng. Lớp dữ liệu là Amazon DocumentDB nằm trong private subnet, được sao chép Multi-AZ để đảm bảo an toàn và sẵn sàng. Giao diện web do AWS Amplify lưu trữ, được bảo mật bằng chứng chỉ từ AWS Certificate Manager. CloudWatch, CloudTrail và SNS đảm nhận giám sát, ghi nhật ký và cảnh báo.

![LMS Management System Architecture](/images/742208320_1712520913220808_2976852082227510005_n.png)

*Dịch vụ AWS sử dụng*
- *CloudFlare*: Phân giải DNS và bảo vệ lớp truy cập cho tên miền.
- *AWS Amplify*: Lưu trữ và phân phối ứng dụng web (giao diện người dùng).
- *AWS Certificate Manager*: Cấp phát và quản lý chứng chỉ SSL/TLS.
- *Internet Gateway*: Cổng kết nối giữa Internet và VPC.
- *Application Load Balancer (ALB)*: Phân phối lưu lượng HTTPS tới các máy chủ EC2.
- *Auto Scaling Group*: Tự động tăng/giảm số lượng EC2 theo tải, trải trên 2 vùng khả dụng.
- *Amazon EC2*: Máy chủ chạy backend của hệ thống LMS (đặt tại public subnet).
- *Amazon DocumentDB*: Cơ sở dữ liệu tài liệu (private subnet), sao chép Multi-AZ.
- *Amazon CloudWatch*: Thu thập số liệu, nhật ký và kích hoạt cảnh báo.
- *AWS CloudTrail*: Ghi lại hoạt động của tài khoản phục vụ kiểm toán và bảo mật.
- *Amazon SNS*: Gửi thông báo cảnh báo qua email tới quản trị viên.

*Thiết kế thành phần*
- *Lớp phân giải và bảo mật*: CloudFlare xử lý truy vấn DNS, Certificate Manager cung cấp chứng chỉ SSL/TLS cho kết nối HTTPS (cổng 443).
- *Lớp giao diện*: AWS Amplify lưu trữ ứng dụng web cho người dạy và người học.
- *Lớp cân bằng tải và tính toán*: ALB nhận yêu cầu và chuyển tiếp tới các EC2 trong Auto Scaling Group đặt tại public subnet của hai vùng khả dụng, đảm bảo mở rộng và chịu lỗi.
- *Lớp dữ liệu*: Amazon DocumentDB tại private subnet lưu trữ dữ liệu khóa học, người dùng và tiến độ, với cơ chế sao chép Multi-AZ.
- *Lớp giám sát và cảnh báo*: EC2 gửi số liệu và nhật ký về CloudWatch; khi vượt ngưỡng, CloudWatch kích hoạt CloudWatch Alarm và gửi thông báo qua SNS đến email quản trị. CloudTrail ghi nhận mọi thao tác.

### 4. Triển khai kỹ thuật
*Các giai đoạn triển khai*

Dự án được chia thành 4 giai đoạn:
1. *Nghiên cứu và thiết kế kiến trúc*: Khảo sát các dịch vụ AWS (VPC, ALB, Auto Scaling, DocumentDB, Amplify) và thiết kế kiến trúc tổng thể (1 tháng trước kỳ thực tập).
2. *Tính toán chi phí và kiểm tra tính khả thi*: Dùng AWS Pricing Calculator để ước tính chi phí và đánh giá khả năng đáp ứng (Tháng 1).
3. *Điều chỉnh kiến trúc để tối ưu chi phí/hiệu năng*: Tinh chỉnh cấu hình EC2, ngưỡng Auto Scaling và DocumentDB nhằm cân bằng chi phí và hiệu năng (Tháng 2).
4. *Phát triển, kiểm thử, triển khai*: Lập trình ứng dụng LMS (frontend và backend), cấu hình hạ tầng bằng AWS CDK/CloudFormation, kiểm thử tải và đưa vào vận hành (Tháng 2–3).

*Yêu cầu kỹ thuật*
- *Hạ tầng mạng*: Amazon VPC với public subnet và private subnet trên hai vùng khả dụng, Internet Gateway, bảng định tuyến và Security Group phù hợp.
- *Lớp ứng dụng*: Máy chủ EC2 (ví dụ t3.small/t3.medium) chạy backend, đặt trong Auto Scaling Group phía sau ALB. Ứng dụng web triển khai trên AWS Amplify.
- *Lớp dữ liệu*: Amazon DocumentDB cấu hình cụm Multi-AZ để đảm bảo tính sẵn sàng và sao lưu.
- *Bảo mật và giám sát*: Chứng chỉ SSL/TLS từ Certificate Manager, giám sát bằng CloudWatch, ghi nhật ký bằng CloudTrail, cảnh báo qua SNS. Sử dụng AWS CDK/CloudFormation để triển khai hạ tầng dưới dạng mã (Infrastructure as Code).

### 5. Lộ trình & Mốc triển khai
- *Trước thực tập (Tháng 0)*: 1 tháng nghiên cứu dịch vụ AWS và phác thảo kiến trúc.
- *Thực tập (Tháng 1–3)*:
    - Tháng 1: Học AWS, dựng VPC và hạ tầng nền tảng.
    - Tháng 2: Thiết kế, điều chỉnh kiến trúc và phát triển ứng dụng.
    - Tháng 3: Kiểm thử, triển khai và đưa vào sử dụng.
- *Sau triển khai*: Theo dõi vận hành, tối ưu chi phí và bổ sung tính năng trong vòng 1 năm.

### 6. Ước tính ngân sách
Có thể xem chi phí trên [AWS Pricing Calculator](https://calculator.aws/#/) (cập nhật liên kết ước tính của bạn).
Hoặc tải [tệp ước tính ngân sách](../attachments/budget_estimation.pdf).

*Chi phí hạ tầng (phương án có tính sẵn sàng cao — Multi-AZ)*

Ước tính theo giá tham khảo khu vực **US East (N. Virginia — us-east-1)**, chạy liên tục 24/7 (730 giờ/tháng).

| Dịch vụ | Cấu hình giả định | Đơn giá tham khảo | Chi phí/tháng (USD) |
|---|---|---|---|
| Amazon EC2 | 2 × `t3.medium` (2 AZ, On-Demand) | $0,0416/giờ | 60,74 |
| Application Load Balancer | 1 ALB + lưu lượng nhỏ (~1 LCU) | $0,0225/giờ + LCU | 22,27 |
| Amazon DocumentDB | 2 × `db.t3.medium` (Multi-AZ) + 10 GB lưu trữ | $0,078/giờ + $0,10/GB | 114,88 |
| Amazon DocumentDB I/O | ~10 triệu yêu cầu I/O | $0,20/triệu | 2,00 |
| AWS Amplify | Hosting + build + băng thông nhỏ | theo mức dùng | 3,00 |
| Amazon CloudWatch | Metrics, logs, alarms cơ bản | theo mức dùng | 4,00 |
| AWS CloudTrail | 1 trail (management events) | miễn phí | 0,00 |
| Amazon SNS | Cảnh báo email (< 1.000 email) | trong gói miễn phí | 0,00 |
| Data Transfer Out | ~10 GB/tháng (trong 100 GB miễn phí) | $0,09/GB (sau mức free) | 0,00 |
| CloudFlare / Certificate Manager | DNS (gói Free) + chứng chỉ SSL/TLS | miễn phí | 0,00 |
| **Tổng cộng** | | | **≈ 206,89/tháng** |

{{% notice info %}}
💰 **Tổng chi phí ước tính:** ≈ **206,89 USD/tháng** — ≈ **2.482,68 USD/12 tháng**.
{{% /notice %}}

*Phương án tiết kiệm (môi trường thử nghiệm / dev)*

Nếu chưa cần tính sẵn sàng cao đầy đủ, có thể giảm chi phí bằng cách dùng `t3.small` và DocumentDB một node:

| Dịch vụ | Cấu hình | Chi phí/tháng (USD) |
|---|---|---|
| Amazon EC2 | 2 × `t3.small` | 30,37 |
| Application Load Balancer | 1 ALB | 22,27 |
| Amazon DocumentDB | 1 × `db.t3.medium` (single-AZ) + 10 GB | 57,94 |
| Các dịch vụ khác (Amplify, CloudWatch, SNS…) | như trên | ~7,00 |
| **Tổng cộng** | | **≈ 117,58/tháng** |

> *Lưu ý:* Đây là con số **ước tính tham khảo**; đơn giá AWS thay đổi theo khu vực và thời điểm. Bạn nên chạy [AWS Pricing Calculator](https://calculator.aws/#/) theo cấu hình thực tế (loại/số lượng EC2, số giờ chạy, cấu hình DocumentDB, lưu lượng truy cập) để có con số chính xác, sau đó cập nhật lại bảng và liên kết ước tính ở trên. Chi phí chủ yếu đến từ **Amazon DocumentDB** và **Amazon EC2** do chạy liên tục 24/7 — có thể tối ưu bằng Savings Plans/Reserved Instances hoặc tắt bớt tài nguyên ngoài giờ cao điểm.

### 7. Đánh giá rủi ro
*Ma trận rủi ro*
- Sự cố một vùng khả dụng: Ảnh hưởng cao, xác suất thấp.
- Tăng đột biến số người dùng: Ảnh hưởng trung bình, xác suất trung bình.
- Vượt ngân sách: Ảnh hưởng trung bình, xác suất trung bình.
- Rủi ro bảo mật (truy cập trái phép): Ảnh hưởng cao, xác suất thấp.

*Chiến lược giảm thiểu*
- Tính sẵn sàng: Triển khai đa vùng khả dụng và DocumentDB Multi-AZ để chịu lỗi.
- Tải cao: Sử dụng Auto Scaling Group tự động mở rộng số lượng EC2 theo nhu cầu.
- Chi phí: Thiết lập cảnh báo ngân sách AWS Budgets và tối ưu loại/số lượng instance.
- Bảo mật: Đặt DocumentDB trong private subnet, dùng Security Group chặt chẽ, HTTPS bắt buộc và ghi nhật ký bằng CloudTrail.

*Kế hoạch dự phòng*
- Sao lưu tự động DocumentDB để khôi phục khi cần.
- Sử dụng CloudFormation/CDK để tái tạo nhanh toàn bộ hạ tầng khi gặp sự cố.

### 8. Kết quả kỳ vọng
*Cải tiến kỹ thuật*: Một nền tảng LMS tập trung, có tính sẵn sàng cao, tự động mở rộng theo tải và được giám sát đầy đủ, thay thế cho các công cụ rời rạc.
*Giá trị dài hạn*: Nền tảng làm cơ sở để phát triển thêm các tính năng nâng cao (thi trực tuyến, phân tích học tập, tích hợp AI) và có thể tái sử dụng cho các dự án đào tạo trong tương lai.

</div>
