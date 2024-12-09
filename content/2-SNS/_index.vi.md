---
title : "Tạo SNS Topic"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

## Tạo SNS topic

- Truy cập SNS Console
![sns console](/images/2-sns/sns-console.png)

- Chọn **Topics** -> **Create topic**
![sns console](/images/2-sns/create-topic.png)

- Tạo topic **ResourceTagMissingNotification**
![sns console](/images/2-sns/topic-details.png)

## Tạo email subscription cho topic

- Trong topic vừa tạo, chọn **Subscriptions** -> **Create subscription**
![subscription](/images/2-sns/create-subscription.png)

- Trong phần _Create subscription_:
  - Chọn **Topic ARN** là topic vừa tạo
  - **Protocol**: Email
  - **Endpoint**: Địa chỉ email muốn nhận thông báo
![subscription details](/images/2-sns/subscription-details.png)

- Sau khi tạo subscription, truy cập địa chỉ email đã đăng ký để xác nhận
![confirmation email](/images/2-sns/confirmation-email.png)
![confirmed](/images/2-sns/confirmed.png)
![confirmed status](/images/2-sns/confirmed-status.png)
