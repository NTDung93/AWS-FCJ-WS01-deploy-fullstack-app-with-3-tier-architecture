---
title : "Deploy Web Tier"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---
#### Introduction
In this section, we will deploy the Web Tier by uploading the source code of the application to **Amazon S3** and deploying the application on **Amazon EC2**. In addition, we will use **Nginx** in this workshop. Nginx will act as a **web server** that we will configure to run the application on **port 80**, as well as help **redirect API** requests from the Web Tier to the App Tier through the **Internal Load Balancer**.

#### Contents:
1. [Update Nginx Configuration File](6.1-UpdateConfigFile/)
2. [Upload Application Source Code to Amazon S3](6.2-UploadCodeToS3/)
3. [Create EC2 Instance](6.3-CreateEc2Instance/)
4. [Connect to EC2 Instance](6.4-ConnectToInstance/)