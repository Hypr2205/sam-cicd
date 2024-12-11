---
title : "Dọn dẹp"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

## Tổng quát

Thông qua các nội dung trên, chúng ta đã được tìm hiểu về Serverless Application Model, cách tạo một serverless với SAMCLI. Chúng ta đã học cách build và deploy mội project SAM thông qua cli và xây dựng CI/CD pipeline bằng SAM pipeline template phục vụ cho quy trình triển khai project một cách hoàn toàn tự động.

## Dọn dẹp

Truy cập CloudFormation console và xoá toàn bộ stack của SAM project
![5](/images/5/deletecf.png)
Truy cập S3 console và xoá các bucket
![5](/images/5/deletes3.png)
Xoá Lambda function
![5](/images/5/deletelambda.png)
