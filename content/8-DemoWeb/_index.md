---
title : "Demo deploy successfully"
date :  "`r Sys.Date()`" 
weight : 8
chapter : false
pre : " <b> 8. </b> "
---
#### Demo deploy successfully

1. Access the website using the **DNS name** of **web-tier-external-lb**
![](/workshop01-AWS-FCJ-2024/images/8/01.png?width=60pc)

#### Demo home interface and book load api using pagination
2. To test the successful api call, before accessing the web, we will inspect on the browser and open the **Network** tab and tick on **Fetch/XHR** to see the request sent and the response received from the server.
    - select the **Headers** tab to view the request sent
![](/workshop01-AWS-FCJ-2024/images/8/02.png?width=60pc)
    
    - Select the **Response** tab to view the response from the server
![](/workshop01-AWS-FCJ-2024/images/8/03.png?width=60pc)

#### Demo book search interface and book search api
3. Access the book search interface by clicking on **Search Books** on the header
![](/workshop01-AWS-FCJ-2024/images/8/04.png?width=60pc)

4. Then enter the name of the book you want to search in the search box and click the **Search** button (you can also filter by book category)
![](/workshop01-AWS-FCJ-2024/images/8/05.png?width=60pc)
![](/workshop01-AWS-FCJ-2024/images/8/06.png?width=60pc)

#### Demo page switching using pagination
5. In the **Search Books** interface, scroll down to the bottom and click on the **page number** to switch pages (or use the **First Page** and **Last Page** buttons)
![](/workshop01-AWS-FCJ-2024/images/8/07.png?width=60pc)

{{% notice note %}}
Because the EC2 instance we are using is not powerful enough, when uploading the front-end S3 code, I have cut a lot of the front-end source code, leading to the app only working on some basic features. If you want the app to run completely, you can clone the source code from the **Main** branch and use a more powerful instance.
{{% /notice %}}