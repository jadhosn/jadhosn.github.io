---
title:  "Azure SQL database - A quick tutorial"
date:   2018-10-06 18:46:35
categories:  
tags: [Azure, SQL, Tutorial]
outside_link: "N"
link:
---
#Step-by-step Azure SQL database Installation: 

Setting up Azure SQL database: 

Azure offers a free trial subscription for the first month (if you didn't use it already). This type of subscription does require valid payment details, BUT if you're a student, you can activate your account using the student trial version (no payment details needed, just sign in with your school's credentials).
A. Create an Azure SQL database: 
Browse to https://portal.azure.com, sign-in with your free trial account.
In the left pane, click + New Resource, then SQL database 

Let's create our server and the database:  
![Image 1](../../images/posts/1/db2.png)
- Database name: sql-test
- Resource group: Create a new group, name it medium
- Server: Configure a new server, name it something unique (I named mine sql-test-medium). 
- Server Admin login: any username (that's easy to remember!) 
- Pricing tier: Basic