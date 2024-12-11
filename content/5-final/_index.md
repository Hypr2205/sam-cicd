---
title : "Cleanup"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

## Summary

Through the steps outlined, we have learned about the Serverless Application Model (SAM), how to create a serverless application using SAM CLI, and how to build and deploy a SAM project. We also built a fully automated CI/CD pipeline using the SAM pipeline template to facilitate project deployment

## Cleanup

To clean up the resources created during the workshop and avoid unnecessary charges, you can delete the CloudFormation stacks, S3 buckets, and Lambda functions associated with your SAM project:

Go to CoudFormation console, Locate and delete all the stacks related to your SAM project
![5](/images/5/deletecf.png)
Go to the S3 console, delete the S3 buckets created for storing SAM artifacts
![5](/images/5/deletes3.png)
Delete any lambda functions created during the SAM project deployment
![5](/images/5/deletelambda.png)
