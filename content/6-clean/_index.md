---
title : "Clean resources"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

- Terminate 2 EC2 instances:
  - In EC2 console, select 2 test instances
  - **Instance state** -> **Terminate instance**
![tẻminate](/images/6-clean/terminate-instance.png)

- Delete CloudWatch log group:
  - Access CloudWatch console, navigate to **Logs** -> **Log groups**
  - Select log group with name **/aws/lambda/CheckResourceTags**
  - **Action** -> **Delete log group**
![lg](/images/6-clean/delete-loggroup.png)

- Go to EventBridge console
  - Navigate to **Scheduler** -> **Schedules**
  - Select **CheckResourceTagsRule**
  - Choose **Delete**
![clean rule](/images/6-clean/clean-rule.png)

- Access SNS console
  - Navigate to **Topics**, select topic **ResourceTagMissingNotification**
  - **Delete**
![topic](/images/6-clean/delete-topic.png)

- Access Lambda console, go to **Functions** section
  - Select function **CheckResourceTags**
  - Select **Actions** -> **Delete**
![lambda](/images/6-clean/delete-lambda.png)
