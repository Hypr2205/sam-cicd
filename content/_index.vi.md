---
title : "Quản lý tài nguyên trên AWS thông qua tag với EventBridge"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
## Tổng quan

Workshop tập trung vào việc sử dụng AWS EventBridge và Lambda nhằm tự động hóa quy trình quản lý tài nguyên dựa trên tag. Thông qua cơ chế kích hoạt sự kiện định kỳ, EventBridge quét các tài nguyên, phát hiện và cảnh báo nếu thiếu các tag bắt buộc. Tag là một cặp key-value giúp nhóm và phân loại tài nguyên trên AWS theo nhiều trường hợp khác nhau (môi trường, dự án, mục đích sử dụng...)

## Nội dung

1. [Giới thiệu](1-Introduce/)
2. [Tạo SNS topic](2-SNS/)
3. [Tạo Lambda function](3-lambda/)
4. [Tạo EventBridge envent](4-cloudwatch/)
5. [Kiểm tra kết quả](5-test/)
6. [Dọn dẹp tài nguyên](6-clean/)
