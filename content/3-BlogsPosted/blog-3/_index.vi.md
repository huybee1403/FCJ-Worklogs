---
title: "Blog 3"
date: 2026-04-20
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Giám sát chủ động Amazon Redshift Serverless bằng AWS Lambda và cảnh báo Slack

---

> [!IMPORTANT]
> ### 🎯 Mục tiêu bài viết
> Bài viết hướng dẫn cách xây dựng một **giải pháp giám sát chủ động (Proactive Monitoring)** cho **Amazon Redshift Serverless** bằng **AWS Lambda**, giúp tự động phát hiện các bất thường về hiệu suất và gửi **cảnh báo theo thời gian thực đến Slack**. Giải pháp giúp nhóm vận hành nhanh chóng xử lý sự cố, tối ưu hiệu suất và kiểm soát chi phí mà không cần theo dõi dashboard liên tục.
>
> * **Bài viết gốc đăng tải tại:** *[AWS Study Group](https://awsstudygroup.com/2026/05/14/giam-sat-chu-dong-cho-amazon-redshift-serverless-bang-aws-lambda-va-canh-bao-slack/?fbclid=IwY2xjawS0WyVleHRuA2FlbQIxMABicmlkETBXUWJOcmRwd1dmbGluRG8zc3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHjQNB21aCPpxAiaELPOoVMVWuMuwbuL5UeWGcAGbi2tfUpmErSiw8GN2KJlQ_aem_A_72VJwE6sRyKIvDmsfpLg)*

---

## 1. Giới thiệu

**Amazon Redshift Serverless** giúp đơn giản hóa việc triển khai kho dữ liệu phân tích bằng cách loại bỏ nhu cầu quản lý cơ sở hạ tầng, cho phép các nhóm tập trung vào xử lý dữ liệu thay vì vận hành hệ thống.

Tuy nhiên, ngay cả trong môi trường serverless, các vấn đề như:

- Truy vấn bị xếp hàng (Queued Queries).
- Truy vấn chạy quá lâu.
- Gia tăng đột biến năng lực tính toán (RPUs).
- Mức sử dụng tài nguyên vượt ngưỡng.

vẫn có thể ảnh hưởng đến hiệu suất và làm tăng chi phí nếu không được phát hiện kịp thời.

Mặc dù Amazon Redshift Serverless cung cấp các dashboard giám sát tích hợp, việc gửi cảnh báo trực tiếp đến **Slack** giúp nhóm vận hành phản ứng nhanh hơn và không cần liên tục theo dõi dashboard.

---

## 2. Giải pháp: Giám sát chủ động bằng AWS Lambda

Giải pháp sử dụng các dịch vụ AWS để tự động thu thập các chỉ số hiệu suất của Amazon Redshift Serverless, đánh giá chúng theo các ngưỡng do người dùng cấu hình và gửi cảnh báo khi phát hiện bất thường.

Các dịch vụ chính bao gồm:

- **Amazon EventBridge** để kích hoạt quá trình giám sát theo lịch.
- **AWS Lambda** để thu thập và đánh giá các chỉ số.
- **Amazon CloudWatch** để lấy các metric hệ thống.
- **Amazon Redshift Data API** để truy vấn thông tin từ Redshift.
- **Amazon SNS** để phát hành thông báo.
- **Amazon Q Developer in Chat applications** để gửi cảnh báo đến Slack.
- **Amazon CloudWatch Logs** để lưu nhật ký thực thi.

---

## 3. Kiến trúc tổng thể

![Kiến trúc giám sát Amazon Redshift Serverless](/images/733471444_2463215147523527_6193328843618823246_n.jpg)

### Luồng hoạt động (End-to-End Flow)

| Bước | Thành phần | Mô tả |
| :---: | :--- | :--- |
| **1** | **Amazon EventBridge → AWS Lambda** | EventBridge kích hoạt Lambda theo lịch định kỳ (mặc định 15 phút/lần trong giờ làm việc). |
| **2** | **AWS Lambda → CloudWatch & Redshift Data API** | Lambda thu thập các chỉ số như truy vấn chờ, truy vấn đang chạy, RPUs, dung lượng lưu trữ, số lượng bảng, kết nối cơ sở dữ liệu và các truy vấn chạy chậm. |
| **3** | **AWS Lambda** | So sánh các chỉ số thu thập được với các ngưỡng hiệu suất do người dùng cấu hình. |
| **4** | **AWS Lambda → Amazon SNS** | Khi phát hiện chỉ số vượt ngưỡng, Lambda gửi thông báo đến SNS Topic. |
| **5** | **Amazon SNS → Amazon Q Developer in Chat applications → Slack** | Amazon Q Developer in Chat applications chuyển cảnh báo đến kênh Slack được chỉ định. |
| **6** | **AWS Lambda → Amazon CloudWatch Logs** | Nhật ký thực thi Lambda được lưu trong CloudWatch Logs để phục vụ giám sát và khắc phục sự cố. |

*Giải pháp giúp tự động giám sát Amazon Redshift Serverless, phát hiện sớm các bất thường về hiệu suất và gửi cảnh báo trực tiếp đến Slack, giúp nhóm vận hành phản ứng nhanh trước khi ảnh hưởng đến người dùng hoặc quy trình phân tích dữ liệu.*

---

## 4. Lợi ích của giải pháp

> [!TIP]
> ### 🚀 Giám sát chủ động và tối ưu vận hành
>
> Giải pháp mang lại nhiều lợi ích trong việc vận hành Amazon Redshift Serverless:
>
> 1. **Phát hiện sớm các vấn đề hiệu suất**: Theo dõi liên tục các chỉ số quan trọng và cảnh báo ngay khi vượt ngưỡng.
> 2. **Tự động hóa quy trình giám sát**: Không cần theo dõi dashboard liên tục nhờ EventBridge và Lambda thực hiện theo lịch.
> 3. **Thông báo theo thời gian thực**: Cảnh báo được gửi trực tiếp đến Slack, giúp nhóm phản ứng nhanh hơn.
> 4. **Chi phí thấp và hoàn toàn serverless**: Giải pháp chỉ sử dụng các dịch vụ serverless như Lambda, EventBridge và SNS, không cần quản lý hạ tầng.
> 5. **Khả năng quan sát đầy đủ**: Nhật ký thực thi được lưu trong CloudWatch Logs, hỗ trợ kiểm tra, theo dõi và khắc phục sự cố hiệu quả.