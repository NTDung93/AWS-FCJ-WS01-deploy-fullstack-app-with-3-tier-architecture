---
title : "Flow explaination"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1.1 </b> "
---
## Flow explaination of three-tier architecture

In the diagram below, we will see the architectural model of a fullstack application implementing **three-tier architecture**. First, the user operation will go through the **Internet gateway** and then to the **External (Internet facing) Application Load Balancer**. Load Balancer will forward traffic to **servers in the Web tier**. Then the servers in the Web tier will call APIs to the **Interal Load Balancer**. Load Balancer will then forward traffic to **servers in the App tier**. Finally, the servers in the App tier will process the request, retrieve data in the **Data tier** (if necessary) and return results to users in the Web tier. This is the basic three-layer architectural model that we will implement in this workshop.

![Architecture diagram](/workshop01-AWS-FCJ-2024/images/1-Introduce/workshop01-white.png?width=60pc)