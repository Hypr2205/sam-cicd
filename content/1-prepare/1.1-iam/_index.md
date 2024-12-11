---
title : "Create IAM user"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.1. </b> "
---

## Create new user

- Go to IAM console
- Select **Users** -> **Create user**
![iam](/images/1/1.1/iam-console.png)
- _Specify user details_ section:
  - Username: choose an username
  - Check **Provide user access to the AWS Management Console** and select **I want to create an IAM user**
  - Select **Custom password** and set the desired password
  - Uncheck **Users must create a new password at next sign-in**
![iam](/images/1/1.1/user-details.png)
- _Set permissions_ section:
  - Select **Attach policies directly**
  - Find **AdministratorAccess**
![iam](/images/1/1.1/user-policies.png)

## Create an access key

- After completing the user creation process, return to the Users list and select the newly created user, then go to the _Security credentials_ tab, Scroll down to the _Access key_ section, select **Create access key**
![iam](/images/1/1.1/credentials.png)
![iam](/images/1/1.1/key.png)
- In create access key section:
  - Select CLI usecase
  - Check **Confirmation**
  - Select **Next** -> **Create access key**
![iam](/images/1/1.1/usecase.png)
- In the _Retrieve access key section_, copy the Access Key ID and Secret Access Key, save them securely, either by manually storing the keys in a safe location or download the provided CSV file for future reference
![iam](/images/1/1.1/get-key.png)
