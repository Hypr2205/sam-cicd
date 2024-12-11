---
title : "Deploy manually"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

## Build

- To build a SAM project, use the `sam build` command. This command processes the project’s manifest files (e.g., requirements.txt) and generates deployment artifacts. Artifacts are the outputs of the build process, which can be compressed files (e.g., .zip, .tar), container images, or binary files. These artifacts are then deployed to various environments such as development, staging, or production. For SAM projects, the artifacts are stored in an S3 bucket
- Steps to build a SAM project:
  1. Run the build command: In the project directory, run the following command: `sam build`. This command will search for relevant manifest files (like requirements.txt for Python projects or package.json for Node.js projects), install dependencies, and prepare the deployment artifacts
  2. After the build process completes, the artifacts will be stored in a folder called .aws-sam/build. This folder contains the necessary files that can be deployed to your AWS environment
![3](/images/3/build-out.png)
![3](/images/3/build-artifact.png)

## Deploy

- To deploy a SAM project, use the `sam deploy` command. This command will create a CloudFormation stack and deploy the project to AWS. It utilizes the `template.yml` file to define and deploy the resources
- Steps to deploy a SAM project:
  1. Run the deploy command: `sam deploy`
  2. For the first deployment, it is recommended to use the `--guided` flag. This will prompt you to configure deployment options, and the settings will be saved in a samconfig.toml file. You can then use this configuration for subsequent deployments
  3. After the first deployment, if there are no changes in the configuration, you can simply run the sam deploy command again without the --guided flag. The deployment settings will be automatically retrieved from the samconfig.toml file
![3](/images/3/deploy.png)
- Deployment process result:
![3](/images/3/deploy-out.png)

## Check AWS Console

1. Go to IAM role, there is a role that created for Lambda function
![3](/images/3/role.png)
2. View the deployed Lambda function in the Lambda Console. The Lambda function will be deployed with the specified runtime (e.g., Python) and packaged as a ZIP file
![3](/images/3/lambda.png)
3. Go to S3 console, an S3 bucket is automatically created to store the deployment artifacts and other files, such as the template.ym
![3](/images/3/s3.png)
![3](/images/3/artifact.png)
4. CloudFormation stack
![3](/images/3/cfs.png)
5. Api gateway
![3](/images/3/apigw.png)
6. Test the API by calling the endpoint using the `curl` command
![3](/images/3/test-endpoint.png)
