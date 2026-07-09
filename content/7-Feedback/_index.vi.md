---
title: "Chia sẻ & Đóng góp ý kiến"
date: 2026-07-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

# Chia sẻ & Đóng góp ý kiến
---

> [!IMPORTANT]
> ### 🌟 Lời ngỏ
> Trang này tổng hợp những cảm nhận, đánh giá khách quan và đề xuất cá nhân của mình sau hành trình tham gia chương trình **First Cloud AI Journey (FCAJ)** và thực tập tại **Amazon Web Services Vietnam**. Đây không chỉ là một báo cáo, mà là những đúc kết chân thực nhất từ trải nghiệm thực tế.

## 1. Nhìn lại hành trình FCAJ

Nhìn lại khoảng thời gian thực tập, mình cảm thấy tự hào về những cột mốc đã đạt được. Từ những bỡ ngỡ ban đầu, mình đã từng bước chinh phục các thử thách — từ việc học nền tảng, đi sâu các dịch vụ nâng cao, cho đến việc **tự tay thiết kế và triển khai một hệ thống hoàn chỉnh trên AWS**:

{{< mermaid >}}
timeline
    title Hành trình thực tập AWS Cloud (FCAJ)
    Onboarding : Làm quen môi trường làm việc chuyên nghiệp
               : Tiếp cận quy trình và tài liệu chuẩn AWS
    Nền tảng : Làm chủ IAM, EC2 và mạng ảo VPC
             : Lưu trữ với Amazon S3 và CloudFront
             : Cơ sở dữ liệu RDS và DynamoDB
    Nâng cao : Serverless với Lambda và API Gateway
             : Tự động hóa CI/CD với CodePipeline
             : Giám sát hệ thống bằng CloudWatch và CloudTrail
             : Hạ tầng dạng mã (IaC) với CloudFormation và CDK
    Dự án thực chiến : Thiết kế và triển khai hệ thống LMS-Management-System
                     : Kiến trúc sẵn sàng cao (ALB, Auto Scaling, EC2, DocumentDB Multi-AZ)
                     : Frontend trên AWS Amplify, giám sát và cảnh báo qua SNS
    Chia sẻ và Cộng đồng : Viết và xuất bản 3 blog kỹ thuật cá nhân
                         : Tham gia 4 sự kiện công nghệ AWS
{{< /mermaid >}}

---

## 2. Những điểm sáng đáng giá

### 🎯 Trải nghiệm thực chiến & Sự tin tưởng (Empowerment)
Điều mình tâm đắc nhất tại FCAJ không phải là quy mô của các dự án, mà là **sự tin tưởng và trao quyền**. Khác với định kiến "thực tập sinh chỉ làm việc vặt", tại đây mình được trực tiếp phụ trách những phần việc quan trọng. Điển hình là việc **tự tay thiết kế và triển khai hệ thống LMS-Management-System** — một nền tảng quản lý học tập trực tuyến chạy trên kiến trúc AWS có tính sẵn sàng cao (VPC, EC2, Application Load Balancer, Auto Scaling, Amazon DocumentDB Multi-AZ, AWS Amplify cùng bộ giám sát CloudWatch/CloudTrail/SNS). Cảm giác nhìn thấy hệ thống mình xây dựng vận hành trơn tru, tự động mở rộng theo tải mang lại động lực cực kỳ to lớn.

### 👥 Văn hóa chia sẻ & Hỗ trợ (Mentorship & Community)
- **Mentorship chất lượng cao:** Các Mentor không "cầm tay chỉ việc", mà hướng dẫn phương pháp tư duy (troubleshooting) để mình tự tìm ra giải pháp. Cách tiếp cận này giúp mình rèn luyện khả năng độc lập và giải quyết vấn đề vượt bậc.
- **Team Admin nhiệt huyết:** Luôn lắng nghe, theo sát và tạo điều kiện tốt nhất để thực tập sinh tập trung vào chuyên môn.
- **Cộng đồng cởi mở:** Môi trường khuyến khích tranh luận kỹ thuật và chia sẻ kiến thức, không có khoảng cách giữa người mới và chuyên gia. Mình cũng có cơ hội mở rộng góc nhìn qua **4 sự kiện công nghệ** (AWS Community Day Vietnam, Workshop Voice AI Agent "Hera", AWS Student Builder Group - Kiro Spec Driven Development và FCAJ - HUTECH Kickoff).

