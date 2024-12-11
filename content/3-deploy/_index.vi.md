---
title : "Deploy project theo cách thủ công"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

## Build

- Để build một SAM project, ta dùng lệnh `sam build`, câu lệnh này sẽ tìm các file manifest (vd: requirements.txt) và tạo các deployment artifact. Artifact là các output của quy trình build, có thể là các file nén (zip, tar,...), container image hoặc các file nhị phân. Các artifact sẽ được triển khai lên các môi trường vận hành (dev, staging, production...). Đối với các project SAM, các artifact sẽ được lưu trữ trong một S3 bucket
- Build app `hello_world` bằng câu lệnh `sam build`, sau quá trình sẽ tạo ra artifact là folder `.aws-sam/build`
![3](/images/3/build-out.png)
![3](/images/3/build-artifact.png)

## Deploy

- Để deploy một project SAM, sử dụng câu lệnh `sam deploy`. Câu lệnh này sẽ tạo một CloudFormation stack và deploy project. Câu lệnh sẽ sử dụng file `template.yml` để tạo CloudFormation stack
- Khi deploy project lần đầu, nên sử dụng thêm flag `--guided` cho câu lệnh build để ghi lại các cấu hình cho các lần deploy sau vào file `samconfig.toml`. Sau này khi deploy chỉ cần câu lệnh `sam build` nếu không có thay đổi trong cấu hình deploy
![3](/images/3/deploy.png)
- Output sau khi deploy hoàn tất:
![3](/images/3/deploy-out.png)

## Kiểm tra trên AWS Console

1. Kiểm tra IAM Role sẽ thấy một role được tạo ra cho Lambda
![3](/images/3/role.png)
2. Vào Lambda console sẽ thấy hàm Lambda với runtime là Python được deploy dưới dạng zip
![3](/images/3/lambda.png)
3. Vào S3 console sẽ thấy một Bucket được tạo ra, chuyển hướng đến bucket sẽ thấy folder `sam-workshop` là nơi lưu trữ artifact và file template
![3](/images/3/s3.png)
![3](/images/3/artifact.png)
4. CloudFormation stack
![3](/images/3/cfs.png)
5. Api gateway
![3](/images/3/apigw.png)
6. Dùng lệnh curl gọi đến API endpoint
![3](/images/3/test-endpoint.png)
