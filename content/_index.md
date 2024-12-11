---
title : "Serverless CI/CD Workshop"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

## Overall

- In this workshop, we will explore how to use the Serverless Application Model (SAM) to develop serverless APIs and create a CI/CD pipeline to automate the deployment process
- AWS SAM (Serverless Application Model) is an open-source framework designed to simplify the development and deployment of serverless applications on AWS. It provides a clean and concise syntax to define the components of a serverless application, such as Lambda functions, API Gateway, databases...
- Why Use AWS SAM?
  1. Simplified Development Process: SAM allows developers to focus on the business logic of their applications without worrying about the detailed configuration of AWS resources
  2. Faster Development and Deployment: with its clear syntax and powerful supporting tools, SAM accelerates the process of building and deploying applications
  3. Tight Integration with AWS Services: SAM is purpose-built for AWS, enabling seamless interaction with services like Lambda, API Gateway, DynamoDB, and others
  4. Easy Application Management: Manage the entire serverless application through a single configuration file
  5. Scalability: Built on AWS CloudFormation, SAM can leverage all of CloudFormation's features for managing AWS resources
- What You'll Learn: By the end of the workshop, you’ll understand how to:
  - Develop serverless APIs with AWS SAM
  - Automate the deployment process using a CI/CD pipeline

## Contents

1. [Pre-requisite](1-prepare/)
2. [Create SAM project](2-create-sam/)
3. [Deploy manually](3-deploy/)
4. [Build CI/CD pipeline](4-cicd/)
5. [Cleanup](5-final/)
