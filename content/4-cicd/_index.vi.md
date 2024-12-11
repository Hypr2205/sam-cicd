---
title : "Deploy project với Github Actions"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

Trong phần trước, chúng ta đã build và deploy project SAM một cách thủ công, nhược điểm của cách này là mỗi khi có thay đổi về code sẽ phải chạy lại các câu lệnh `sam build`, `sam deploy` hoặc `sam deploy --guided` nếu có thay đổi về cấu hình deploy, việc này làm tốn thời gian và phải thực hiện các công việc lặp đi lặp lại và có thể xảy ra lỗi trong quá trình. Để khắc phục các nhược điểm trên, trong phần này chúng ta sẽ sử dụng Github Actions để xây dựng một quy trình deploy một cách hoàn toàn tự động, giảm thiểu các lỗi phát sinh và các thao tác trùng lặp

## Tạo Git repo

- Đăng nhập vào tài khoản Github và tạo một repo mới tên là **aws-sam-workshop**
![4](/images/4/create-repo.png)
- Ở góc trên bên phải, nhấn vào user avatar, chọn **Settings** -> **Developer settings** -> **Personal access token** -> **Token (classic)** -> **Generate new token**
![4](/images/4/token.png)
- Trong phần tạo token, đặt tên token & chọn scope `repo` và `workflows`. Sau khi tạo copy và lưu lại token
![4](/images/4/scope.png)
- Đẩy project workshop lên repo

```bash
git init
echo -e "\n\n.aws-sam" >> .gitignore
echo -e "samconfig.toml" >> .gitignore
echo -e "target" >> .gitignore
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/<your_github_username>/aws-sam-workshop.git
git push -u origin main
```

## Tạo pipeline

Chúng ta sẽ cùng tạo 1 workflow với 2 stage dev và produciton sử dụng SAM pipeline template

### 1. Tạo stage dev cho pipeline

Tại project `sam-workshop`, chạy câu lệnh sau:

```bash
sam pipeline bootstrap --stage dev
```

Câu lệnh sẽ tạo ra output như sau:

```bash
sam pipeline bootstrap generates the required AWS infrastructure resources to connect
to your CI/CD system. This step must be run for each deployment stage in your pipeline,
prior to running the sam pipeline init command.

We will ask for [1] stage definition, [2] account details, and
[3] references to existing resources in order to bootstrap these pipeline resources.

[1] Stage definition
Stage configuration name: dev

[2] Account details
The following AWS credential sources are available to use.
To know more about configuration AWS credentials, visit the link below:
https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html
        1 - Environment variables (not available)
        2 - default (named profile)
        q - Quit and configure AWS credentials
Select a credential source to associate with this stage: 2
Associated account 381492023411 with configuration dev.

Enter the region in which you want these resources to be created [ap-southeast-1]:
Select a user permissions provider:
        1 - IAM (default)
        2 - OpenID Connect (OIDC)
Choice (1, 2): 2
Select an OIDC provider:
        1 - GitHub Actions
        2 - GitLab
        3 - Bitbucket
Choice (1, 2, 3): 1
Enter the URL of the OIDC provider [https://token.actions.githubusercontent.com]: <Enter>
Enter the OIDC client ID (sometimes called audience) [sts.amazonaws.com]: <Enter>
Enter the GitHub organization that the code repository belongs to. If there is no organization enter your username instead: <your_github_username>
Enter GitHub repository name: aws-sam-workshop
Enter the name of the branch that deployments will occur from [main]: <Enter>    

[3] Reference application build resources
Enter the pipeline execution role ARN if you have previously created one, or we will create one for you []: <Enter>
Enter the CloudFormation execution role ARN if you have previously created one, or we will create one for you []: <Enter>
Please enter the artifact bucket ARN for your Lambda function. If you do not have a bucket, we will create one for you []: <Enter>
Does your application contain any IMAGE type Lambda functions? [y/N]: <Enter>

[4] Summary
Below is the summary of the answers:
        1 - Account: 381492023411
        2 - Stage configuration name: dev
        3 - Region: ap-southeast-1
        4 - OIDC identity provider URL: https://token.actions.githubusercontent.com
        5 - OIDC client ID: sts.amazonaws.com
        6 - GitHub organization: Hypr2205
        7 - GitHub repository: aws-sam-workshop
        8 - Deployment branch:  main
        9 - Pipeline execution role: [to be created]
        10 - CloudFormation execution role: [to be created]
        11 - Artifacts bucket: [to be created]
        12 - ECR image repository: [skipped]
Press enter to confirm the values above, or select an item to edit the value: <Enter>
The following resources were created in your account:
        - Pipeline execution role
        - CloudFormation execution role
        - Artifact bucket
        - IAM OIDC Identity Provider
View the definition in .aws-sam\pipeline\pipelineconfig.toml,
run sam pipeline bootstrap to generate another set of resources, or proceed to
sam pipeline init to create your pipeline configuration file.
```

Kiểm tra CloudFormation sẽ thấy một stack mới được tạo ra cho stage dev
![4](/images/4/cfdev.png)

### 2. Tạo stage production cho pipeline

```bash
sam pipeline bootstrap --stage prod
```

Các tuỳ chọn tương tự như pipeline dev. Lúc này khi quay lại CloudFormation sẽ thấy một stack mới được tạo ra dành cho stage production

### 3. Tạo Github actions

```bash
sam pipeline init
```

![4](/images/4/pipeline.png)

Sau khi hoàn tất quá trình sẽ tạo ra Github actions workflow ở file `.github/workflows/pipeline.yaml`

## Deploy và test CI/CD

```bash
g add .
g commit -m "config: generate action workflow with SAM pipeline"
git push -u origin main
```

Truy cập repo trên Github, chuyển qua tab **Actions** để kiểm tra và chờ pipeline hoàn thành
![4](/images/4/pipeline-status.png)

Trở lại CloudFormation console để kiểm tra kết quả
![4](/images/4/cfafter.png)

Dùng `curl` gọi đến url để kiểm tra (lưu ý: kiểm tra cả 2 url của stack dev và prod)
![4](/images/4/url-test.png)
