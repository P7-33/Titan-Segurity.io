---
title: 'Web Application Lab Setup on Windows'
date: 2019-10-08T17:50:00+01:00
draft: false
---

Hello friends! Today we are going to show you how you can set up a vulnerable web application server in a Windows system using Xampp. Here we will be configuring the most popular web applications (DVWA, bwapp, SQLI, Mutillidae). So, let’s do that.

### **Table of Content**

**Requirement**

*   Web application
*   Xampp Server Installation in Windows
*   DVWA
*   bWAPP
*   Sqli
*   Mutillidae

**Requirement-Xampp server (Windows-X64)**

### **Web Application**

A web application is a computer program that utilizes web browsers and web technology to perform tasks over the Internet. Web apps can be built for a wider use which can be used by anyone; from an enterprise to an entity for a variety of reasons. Frequently used Web applications can include webmail.

### **Xampp Server Installation**

XAMPP stand for Apache + MariaDB + PHP + Perl

XAMPP is a free and open-source cross-platform web server solution stack package developed by Apache Friends, consisting mainly of the Apache HTTP Server, MariaDB database, and interpreters for scripts written in the PHP and Perl programming languages. Since most actual web server deployments use the same components as XAMPP, it makes transitioning from a local test server to a live server possible. (read more from Wikipedia)

