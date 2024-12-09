---
title : "Tạo Lambda function"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---

## Tạo function

- Truy cập Lambda console
![lambda console](/images/3-lambda/lambda-console.png)

- Tạo Lambda với tên **CheckResourceTags** sử dụng Python
![details](/images/3-lambda/lambda-details.png)

- Trong phần _Change default execution role_:
  - Chọn **Use an existing role**
  - Chọn role **LambdaEventBridge** đã tạo
![change role](/images/3-lambda/lambda-change-role.png)

- Code function kiểm tra các EC2 instance thiếu tag _Environment_:

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

## Tạo biến môi trường

- Trong Lambda vừa tạo, chuyển sang tab _Configuration_, chọn **Environment variables**, chọn **Edit**
![env](/images/3-lambda/env.png)

- Thêm biến môi trường **SNS_TOPIC_ARN** là ARN của topic đã tạo
![arn](/images/3-lambda/topic-arn.png)
