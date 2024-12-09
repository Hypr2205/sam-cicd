---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

- Xoá 2 instance EC2:
  - Trong EC2 console, chọn 2 instace test
  - Chọn **Instance state** -> **Terminate instance**
![tẻminate](/images/6-clean/terminate-instance.png)

- Xoá CloudWatch log group:
  - Vào CloudWatch console, chọn **Logs** -> **Log groups**
  - Chọn log group **/aws/lambda/CheckResourceTags**
  - **Action** -> **Delete log group**
![lg](/images/6-clean/delete-loggroup.png)

- Vào EventBridge console
  - Chuyển sang mục **Scheduler** -> **Schedules**
  - Chọn **CheckResourceTagsRule**
  - Chọn **Delete**
![clean rule](/images/6-clean/clean-rule.png)

- Vào SNS console
  - Chuyển sang mục **Topics**, chọn topic **ResourceTagMissingNotification**
  - Chọn **Delete**
![topic](/images/6-clean/delete-topic.png)

- Vào Lambda console, chuyển sang mục **Functions**
  - Chọn function **CheckResourceTags**
  - Chọn **Actions** -> **Delete**
![lambda](/images/6-clean/delete-lambda.png)
