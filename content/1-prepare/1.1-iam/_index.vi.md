---
title : "Tạo IAM user"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.1. </b> "
---

## Tạo user

- Vào IAM console
- Chọn **Users** -> **Create user**
![iam](/images/1/1.1/iam-console.png)
- Trong phần _Specify user details_
  - Username: đặt tên cho user
  - Tích vào **Provide user access to the AWS Management Console** và chọn **I want to create an IAM user**
  - Chọn **Custom password** và đặt mật khẩu dăng nhập
  - Bỏ chọn ô **Users must create a new password at next sign-in**
![iam](/images/1/1.1/user-details.png)
- Ở phần _Set permissions_
  - Chọn **Attach policies directly**
  - Tìm và chọn **AdministratorAccess**
![iam](/images/1/1.1/user-policies.png)

## Tạo access key

- Sau khi tạo hoàn tất, quay lại danh sách user, nhấn chọn user vừa tạo, chuyển qua tab _Security credentials_, kéo xuống dưới tìm phần _Access key_, chọn **Create access key**
![iam](/images/1/1.1/credentials.png)
![iam](/images/1/1.1/key.png)
- Trong giao diện tạo access key
  - Chọn usecase CLI
  - Tích chọn ô **Confirmation**
  - Chọn **Next** -> **Create access key**
![iam](/images/1/1.1/usecase.png)
- Ở phần _Retrieve access key_, copy và lưu lại access key và secret key hoặc download file csv
![iam](/images/1/1.1/get-key.png)
