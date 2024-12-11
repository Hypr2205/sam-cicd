---
title : "Tạo project SAM"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

## Tạo project bằng CLI

- Mở terminal, gõ lệnh `sam init` và các lựa chọn như sau:
![sam](/images/2/sam-init.png)
- Sau khi tạo project, mở source code và chạy câu lệnh sau:

```bash
pip install -r hello_world/requirements.txt
```

- Project *hello_world* được tạo ra có kiến trúc như sau:
![sam](/images/2/sam-structure.png)

## Chạy project local

Có hai cách để chạy một project SAM ở local, yêu cầu máy local phải có Docker

1. Cách 1: Gọi event qua các file `.json` trong folder `events`

```bash
sam local invoke --event events/event.json
```

- Kết quả sau khi chạy
![sam](/images/2/invoke-event.png)
- Lúc này chạy câu lệnh `docker images` sẽ thấy một image được pull về máy
![sam](/images/2/docker-image.png)

2. Cách 2: Chạy một http server hoạt động giống API gateway

```bash
sam local start-api --port 8080

curl http://localhost:8080/hello
```

![sam](/images/2/local-htpp.png)
![sam](/images/2/curl.png)
