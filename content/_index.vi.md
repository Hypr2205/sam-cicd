---
title : "Serverless CI/CD Workshop"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

## Tổng quan

- Trong workshop này, chúng ta sẽ tìm hiểu về cách sử dụng Serverless Application Model (SAM) để phát triển serverless api và xây dựng CI/CD pipeline giúp tự động hoá quy trình triển khai sản phẩm

- AWS SAM (Serverless Application Model) là một framework mã nguồn mở được thiết kế để đơn giản hóa quá trình phát triển và triển khai các ứng dụng serverless trên AWS. Nó cung cấp một cú pháp gọn gàng và dễ hiểu để xác định các thành phần của ứng dụng serverless như các hàm Lambda, API Gateway, cơ sở dữ liệu...

- Tại sao sử dụng AWS SAM?
  - Đơn giản hóa quá trình phát triển: SAM giúp lập trình viên tập trung vào phát triển logic nghiệp vụ của ứng dụng thay vì phải lo lắng về việc cấu hình chi tiết các tài nguyên AWS
  - Với cú pháp rõ ràng và các công cụ hỗ trợ mạnh mẽ, SAM giúp quá trình xây dựng và triển khai ứng dụng nhanh hơn
  - Tích hợp chặt chẽ với AWS: SAM được xây dựng đặc biệt cho AWS, vì vậy nó hoạt động liền mạch với các dịch vụ của AWS như Lambda, API Gateway, DynamoDB,...
  - Dễ dàng quản lý: quản lý toàn bộ ứng dụng serverless thông qua một tập tin cấu hình duy nhất
  - Mở rộng: SAM được xây dựng dựa trên AWS CloudFormation, vì vậy có thể tận dụng tất cả các tính năng của CloudFormation để quản lý tài nguyên AWS

- Các thành phần chính của AWS SAM
  - Templates: Các tệp YAML hoặc JSON chứa định nghĩa của ứng dụng serverless, bao gồm các hàm Lambda, API Gateway, cơ sở dữ liệu và các tài nguyên AWS khác
  - AWS SAM CLI: Một công cụ dòng lệnh giúp tạo, xây dựng, đóng gói và triển khai các ứng dụng SAM

## Nội dung

1. [Chuẩn bị](1-prepare/)
2. [Tạo project SAM](2-create-sam/)
3. [Deploy project thủ công](3-deploy/)
4. [Xây dựng CI/CD pipeline](4-cicd/)
5. [Tổng kết & dọn dẹp](5-final/)
