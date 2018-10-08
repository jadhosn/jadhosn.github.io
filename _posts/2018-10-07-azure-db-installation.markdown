---
title:  "Azure SQL database - A quick tutorial"
date:   2018-10-06 18:46:35
categories:  
tags: [Azure, SQL, Tutorial]
outside_link: "N"
link:
---
A Step-by-step Azure SQL database Installation: 

A. Setting up Azure SQL database: 

Azure offers a [free trial subscription](https://azure.microsoft.com/en-us/free/) for the first month (if you didn't 
use it already). This type of subscription does require valid payment details, __BUT__ if you're a student, you can 
activate your account using [the student trial version](https://medium.com/r/?url=https%3A%2F%2Fazure.microsoft.com%2Fen-us%2Ffree%2Fstudents%2F)
 (no payment details needed, just sign in with your school's credentials).  

B. Create an Azure SQL database: 
1. Browse to [https://portal.azure.com](https://portal.azure.com), sign-in with your free trial account
2. In the left pane, click **+ New Resource**, then **SQL database**  
![Image2](../../images/posts/1/db1.png)  

Let's create our server and the database:    
- Database name: **sql-test**
- Resource group: Create a new group, name it **medium**
- Server: Configure a new server, name it something unique (call it something like **sql-test-medium-001**). 
- Server Admin login: any username (that's easy to remember!) 
- Pricing tier: Basic  
![Image 2](../../images/posts/1/db2.png)  
After a short time (Yes, it takes a solid minute or so), you can see your new **server** and **database** in 
**All Resources**  
![Image 3](../../images/posts/1/db3.png)  
Let's check whether we created our database properly:  
* Click on your **database**: sql-test  
![Image 4](../../images/posts/1/db4.png)  
* Click on Query Editor (preview)  
![Image 5](../../images/posts/1/db5.png)  
* Azure will prompt to login (using the username that you used when you created the server above)  
![Image 6](../../images/posts/1/db6.png)   
* Type in a small SQL command to test the database: Type in the query window on the right this SQL command
 _SELECT * FROM SalesLT.Customer;_ and then hit **run**. You should see an output similar to the one below  
![Image 8](../../images/posts/1/db8.png)  


C. Configure Azure firewall for external database client tools (SSMS, Azure data studio ...)  
* Go back to all resources, and click on your **server** sql-test-medium  
![Image 9](../../images/posts/1/db9.png)  
* Go to Firewal and virtual network  
![Image 10](../../images/posts/1/db10.png)  
* Click on Add Client IP  
![Image 11](../../images/posts/1/db11.png)  
* Don't forget to SAVE!  
![Image 12](../../images/posts/1/db12.png)   

This should take care of setting up your azure testing database!  

