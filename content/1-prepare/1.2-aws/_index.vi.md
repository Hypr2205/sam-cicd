---
title : "Cài đặt CLI"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 1.2. </b> "
---

## Cài đặt AWSCLI

1. Cài đặt trên Linux:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

2. Cài đặt trên Windows

```powershell
scoop bucket add main
scoop install main/aws
```

3. Sau khi cài đặt gõ lệnh `aws --version` để kiểm tra

![aws](/images/1/1.2/awscli.png)

4. Tại terminal gõ lệnh `aws configure` và điền các thông tin:

- Access Key ID & Secret Access Key: thông tin access key đã lưu ở phần trước
- Default region name: ap-southeast-1
- Default output format: có thể là json hoặc yaml
![aws](/images/1/1.2/cli-configure.png)

5. Sau khi nhập xong gõ lệnh `aws sts get-caller-identity` để kiểm tra thông tin vừa nhập

## Cài đặt SAMCLI

1. Cài đặt trên Linux

- [Tải file cài đặt](https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip)

```bash
unzip aws-sam-cli-linux-x86_64.zip -d sam-installation
sudo ./sam-installation/install
```

2. Cài đặt trên Windows

- [Tải file cài đặt](https://github.com/aws/aws-sam-cli/releases/latest/download/AWS_SAM_CLI_64_PY3.msi)
- Chạy file cài đặt vừa tải và làm theo hướng dẫn xuất hiện

3. Sau khi cài đăt, gõ lệnh `sam --version` để kiểm tra

![aws](/images/1/1.2/sam.png)