Download from **[here](https://www.apachefriends.org/download.html)**

Once the installation is done, we need to start the service of Mysql and Apache service in Xampp server.

![](https://i1.wp.com/1.bp.blogspot.com/-T1v_SZYTybU/XZy0Bit_YLI/AAAAAAAAg1M/c_dVrfNtNsMvvHjgkCf4UN6rq8eN8eVGwCLcBGAsYHQ/s1600/1.jpg?w=687&ssl=1)

### **DVWA**

DVWA is a web application that is damn sensitive to PHP / MySQL. The main objectives are to provide security professionals with assistance to test their skills and resources in a legal environment, enable web developers to better understand the processes of protecting web applications and assist teachers/students to teach/learn protection in the classroom.

Download from **[here](http://www.dvwa.co.uk/)**

Once the dvwa is installed completely then we will navigate to **C:/_Xampp/htdocs/dvwa/config.inc.php.dist_** to change the username and password for the database.

Open the configuration file to set the Username and Password.

![](https://i1.wp.com/1.bp.blogspot.com/-HpsxSKGlGoI/XZy0HvD5wGI/AAAAAAAAg2Q/Y4AKeTnFzxIu09UGPUaDL62lbkgtRMVjwCLcBGAsYHQ/s1600/3.jpg?w=687&ssl=1)

Here, you can notice that the default **username** is **root** and **password** is **password** which we will modify.

![](https://i1.wp.com/1.bp.blogspot.com/-0v0CsO152hs/XZy0H_vORrI/AAAAAAAAg2U/yig9F69On68dbjURJUrhfZsvF0hVkLyqACLcBGAsYHQ/s1600/4.jpg?w=687&ssl=1)

Now here you may notice that we have set the password **“blank”** for user “root”. Now save these settings and quit.

![](https://i1.wp.com/1.bp.blogspot.com/-zLA6eT8SMHc/XZy0Hzw5sdI/AAAAAAAAg2Y/TC-sKn5S9HQj8rXxHjsg87kYPtd2NLu-QCLcBGAsYHQ/s1600/5.jpg?w=687&ssl=1)

Rename the file as “config.inc.php” after making above changes and save it.

![](https://i0.wp.com/1.bp.blogspot.com/-TxNtKAY-Zfo/XZy0IRrDbfI/AAAAAAAAg2c/reBVwOnVkMAnONgT2sMQAsIpu9chHvKEACLcBGAsYHQ/s1600/6.jpg?w=687&ssl=1)

Now we need to open the DVWA application in our localhost to create the database.

```
http://localhost/dvwa/setup.php
```

Now click on **create** database and database is created.

![](https://i0.wp.com/1.bp.blogspot.com/-qKoLLI3_IHI/XZy0InoHbJI/AAAAAAAAg2g/La8iP38Yg2QzVvLjzwuiVdhYDeuEUZWdACLcBGAsYHQ/s1600/7.jpg?w=687&ssl=1)

Now click on login and you are done with the setup.

![](https://i1.wp.com/1.bp.blogspot.com/-JFQVhFI2GQU/XZy0I1jd3fI/AAAAAAAAg2k/WE0__9z0LSkiG6XDgo97Pl_huCVqQLxLwCLcBGAsYHQ/s1600/8.jpg?w=687&ssl=1)

For login, we will use the DVWA username which is **admin** and **password** which is DVWA password by default.

![](https://i0.wp.com/1.bp.blogspot.com/-2wM-8dnKCT0/XZy0JLHLQvI/AAAAAAAAg2o/5nGquloOqzwAMrca6Ghrbgpt75Q4aL5xgCLcBGAsYHQ/s320/9.jpg?w=687&ssl=1)

### **Bwapp**

Now let’s set up a new lab which is BWAPP.

BWAPP is a free, open-source and intentionally unreliable web application, or a web buggy program. It helps security enthusiasts, designers and students discover Web bugs and stop them from doing so. BWAPP plans for positive penetration tests and cyber ethics initiatives.

Download it from **[here](http://www.itsecgames.com/)**.

Now navigate to **“C:/_Xampp/htdoc/bwapp/admin”_** folder to change the default username and password for the database.

![](https://i2.wp.com/1.bp.blogspot.com/-pVFoTzjfDz8/XZy0BT3NfFI/AAAAAAAAg1E/vvnpTWTI9y8TvWcbc1gggFKkIxZoz1_XQCLcBGAsYHQ/s1600/10.jpg?w=687&ssl=1)

Now you can see that the default **username** is **root** and **password** is **bug** which we will modify.

![](https://i0.wp.com/1.bp.blogspot.com/-8LH4Siv7eBo/XZy0BhdYWAI/AAAAAAAAg1I/PXX9tsisAcQpDin4IO2vaU_-gpFYmj-6QCLcBGAsYHQ/s1600/11.jpg?w=687&ssl=1)

Now here the **username** is **root** and **password** we have **set blank**. Now save the settings and quit.

![](https://i2.wp.com/1.bp.blogspot.com/-2gPrtIE0a5Q/XZy0CLzfbJI/AAAAAAAAg1Q/M4aMwLxeCYIy-tUKzpC8v4uGXx2qL4hpwCLcBGAsYHQ/s1600/12.jpg?w=687&ssl=1)

Now let’s open “bwapp/install.php” in the localhost and click on “here” to complete the installation.

![](https://i2.wp.com/1.bp.blogspot.com/-mipdZsVxMaU/XZy0CqDjRlI/AAAAAAAAg1U/nMtCM9kKkvQtFj8BzupR8MYVzJxSEf_9wCLcBGAsYHQ/s1600/13.jpg?w=687&ssl=1)

Now the installation is complete.

![](https://i2.wp.com/1.bp.blogspot.com/-ZQSpyRjIx70/XZy0DJ3xZ_I/AAAAAAAAg1Y/fbToVCEGIW0viCbRyjqAGglnryCPo0YcACLcBGAsYHQ/s1600/14.jpg?w=687&ssl=1)

When you will login as bee:bug; you will get the portal to test your penetration testing skill

![](https://i1.wp.com/1.bp.blogspot.com/-ZdpNxb90OMQ/XZy0DJwu3bI/AAAAAAAAg1c/2mQ9OXgvBEsVQecId8wKCPw3bWkZmzA3QCLcBGAsYHQ/s1600/15.jpg?w=687&ssl=1)

Here you can click on **bugs** and all bugs will be displayed to you which are there in bwapp web application.

![](https://i1.wp.com/1.bp.blogspot.com/-VZWX3hAibqU/XZy0DVJDb9I/AAAAAAAAg1g/tXBV2imayvQxNt-dTF2nwrPofSehZUG-gCLcBGAsYHQ/s1600/16.jpg?w=687&ssl=1)

### **SQLI**

SQLi: A facility that provides a robust testing environment for those involved in SQL injection acquisition and enhancement. Let’s start. First, we will download the SQLI lab through GitHub.

Now we will navigate _to **C:/htdocs/sqlilabs/sqli-connections**_ to edit the setup-db.php.

![](https://i1.wp.com/1.bp.blogspot.com/-GeUxv6JQm98/XZy0EKnm1FI/AAAAAAAAg1o/7Qd2O16jhyoDAPnVilNBA6ej08tYAE2gQCLcBGAsYHQ/s1600/17.jpg?w=687&ssl=1)

Now here we will set the password “blank” and save the changes and then quit.

![](https://i1.wp.com/1.bp.blogspot.com/-6fC34GvM_sM/XZy0EJoIffI/AAAAAAAAg1k/FbzYLYlixzcaINJyKhlH0-8YIK7CYT53ACLcBGAsYHQ/s1600/18.jpg?w=687&ssl=1)

Now browse this web application from through this _URL: localhost/sqli_ and click on **Setup/reset** Databases for labs.

![](https://i0.wp.com/1.bp.blogspot.com/-RfxgHTf-9JE/XZy0EtDXIpI/AAAAAAAAg1s/6pEVTGjPY5ATfygJeNiZNuwERUt5z0vEQCLcBGAsYHQ/s1600/19.jpg?w=687&ssl=1)

Now the sqli lab is ready to use. Now a page will open up in your browser which is an indication that we can access different kinds of Sqli challenges

![](https://i0.wp.com/1.bp.blogspot.com/-Zd9-sWzYpRw/XZy0Er1sY8I/AAAAAAAAg1w/-EvnNpbP0nUvgBBWWo4BBZ_qyFFHeq0kgCLcBGAsYHQ/s1600/20.jpg?w=687&ssl=1)

Now you can see that we have opened lesson 1. So, we have successfully set Sqli labs for practice.

![](https://i1.wp.com/1.bp.blogspot.com/-nVNOj3Y8E3c/XZy0FAzjRUI/AAAAAAAAg10/6gWAo8sShcEkAeyXg_xULUZNi4NrdOb5ACLcBGAsYHQ/s1600/21.jpg?w=687&ssl=1)

### **Mutillidae**

OWASP Mutillidae is an open-source web application that is intentionally vulnerable and actively aims at web security. It’s a laboratory for those involved in SQL injection acquisition and development, which offers a full test environment. This internet hacking framework is simple to use and is designed for labs, safety lovers, schools, CTFs and vulnerability assessments.

First, we will navigate to “**C:/Xampp/htdocs/mutillidae/includes**” to edit the “**database-config.php**” as shown below.

![](https://i1.wp.com/1.bp.blogspot.com/-ZmmabRlBS8A/XZy0FbJ0SvI/AAAAAAAAg14/jTMKVpJ0-DUwptBuHk3zgEl__ogZtG_wACLcBGAsYHQ/s1600/22.jpg?w=687&ssl=1)

Here we can see that password is set mutillidae which we will replace with **blank**.

![](https://i0.wp.com/1.bp.blogspot.com/-UoKvVTXpZqs/XZy0FhBBytI/AAAAAAAAg18/LBRktkqIyFgLRGHBGH8E1bA_3rx5rhjuwCLcBGAsYHQ/s1600/23.jpg?w=687&ssl=1)

You can view that we have set the password **“blank”.** Now save the settings and quit.

![](https://i0.wp.com/1.bp.blogspot.com/-YmlU1YdfiMc/XZy0F-k2WTI/AAAAAAAAg2A/X2Ix6euA9DkyBdaTL5QDzjK-Gemz2jkIACLcBGAsYHQ/s1600/24.jpg?w=687&ssl=1)

Now you can see the page where you need to click on **opt out** tap.

![](https://i0.wp.com/1.bp.blogspot.com/-bCSxfBTuB_4/XZy0G6pIlDI/AAAAAAAAg2I/PgqEfkgq1A8ZQKdHNalsH32T9k820xz8QCLcBGAsYHQ/s1600/25.jpg?w=687&ssl=1)

Now we will open this our local browser by the following _URL: localhost/mutillidae_ where we will find an option of reset database. Just click on it to **reset the database**. So, In this way, we can setup our vulnerable web application lab for penetration testing.

![](https://i1.wp.com/1.bp.blogspot.com/-bIeMv7CXFko/XZy0GinHgVI/AAAAAAAAg2E/e2thXTmyZRkXv0PkmAT48Qrabc_j320iACLcBGAsYHQ/s1600/26.jpg?w=687&ssl=1)

Now you will be redirected to a page which will ask you to click ok to proceed. Here you need to click on **OK** and you are done with the configuration of the Mutillidae lab.

![](https://i0.wp.com/1.bp.blogspot.com/-0Ff5oyCsaEI/XZy0HH_K__I/AAAAAAAAg2M/o94hfA2kyYck4RL-2FvT4EVxrjdAucpdACLcBGAsYHQ/s1600/27.jpg?w=687&ssl=1)

We have successfully set all the web applications in Xampp server in Windows.

**Author**: Geet Madan is a Certified Ethical Hacker, Researcher and Technical Writer at Hacking Articles on Information Security**. **Contact [**here**](https://www.linkedin.com/in/geet-madan-86568b170/)

The post [Web Application Lab Setup on Windows](https://www.hackingarticles.in/web-application-lab-setup-on-windows/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2OvAqUl