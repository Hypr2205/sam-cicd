---
title : "Create EventBridge event"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

- Access CloudWatch console
![console](/images/4-cw/console.png)

- Navigate to **Events**, select **Rules** -> **Create rule**

- In _Rule detail_ section:
  - **Name**: CheckResourceTagsRule
  - **Event bus**: default
  - **Rule type**: Scheduled
![rule details](/images/4-cw/rule-details.png)

- In _Schedule pattern_ section:
  - **Occurrence**: Recurring schedule
  - **Time zone**: UTC+7 Asia/SaiGon
  - **Schedule type**: Cron-based
  - **Cron expression**: `cron(0/5 * * * ? *)`
  - **Flexible time window**: 5 minutes
![pattern](/images/4-cw/schedule-pattern.png)

- In _Select target_ section, select _AWS Lambda_
![target](/images/4-cw/target.png)

- In _Invoke_ section, select Lambda function that you created earlier
![invoke](/images/4-cw/invoke.png)

- _Settings_:
![settings](/images/4-cw/settings.png)
