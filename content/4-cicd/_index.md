---
title : "CI/CD with Github Actions"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

In the previous section, we manually built and deployed the SAM project using commands like `sam build`, `sam deploy`, or `sam deploy --guided`. The drawback of this manual approach is that every time there is a code change, we have to rerun these commands, which is time-consuming and prone to human error. To overcome these limitations, we can use GitHub Actions to automate the deployment process, reducing the chances of errors and eliminating repetitive tasks

## Create an Github repository

- Log in to your GitHub account and create new repository with following name: **aws-sam-workshop**
![4](/images/4/create-repo.png)
- In the top-right corner, click on your user avatar and select **Settings** -> **Developer settings** -> **Personal access token** -> **Token (classic)** -> **Generate new token**
![4](/images/4/token.png)
- In the token creation screen, provide a name for the token and select the necessary scopes: repo and workflows.After the token is created, copy and store the token in a secure location
![4](/images/4/scope.png)
- Push project to Github

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

To automate the deployment process, we will create a pipeline using the SAM Pipeline template, which will have two stages: dev and production

### 1. Create the Dev stage for the lpipeline

Navigate to the project directory, run the following command:

```bash
sam pipeline bootstrap --stage dev
```

After running the command, you should see output similar to this:

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

After running the command, you can verify that the dev stage has been successfully set up by checking AWS CloudFormation
![4](/images/4/cfdev.png)

### 2. Create the Production stage for the pipeline

```bash
sam pipeline bootstrap --stage prod
```

Similar to the dev stage, we can create the production stage for the pipeline using a similar command.After running the command, you will see output similar to the dev stage setup. The resources required for the production stage will be created, and the stack will be updated in CloudFormation

### 3. Tạo Github actions

Now, let's automate the deployment process with GitHub Actions. We will initialize the pipeline configuration using the sam pipeline init command, which will generate the necessary GitHub Actions workflow

```bash
sam pipeline init
```

![4](/images/4/pipeline.png)

After running this command, you will see a process that prepares the pipeline configuration, including setting up the GitHub Actions workflow. The command will create a new file: `.github/workflows/pipeline.yaml`

## Deploy and test CI/CD pipeline

Now that you've set up the pipeline and configured the GitHub Actions workflow, let's deploy the pipeline. Stage and commit the changes you made then push the changes to GitHub repository:

```bash
g add .
g commit -m "config: generate action workflow with SAM pipeline"
git push -u origin main
```

Visit workshop GitHub repository, navigate to the **Actions** tab to view the pipeline's progress
![4](/images/4/pipeline-status.png)

After the pipeline completes successfully, you can verify the deployed resources in CloudFormation console
![4](/images/4/cfafter.png)

Use `curl` to send requests to both the dev and production API endpoints to verify the deployment is successful
![4](/images/4/url-test.png)
