---
title : "Install CLI"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 1.2. </b> "
---

## Install AWSCLI

1. Linux:

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

2. Windows

```powershell
scoop bucket add main
scoop install main/aws
```

3. Type `aws --version` after installation process

![aws](/images/1/1.2/awscli.png)

4. Type `aws configure` and fill the required informations:

- Access Key ID & Secret Access Key: access key you saved previously
- Default region name: ap-southeast-1
- Default output format: json/yaml
![aws](/images/1/1.2/cli-configure.png)

5. Type `aws sts get-caller-identity` to get IAM user information after configure cli

## Install SAMCLI

1. Linux

- [Download installer](https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip)

```bash
unzip aws-sam-cli-linux-x86_64.zip -d sam-installation
sudo ./sam-installation/install
```

2. Windows

- [Download installer](https://github.com/aws/aws-sam-cli/releases/latest/download/AWS_SAM_CLI_64_PY3.msi)
- Locate the downloaded installer file on your system then double-click the file to run it. Follow the on-screen instructions provided by the installer to complete the setup process

3. Type `sam --version` after installation processs

![aws](/images/1/1.2/sam.png)