### 📚 Lộ trình đào tạo (Training Roadmap) bài bản
Lộ trình đi từ nền tảng (Compute, Networking, Storage) đến nâng cao (Serverless, IaC, CI/CD, Monitoring) được thiết kế cực kỳ logic. Các bài Lab bám sát thực tế doanh nghiệp giúp thu hẹp khoảng cách giữa lý thuyết học thuật và môi trường làm việc thực tế, đồng thời tạo tiền đề để mình vận dụng ngay vào dự án LMS.

### ✍️ Rèn kỹ năng viết & chia sẻ kỹ thuật
Việc viết và xuất bản **3 blog kỹ thuật** giúp mình củng cố kiến thức và luyện khả năng trình bày:
1. Xây dựng hệ thống cấu hình đa đối tượng thuê (multi-tenant) với các mẫu lưu trữ được gắn thẻ.
2. Kết nối an toàn AWS DevOps Agent với các dịch vụ riêng tư trong VPC.
3. Giám sát chủ động Amazon Redshift Serverless bằng AWS Lambda và cảnh báo Slack.

---

## 3. Đóng góp ý kiến & Đề xuất cải thiện

Để chương trình FCAJ các khóa sau ngày càng hoàn thiện và mang lại trải nghiệm tốt hơn cho các bạn sinh viên, mình xin đóng góp một vài ý kiến nhỏ:

> [!TIP]
> ### 💡 Tối ưu hóa tuần Onboarding
> Khối lượng kiến thức, tài liệu và quy trình trong tuần đầu tiên là rất lớn (đặc biệt với sinh viên mới).
> **Đề xuất:** Xây dựng một **Reading Roadmap (Sơ đồ đọc tài liệu)** chi tiết theo từng ngày hoặc checklist cụ thể cho tuần đầu. Việc này sẽ giúp các bạn thực tập sinh phân bổ thời gian hợp lý, không bị "ngợp" và bắt nhịp dự án nhanh hơn.

> [!TIP]
> ### 💡 Bổ sung các phiên Mock Interview & Review CV
> Kỹ năng chuyên môn đã được rèn luyện rất tốt, tuy nhiên kỹ năng trình bày bản thân cũng cực kỳ quan trọng.
> **Đề xuất:** Ban tổ chức có thể tổ chức thêm các buổi Mock Interview (Phỏng vấn thử) hoặc Review CV 1-1 với góc nhìn từ nhà tuyển dụng/Senior Engineer ở giai đoạn cuối kỳ thực tập, giúp sinh viên tự tin hơn khi bước ra thị trường lao động.

---

## 4. Lời kết & Tri ân

FCAJ thực sự là một **bệ phóng hoàn hảo** cho những ai đam mê công nghệ Điện toán đám mây. Môi trường làm việc chuyên nghiệp, những bài học thực tế, và sự tận tâm của các anh chị đi trước đã giúp mình định hình rõ ràng **Lộ trình sự nghiệp (Career Path)**.

> [!IMPORTANT]
> Mình xin gửi lời tri ân chân thành nhất đến:
> - **Đội ngũ First Cloud AI Journey** và các anh chị Admin vì một chương trình quá tuyệt vời.
> - **Các Mentor** đã luôn kiên nhẫn đồng hành, chữa từng lỗi nhỏ và truyền cảm hứng cho mình.
> - **Amazon Web Services Vietnam** đã tạo ra một môi trường thực tập đẳng cấp và đầy giá trị.

Mình rất hy vọng sẽ có cơ hội được tiếp tục đồng hành, cống hiến cho công ty ở những vai trò chính thức trong tương lai. **Cảm ơn vì một hành trình đáng nhớ!**
