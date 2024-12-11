---
title : "Create SAM project"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

## Generate SAM project with CLI

- Open your then type `sam init`:
![sam](/images/2/sam-init.png)
- Open the source code of the project in your preferred code editor or IDE. Run the following command in the terminal inside the project directory:

```bash
pip install -r hello_world/requirements.txt
```

- Project architecture:
![sam](/images/2/sam-structure.png)

## Run project local

To run a Serverless Application Model (SAM) project locally, you need Docker installed on your local machine. There are two main ways to do this:

1. Method 1: Using sam local invoke with Event Files

```bash
sam local invoke --event events/event.json
```

- Result:
![sam](/images/2/invoke-event.png)
- Run `docker images`:
![sam](/images/2/docker-image.png)

2. Method 2: Using `sam local start-api` starts an HTTP server locally to simulate the behavior of an API Gateway

```bash
sam local start-api --port 8080

curl http://localhost:8080/hello
```

![sam](/images/2/local-htpp.png)
![sam](/images/2/curl.png)
