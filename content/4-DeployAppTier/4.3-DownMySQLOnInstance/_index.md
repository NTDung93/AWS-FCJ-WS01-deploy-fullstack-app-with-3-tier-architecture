---
title : "Download MySQL on EC2 instance"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

## Download MySQL on EC2 instance

1. Run the following commands to download MySQL on the instance:
   - **`sudo yum install -y https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm`**
   - **`sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022`**
   - **`sudo yum install -y mysql-community-client`**
![download mysql](/workshop01-AWS-FCJ-2024/images/4-3/01.png?width=50pc)

2. Connect to RDS database:
   - Run command **mysql -h <RDS-ENDPOINT> -u <USERNAME> -p** (**`mysql -h database-1.cbk6is6oozuw.ap-southeast-1.rds.amazonaws.com -u admin -p`**)
   - Then enter password **`12345678`**
![connect to rds](/workshop01-AWS-FCJ-2024/images/4-3/02.png?width=50pc)

3. Run **`create database librarydb;`** to create a new db
![create db](/workshop01-AWS-FCJ-2024/images/4-3/03.png?width=50pc)

4. Run **`show database;`** to show existing dbs
![show db](/workshop01-AWS-FCJ-2024/images/4-3/04.png?width=50pc)

5. Run **`use librarydb;`** to use the newly created db
![use db](/workshop01-AWS-FCJ-2024/images/4-3/05.png?width=50pc)

6. Run **`show tables;`** to show tables in the db, at this time the db has no tables
![show tables](/workshop01-AWS-FCJ-2024/images/4-3/06.png?width=50pc)

7. To create tables for the db, go to the **application.properties** file of the back-end and reconfigure the information as shown below
![application properties](/workshop01-AWS-FCJ-2024/images/4-3/07.png?width=50pc)

8. Then we will run the app. After the app runs successfully, run the **`show tables;`** command again to check
![show tables](/workshop01-AWS-FCJ-2024/images/4-3/08.png?width=50pc)

9. Run the command **insert into librarydb.book (author, category, copies, copies_available, description, img, title) values ('John', 'Programming', 10, 8, 'Tutorial about Java', '', 'Java Advanced');** to add a row of data to the book table
![insert data](/workshop01-AWS-FCJ-2024/images/4-3/09.png?width=50pc)

10. Run **`select * from librarydb.book;`** to show the rows of data in the book table
![show data](/workshop01-AWS-FCJ-2024/images/4-3/10.png?width=50pc)

{{% notice note %}}
The above steps are just to test that the db works well according to the queries we have written. But in this workshop, we will use the database first approach, meaning we will create the db first and then create entities and repositories in the app to map with the db.
{{% /notice %}}

11. Open MySQL, access the created connection and import the **`React-Springboot-Add-Tables-Script-1.sql`** file in the **`starter-files`** folder, then run the available scripts to create the db named **librarydb** and the tables in the db
![import sql](/workshop01-AWS-FCJ-2024/images/4-3/11.png?width=50pc)

