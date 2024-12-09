---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

This is a simple workshop on managing resources on AWS by setting up tags for created resources. The overall model is as follows:

1. EventBridge (CloudWatch Events): Periodically triggers to check resources (EC2, S3, etc.).
2. Lambda: Activated by CloudWatch Events when a resource is detected to be missing required tags.
3. SNS Topic: Sends notification emails.

![resoure-management](/images/resource-management.png)
