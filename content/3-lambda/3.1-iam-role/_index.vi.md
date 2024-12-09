---
title : "Tạo IAM role"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

- Truy cập IAM Console
![iam](/images/3-lambda/iam-console.png)

- Chọn **Roles** -> **Create role**
![iam](/images/3-lambda/create-role.png)

- Trong phần _Trusted entity_:
  - **Trusted entity type**: AWS servcie
  - **Usecase**: Lambda
![trusted entity](/images/3-lambda/iam-trusted-entity.png)

- Chọn các permission sau:
![permission](/images/3-lambda/permissions.png)
