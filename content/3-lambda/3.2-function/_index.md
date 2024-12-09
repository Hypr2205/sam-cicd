---
title : "Create Lambda function"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---

## Tạo function

- Access Lambda console
![lambda console](/images/3-lambda/lambda-console.png)

- Create function: **CheckResourceTags** with Python runtime
![details](/images/3-lambda/lambda-details.png)

- In the _Change default execution role_ section:
  - **Use an existing role**
  - Choose the **LambdaEventBridge** role that was previously created
![change role](/images/3-lambda/lambda-change-role.png)

- Lambda function code to check EC2 instances missing the _Environment_ tag:

```py
import boto3
import os

ec2 = boto3.client('ec2')
sns = boto3.client('sns')

def lambda_handler(event, context):
    sns_topic_arn = os.environ['SNS_TOPIC_ARN']
    
    instances = ec2.describe_instances()
    
    missing_tag_instances = []
    
    for reservation in instances['Reservations']:
        for instance in reservation['Instances']:
            tags = instance.get('Tags', [])
            # Check if the 'Environment' tag is missing or empty
            if not any(tag['Key'] == 'Environment' and tag['Value'] for tag in tags):
                missing_tag_instances.append(instance['InstanceId'])
    
    # Send SNS notification
    if missing_tag_instances:
        message = f"These EC2 instances are missing the 'Environment' tag: {missing_tag_instances}"
        sns.publish(
            TopicArn=sns_topic_arn,
            Subject="EC2 Instances Missing 'Environment' Tag",
            Message=message
        )
    
    return {
        'statusCode': 200,
        'body': 'Notification sent for missing tag instances.'
    }
```

## Add environtment variable

- Access the _Configuration_ tab, Select **Environment** variables, then click **Edit**
![env](/images/3-lambda/env.png)

- Add a new environment variable
  - Key: SNS_TOPIC_ARN
  - Value: The ARN of the SNS topic you created earlier
![arn](/images/3-lambda/topic-arn.png)
