---
title : "Tạo EventBridge event"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

- Truy cập CloudWatch console
![console](/images/4-cw/console.png)

- Trong phần **Events**, chọn **Rules** -> **Create rule**

- Trong phần _Rule detail_:
  - **Name**: CheckResourceTagsRule
  - **Event bus**: default
  - **Rule type**: Scheduled
![rule details](/images/4-cw/rule-details.png)

- Trong phần _Schedule pattern_:
  - **Occurrence**: Recurring schedule
  - **Time zone**: UTC+7 Asia/SaiGon
  - **Schedule type**: Cron-based
  - **Cron expression**: `cron(0/5 * * * ? *)`
  - **Flexible time window**: 5 minutes
![pattern](/images/4-cw/schedule-pattern.png)

- Trong phần _Select target_, chọn _AWS Lambda_
![target](/images/4-cw/target.png)

- Dưới phần _Invoke_, chọn Lambda function đã tạo
![invoke](/images/4-cw/invoke.png)

- Trong mục _Settings_:
![settings](/images/4-cw/settings.png)
