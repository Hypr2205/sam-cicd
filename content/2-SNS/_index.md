---
title : "Create topic for SNS"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

## Create SNS topic

- Access SNS Console
![sns console](/images/2-sns/sns-console.png)

- Navigate to **Topics** -> **Create topic**
![sns console](/images/2-sns/create-topic.png)

- Create new topic: **ResourceTagMissingNotification**
![sns console](/images/2-sns/topic-details.png)

## Create an Email Subscription for the Topic

- Navigate to the _Subscriptions_ section in the newly created topic, go to **Subscriptions** -> **Create subscription**
![subscription](/images/2-sns/create-subscription.png)

- Configure subscription details:
  - **Topic ARN**: Select the ARN of the newly created topic
  - **Protocol**: Email
  - **Endpoint**: Enter the email address where you want to receive notifications
![subscription details](/images/2-sns/subscription-details.png)

- Confirm the Subscription: After creating the subscription, check your registered email inbox for a confirmation email & click the confirmation link to activate the subscription
![confirmation email](/images/2-sns/confirmation-email.png)
![confirmed](/images/2-sns/confirmed.png)
![confirmed status](/images/2-sns/confirmed-status.png)
