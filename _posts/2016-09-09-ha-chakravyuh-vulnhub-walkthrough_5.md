---
title: 'HA: Chakravyuh Vulnhub Walkthrough'
date: 2019-11-05T18:40:00+01:00
draft: false
---

Today we are going to solve our Boot to Root challenge called “HA Chakravyuh”. We have developed this lab for the purpose of online penetration practices. It is based on the Mahabharat Saga’s renowned Battle Formation by the same name. Let’s Solve it!!

**Download [Here](https://www.vulnhub.com/entry/ha-chakravyuh,388/)**

**Level: Intermediate**

**Task:** To Enumerate the Target Machine and Get the Root Access.

### **Penetration Methodologies**

*   **Network Scanning**
    *   Netdiscover
    *   Nmap Scan
*   **Enumeration**
    *   Browsing HTTP Service
    *   Anonymous FTP Login
    *   Password Bruteforce using John The Ripper
    *   Getting Login Credentials
    *   Searching Exploit using Searchsploit
*   **Exploitation**
    *   Exploiting LFI Vulnerability
    *   Getting a reverse connection
    *   Spawning a TTY Shell
*   **Privilege Escalation**
    *   Docker

### **Walkthrough**

### **Network Scanning**

After downloading, run the Machine in VMWare Workstation. To work on the machine, we will be needing its IP Address. For this, we will be using the netdiscover command. After matching the MAC and IP Address we found the Virtual Machine IP Address to be 192.168.1.105.

```
netdiscover
```

![](https://i2.wp.com/1.bp.blogspot.com/-1YHfQh6T2oM/XcGvi-7FyWI/AAAAAAAAhPQ/Z8o8C3SrewE1NW89mnODEWOGhRSZjQMuACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now that we have the Target Machine IP Address, our next logical step would be to do a port scan on the target to get information about the various services that are running on the target machine. After the Aggressive Scan of all the ports, we see that we have the SSH service (22), HTTP service (80), FTP service (65530) running on the Target Machine. We did a scan for all the ports because sometimes Administrators set up a service on a different port altogether so that they are not visible in a normal scan.

```
nmap -p- -A 192.168.1.105
```

![](https://i0.wp.com/1.bp.blogspot.com/-3O-AKWtOLB8/XcGvlywtPpI/AAAAAAAAhPw/Lyb7DQ9Kq1wl-5eIoCFeX8SmvTXosjHaQCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

Moving on, we observed that we have the HTTP service running. It is probable that a web page is hosted. So, we decided to take a look through our Web Browser. It contained a webpage with a painting depicting Arjuna battling to break the Chakravyuh. We did a thorough browsing of the webpage. We went through its source code and images, but there was no way in or any hint.

```
http://192.168.1.105
```

![](https://i0.wp.com/1.bp.blogspot.com/-Fc2E_3igbRw/XcGvnX2KriI/AAAAAAAAhP8/1NEpkMqZrWUOV_H4sUX4RI96QbZlezJOQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

We then diverted our attention to the service that was shifted to port 65530. During our Nmap aggressive scan, we saw that Nmap was able to tell us that the Anonymous login is enabled on this server. We decided to take a look at the shared files. So, after logging in the FTP service we looked around to find a directory named pub. Inside it was a Compressed 7z file named arjun. To take a closer look we downloaded the file with the help of get command.

```
ftp 192.168.1.105 65530  
Anonymous  
ls  
cd pub  
ls  
get arjun.7z  
bye
```

![](https://i2.wp.com/1.bp.blogspot.com/-eaQhrjrG1bQ/XcGvmkePCfI/AAAAAAAAhP0/ksaa5EQJSu4mDkOkyh3gcXMpJQ1wLGzaQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

After successfully downloading we tried to open the Compressed file using the Archive Manager as shown in the image below. It gave us a prompt for a password. We currently didn’t have any passwords. So now we have to try and enumerate the password for this file.

![](https://i1.wp.com/1.bp.blogspot.com/-9ia3f5eil_k/XcGvm-_Z9CI/AAAAAAAAhP4/9HXLm9Q5go4yELWf5KldJ3g0OUr0jZDqACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

We didn’t have any choice other than brute force the password. In order to brute force with John The Ripper. We required a python script that could give us the hashed from the compressed file. These scripts usually have the name as “xyz2john”, where xyz would be the file extension that we need hashes from. We googled 7z2john, we found the script and saved on our system as 7z2ctf.py. It is pretty easy to find this script. But still, if you don’t get it, you can download by clicking [here](https://github.com/truongkma/ctf-tools/blob/master/John/run/7z2john.py).  Now that we have the python script, we extracted the hashes from the file and ran John The Ripper to crack the password hash. Upon cracking we see that we have the password as “family”.

```
python 7z2ctf.py arjun.7z > hash  
john --wordlist=/usr/share/wordlists/rockyou.txt hash  
john hash --show  
arjun.7z:family
```

![](https://i2.wp.com/1.bp.blogspot.com/-n3koZx93kow/XcGvnkr9yrI/AAAAAAAAhQA/TI81cCf9WIA0wbOQ0w8X6GB5UFwbrbQsgCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

We opened the Compressed file to find a text file named secret inside it. On opening the secret.txt we find an encoded text inside it. On a first look, it seemed like Base64 encoded text. 

```
Z2lsYTphZG1pbkBnbWFpbC5jb206cHJpbmNlc2E=
```

![](https://i0.wp.com/1.bp.blogspot.com/-z2YPk235uqM/XcGvn85EQyI/AAAAAAAAhQE/xuT1xxgzQqAjTWrIwk0xexCmZmpwCR7GwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

We decoded the text found in the secret.txt using the echo and base64 command. The encryption was indeed base64. Upon decryption, we see that the text hints that we have Gila CMS to deal with in this scenario. Also, we got what seems to be login id and password.

```
echo "Z2lsYTphZG1pbkBnbWFpbC5jb206cHJpbmNlc2E=" | base64 -d  
gila:admin@gmail.com:princesa
```

![](https://i0.wp.com/1.bp.blogspot.com/-vPmJIk_4M4M/XcGvoV390_I/AAAAAAAAhQI/QsllCJ0LWN8jj4v_E0BSOQQGyyCXZJdiACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Since we got the hint that we have the Gila CMS. We tried to visit the link to access the page hosted with the help of Gila CMS. And we have a webpage as shown in the image below.

```
http://192.168.1.105/gila/
```

![](https://i0.wp.com/1.bp.blogspot.com/-VIP3Lp69IxQ/XcGvo3u39EI/AAAAAAAAhQM/XZHhqKPfU1wAWlhb87bM1zLeZagsnNbtACLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

We also tried the admin keyword to access the login panel. This came out to be the actual login panel. So, we entered the credentials we found earlier.

```
http://192.168.1.105/gila/admin  
admin@gmail.com  
princesa
```

![](https://i0.wp.com/1.bp.blogspot.com/-WA19THEC1ss/XcGvjG9qhkI/AAAAAAAAhPY/u2Pk_DQ-9Ss_ASk5DF0FV8BBuptJXGt4wCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

They worked like charm. We got inside the Gila CMS admin panel. We took a look around to see if we have any hints or any way to exploit it.

![](https://i2.wp.com/1.bp.blogspot.com/-HMTnytzC-aQ/XcGvjEhSrhI/AAAAAAAAhPU/JLn_HMcYKBcgXFmRQjEdB7YiTq1MUtuyACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

After looking for a while we couldn’t find any way in through the CMS. So, we went onto the basics. We searched for Gila CMS in searchsploit. We saw that we have a Local File Inclusion Vulnerability that could be useful. We downloaded the exploit to our Attacker machine. After completion of the Download.

```
searchsploit gila cms  
Gila CMS < 1.11.1 - Local File Inclusion  
searchsploit -m 47407  
cat 47407.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-oEb4-nHjhf8/XcGvkFZIpTI/AAAAAAAAhPc/jNDrZpKOec4J0_Kd2d_YqwyBa6DVxsmowCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

### **Exploitation**

In the exploit we see that we have the link but as mentioned by the author of the exploit that the PoC mentioned works on Xampp Server and we have a Linux machine as the target machine. So, we changed the link to point at the /etc/passwd. Also, it has the website set at the gilacms section and we found that we have it at /gila/. So, we changed that bit too.

```
http://192.168.1.105/gila/admin/fm/?f=src../../../../../../../../../etc/passwd
```

![](https://i0.wp.com/1.bp.blogspot.com/-3QwBjJ9P4-w/XcGvkYnOiPI/AAAAAAAAhPg/otc7LoLc5aklq2o0nPVJ1n29praOGQ16wCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

We see that we have the list of all the files hosted via the Gila CMS. We see that we have the index.php file. It seemed like our way in. So, we opened the file. It contained the PHP code for the display of the index page. We used our PHP reverse shellcode by pentestmonkey. It can be found **[here](http://pentestmonkey.net/tools/web-shells/php-reverse-shell)**. We changed the IP Address in the shell to the IP Address of our Attacker Machine. We started a netcat listener on our attacker machine on the port that we mentioned in our reverse shell. After making the necessary changes, we saved the changes in index.php. And we opened the file in the Web Browser.

![](https://i0.wp.com/1.bp.blogspot.com/-Stn3SBsgCB8/XcGvkg_5T-I/AAAAAAAAhPo/iM50CktuEIsm5XvebcivKYbKSpI9c9aCgCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

As we opened the file, the PHP reverse shell got executed and we got the shell on the target machine. It was an improper shell. So, we used the python one-liner to convert it into a proper shell. After getting the shell as per our satisfaction we ran the id command to see the users and groups on the target machine. We got to know that we have a docker user group. This could help us in Privilege Escalation.

```
nc -lvp 1234  
python -c 'import pty;pty.spawn("/bin/bash")'  
id
```

![](https://i1.wp.com/1.bp.blogspot.com/-TNFQJtGcWvI/XcGvk0-CehI/AAAAAAAAhPk/TTZCgU02IrgJmMisMHVmRBIbm2IwWdAgwCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

### **Privilege Escalation**

Since we have access to the user which is a part of the docker group. While working we docker we know that there is an issue with the docker that all the commands in docker require sudo as docker needs root to run. The Docker daemon works in such a way that it is allowed access to the root user or any other user in the particular docker group. This shows that access to the docker group is the same as to give a perpetual, root access without any password. We ran the command shown below. This command obtains the alpine image from the Docker Hub Registry and runs it. The –v parameter specifies that we want to create a volume in the Docker instance. The –it parameters put the Docker into the shell mode rather than starting a daemon process. The instance is set up to mount the root filesystem of the target machine to the instance volume, so when the instance starts it immediately loads a chroot into that volume. This gives us the root of the machine. After running the command, we traverse into the /mnt directory and found out flag.txt. This concludes this lab.

```
docker run -v /root:/mnt -it alpine  
cd /mnt  
ls  
cat final.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-MzR5SxlaQ90/XcGvlfABrDI/AAAAAAAAhPs/zvu73k7DdzsDY1meNJjSb2CIBZopSGaSQCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

**Author: Pavandeep Singh** is a Technical Writer, Researcher and Penetration Tester Contact **[here](https://www.linkedin.com/in/pavandeep-singh-6b1074132)**

The post [HA: Chakravyuh Vulnhub Walkthrough](https://www.hackingarticles.in/ha-chakravyuh-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/36Dfvp2