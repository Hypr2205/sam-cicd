---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

Đây là một workshop đơn giản về quản lý các tài nguyên trên AWS thông qua việc thiết lập các tag cho tài nguyên được tạo ra. Mô hình tổng quan như sau:

1. EventBridge (CloudWatch event) sẽ kích hoạt định kỳ để kiểm tra các tài nguyên (EC2, S3...)
2. Lambda: Được kích hoạt bởi CloudWatch event khi phát hiện 1 tài nguyên thiếu tag yêu cầu
3. SNS Topic: Gửi email thông báo

![resoure-management](/images/resource-management.png)
