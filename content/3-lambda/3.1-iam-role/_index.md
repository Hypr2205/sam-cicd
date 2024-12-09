---
title : "Create new IAM role for Lambda function"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

- Access IAM console
![iam](/images/3-lambda/iam-console.png)

- **Roles** -> **Create role**
![iam](/images/3-lambda/create-role.png)

- At _Trusted entity_ section:
  - **Trusted entity type**: AWS servcie
  - **Usecase**: Lambda
![trusted entity](/images/3-lambda/iam-trusted-entity.png)

- Attach policies:
![permission](/images/3-lambda/permissions.png)
