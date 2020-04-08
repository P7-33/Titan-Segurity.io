---
title: 'Privilege Escalation Cheatsheet (Vulnhub)'
date: 2019-10-22T19:17:00+01:00
draft: false
---

This cheatsheet is aimed at the CTF Players and Beginners to help them understand the fundamentals of Privilege Escalation with examples. It is not a cheatsheet for Enumeration using Linux Commands. Privilege escalation is all about proper enumeration. There are multiple ways to perform the same tasks. We have performed and compiled this list on our experience.  
**NOTE:** This is a brief version of this Cheatsheet. For the complete privilege escalation Cheatsheet visit our [GitHub page](https://github.com/Ignitetechnologies/Privilege-Escalation).  

### **Table of Content**

1.  Abusing Sudo Rights
2.  SUID Bit
3.  Kernel Exploit
4.  Path Variable
5.  Enumeration
6.  MySQL
7.  Crontab
8.  Wildcard Injection
9.  Capabilities  
    
10.  Writable etc/passwd file
11.  Writable files or script as root
12.  Buffer Overflow
13.  Docker

### **Abusing Sudo Rights**

The word sudo stands for Super User and Do. Basically, the keyword ‘sudo’, when used as a prefix to a command will allow you to run the said command as root without changing your user. When you run any command along with sudo, it will ask for root privileges in order to execute the command and here, Linux will confirm if that particular username is in the sudoers file. If the information matches to the sudoers file then that command will run and if not then you cannot run the command or program using the sudo command. As per sudo rights the root user can execute from ALL terminals, acting as ALL users: ALL group, and run ALL command. So, we can manipulate such rights and use them to our advantage as we have done it many CTF’s.  
Read from here: https://www.hackingarticles.in/linux-privilege-escalation-using-exploiting-sudo-rights/  
1\. [Ted:1](https://www.hackingarticles.in/ted1-vulnhub-walkthrough/)  
2\. [KFIOFan: 1](https://www.hackingarticles.in/kfiofan1-vulnhub-walkthrough/)  
3\. [21 LTR: Scene1](https://www.hackingarticles.in/hack-the-21ltr-scene-1-vm-boot-to-root/)  
4\. [Skytower](https://www.hackingarticles.in/hack-the-skytower-ctf-chAllenge/)  
5\. [Matrix: 1](https://www.hackingarticles.in/matrix-1-vulnhub-walkthrough/)  
6\. [Sputnik 1](https://www.hackingarticles.in/sputnik-1-vulnhub-walkthrough/)  
7\. [Sunset](https://www.hackingarticles.in/sunset-vulnhub-walkthrough/)  
8\. [DC-2](https://www.hackingarticles.in/dc-2-walkthrough/)  
9\. [Kioptrix: Level 1.2](https://www.hackingarticles.in/hack-the-kioptrix-level-1-2-boot2root-chAllenge/)  
10\. [Matrix-3](https://www.hackingarticles.in/matrix-3-vulnhub-walkthrough/)  

### **SUID Bit**

Set User ID (SUID) is a form of permission that lets the user execute any file with the permissions of a certain user. Those files which have suid permissions run with higher privileges. The maximum number of bits is used to set permission for each user is 7, which is a combination of read (4) write (2) and execute (1) operation. For example, if you set chmod 755, then it will look like as **rwxr-xr-x**. But when special permission is given to each user it becomes SUID, SGID, and sticky bits. When extra bit “4” is set to the user (Owner) it becomes **SUID (Set user ID)**, then it will look like as **rwsr-xr-x.** SUID bits can be manipulated by changing the permission of a file so that we can execute or write it in as we choose to in order to gain access and do the needful.  
Read from here: https://www.hackingarticles.in/linux-privilege-escalation-using-suid-binaries/  
1\. [Kevgir](https://www.hackingarticles.in/hack-kevgir-vm-ctf-challenge/)  
2\. [digitalworld.local – BRAVERY](https://www.hackingarticles.in/digitalworld-local-bravery-vulnhub-walkthrough/)  
3\. [Happycorp: 1](https://www.hackingarticles.in/happycorp1-vulnhub-walkthrough/)  
4\. [FourAndSix: 2](https://www.hackingarticles.in/fourandsix-2-vulnhub-walkthrough/)  
5\. [DC-1](https://www.hackingarticles.in/dc-1-vulnhub-walkthrough/https://www.hackingarticles.in/dc-1-vulnhub-walkthrough/)  
6\. [dpwwn:2](https://www.hackingarticles.in/dpwwn2-vulnhub-walkthrough/)  
7\. [MinU: v2](https://www.hackingarticles.in/minu-v2-vulnhub-walkthrough/)  
8\. [Toppo:1](https://www.hackingarticles.in/hack-the-toppo1-vm-ctf-challenges/)  
9\. [Mr. Robot](https://www.hackingarticles.in/hack-mr-robot-vm-ctf-challenge/)  
10\. [Covfefe](https://www.hackingarticles.in/hack-covfefe-vm-ctf-challenge/)  

### **Kernel Exploit**

Kernel exploit is one of the most commonly used exploits nowadays as it is the most advanced attack there is today. It works for both Windows and Linux. In this attack, malicious code evades and takes control of the root/administrator to bypass user control access and as it abuses kernel.  
1\. [pWnOS -1.0](https://www.hackingarticles.in/hack-the-pwnos-1-0-boot-to-root/)  
2\. [LAMPSecurity: CTF 5](https://www.hackingarticles.in/hack-the-lampsecurity-ctf-5-ctf-challenge)  
3\. [Kioptrix : Level 1.1](https://www.hackingarticles.in/hack-the-kioptrix-level-2-boot2root-challenge/)  
4\. [Hackademic-RTB1](https://www.hackingarticles.in/hack-the-hackademic-rtb1-vm-boot-to-root/)  
5\. [Hackademic-RTB2](https://www.hackingarticles.in/hack-the-hackademic-rtb2-boot2root/)  
6\. [ch4inrulz : 1.0.1](https://www.hackingarticles.in/hack-the-ch4inrulz-1-0-1-ctf-challenge/)  
7\. [Kioprtix: 5](https://www.hackingarticles.in/hack-the-kioptrix-5-ctf-challenge/)  
8\. [Simple](https://www.hackingarticles.in/hack-simple-vm-ctf-challenge/)  
9\. [SecOS: 1](https://www.hackingarticles.in/hack-the-secos1-ctf-challenge/)  
10\. [Droopy](https://www.hackingarticles.in/hack-droopy-vm-ctf-challenge/)  

### **Path Variable**

PATH is an environmental variable in Linux and Unix-like operating systems which specifies all bin and sbin directories that hold all executable programs are stored. When the user runs any command on the terminal, its request to the shell to search for executable files with the help of PATH Variable in response to commands executed by a user. The superuser also usually has /sbin and /usr/sbin entries for easily executing system administration commands.  
Read from here: https://www.hackingarticles.in/linux-privilege-escalation-using-path-variable/  
1\. [PwnLab](https://www.hackingarticles.in/penetration-testing-pwnlab-ctf-challenge/)  
2\. [USV](https://www.hackingarticles.in/hack-usv-vm-ctf-challenge/)  
3\. [Zeus:1](https://www.hackingarticles.in/zeus1-vulnhub-walkthrough/)  
4\. [The Gemini inc](https://www.hackingarticles.in/hack-the-gemini-inc-ctf-challenge/)  
5\. [EW-Skuzzy](https://www.hackingarticles.in/hack-ew-skuzzy-vm-ctf-challenge)  
6\. [Nullbyte](https://www.hackingarticles.in/hack-nullbyte-vm-ctf-challenge/)  
7\. [symfonos : 1](https://www.hackingarticles.in/symfonos1-vulnhub-walkthrough/)  
8\. [Silky-CTF: 0x01](https://www.hackingarticles.in/silky-ctf-0x01-vulnhub-walkthrough/)  
9\. [Beast 2](https://www.hackingarticles.in/beast-2-vulnhub-walkthrough/)  

### **Enumeration**

Enumeration is a phase of attacking where the attacker focuses on traversing through the system and network in order to find useful information such as password hashes, active connections, etc. During this, bash history and config files come handy as they often have the most useful data of which an attacker can take advantage.  
1\. [The Library:1](https://hackingarticles.in/the-library1-vulnhub-walkthrough/)  
2\. [The Library:2](https://www.hackingarticles.in/the-library2-vulnhub-walkthrough/)  
3\. [LAMPSecurity: CTF 4](https://www.hackingarticles.in/hack-the-lampsecurity-ctf4-ctf-challenge/)  
4\. [LAMPSecurity: CTF 7](https://www.hackingarticles.in/hack-the-lampsecurity-ctf-7-ctf-challenge/)  
5\. [Xerxes: 1](https://www.hackingarticles.in/xerxes-1-vulnhub-walkthrough)  
6\. [pWnOS -2.0](https://www.hackingarticles.in/hack-the-pwnos-2-0-boot-2-root-challenge)  
7\. [DE-ICE:S1.130](https://www.hackingarticles.in/hack-the-de-ice-s1-130-boot2root-challenge/)  
8\. [SickOS 1.1](https://www.hackingarticles.in/hack-sickos-1-1-vm-ctf-challenge)  
9\. [Tommyboy](https://www.hackingarticles.in/hack-tommyboy-vm-ctf-challenge)  
10\. [VulnOS: 1](https://www.hackingarticles.in/hack-the-vulnos-1-ctf-challenge)  

### **MySQL**

MySQL provides a mechanism by which the default set of functions can be expanded by means of a custom written dynamic libraries containing User Defined Functions, or UDFs.  

1.  [Kioptrix : Level 1.3](https://www.hackingarticles.in/hack-the-kioptrix-level-1-3-boot2root-challenge/)
2.  [Raven](https://www.hackingarticles.in/hack-the-raven-walkthrough-ctf-challenge/)
3.  [Raven : 2](https://www.hackingarticles.in/raven-2-vulnhub-walkthrough/)

### **Crontab**

Cron Jobs are used for scheduling tasks by executing commands at specific dates and times on the server. They’re most commonly used for sysadmin jobs such as backups or cleaning /tmp/ directories and so on. The word Cron comes from crontab and it is present inside /etc directory.  
Read from here: [https://www.hackingarticles.in/linux-privilege-escalation-by-exploiting-cron-jobs/](https://www.hackingarticles.in/linux-privilege-escalation-by-exploiting-cron-jobs/)  

1.  [Billy Madison](https://www.hackingarticles.in/hack-billy-madison-vm-ctf-challenge/)
2.  [dpwwn: 1](https://www.hackingarticles.in/dpwwn-1-vulnhub-walkthrough/)
3.  [BSides Vancuver: 2018](https://www.hackingarticles.in/hack-the-bsides-vancouver2018-vm-boot2root-challenge/)
4.  [Jarbas : 1](https://www.hackingarticles.in/hack-the-jarbas-1-ctf-challenge/)
5.  [SP:Jerome](https://www.hackingarticles.in/spjerome-vulnhub-walkthrough/)

### **Wildcard Injection**

The wildcard is a character or set of characters that can be used as a replacement for some range/class of characters. Wildcards are interpreted by the shell before any other action is taken therefore one can take the privilege of it to execute an arbitrary command using a wild asterisk (\*) argument.  
Read from here: [https://www.hackingarticles.in/exploiting-wildcard-for-privilege-escalation/](https://www.hackingarticles.in/exploiting-wildcard-for-privilege-escalation/)  

1.  [Milnet](https://www.hackingarticles.in/hack-milnet-vm-ctf-challenge/)
2.  [Pipe](https://www.hackingarticles.in/hack-pipe-vm-ctf-challenge/)

### **Capabilities**

Capabilities are referred to if there are any additional privileges given to a file or directory. This can also be manipulated to our own advantage in order to achieve the desired goal. It can override the permissions or the READ access to a filesystem along with the ability to call chroot.  

1.  [Kuya : 1](https://www.hackingarticles.in/vulnhub-kuya-1-walkthrough/)
2.  [DomDom: 1](https://www.hackingarticles.in/domdom-1-vulnhub-walkthrough/)

### **Writable /etc/passwd file**

/etc/passwd file is the one where passwords and usernames are saved with their every detail possible. So, if by chance you find that this file is writable then you can add your own user with or without password and bypass access control of the system.  

1.  [Hackday Albania](https://www.hackingarticles.in/hack-hackday-albania-vm-ctf-challenge/)
2.  [Billu Box 2](https://www.hackingarticles.in/hack-billu-b0x-vm-boot2root-challenge/)
3.  [Bulldog 2](https://www.hackingarticles.in/hack-the-bulldog2-ctf-challenge/)

### **Writable files or script as root**

Sometimes, there are often files which are writable. Such files can be edited with our developed malicious code. This code can either run as root or can run to gain root access. Thus, the writable files are quite important for privilege escalation.  

1.  [Skydog](https://www.hackingarticles.in/hack-skydog-vm-ctf-challenge/)
2.  [Breach 1.0](https://www.hackingarticles.in/hack-breach-1-0-vm-ctf-challenges/)
3.  [Bot Challenge: Dexter](https://www.hackingarticles.in/hack-bot-challenge-dexter-boot2root-challenge/)
4.  [Fowsniff : 1](https://www.hackingarticles.in/fowsniff-1-vulnhub-walkthrough/)
5.  [Mercy](https://www.hackingarticles.in/mercy-vulnhub-walkthrough/)
6.  [Casino Royale](https://www.hackingarticles.in/casino-royale-1-vulnhub-walkthrough/)
7.  [SP eric](https://www.hackingarticles.in/sp-eric-vulnhub-lab-walkthrough/)
8.  [PumpkinGarden](https://www.hackingarticles.in/pumpkingarden-vulnhub-walkthrough/)
9.  [dpwwn: 1](https://www.hackingarticles.in/dpwwn-1-vulnhub-walkthrough/)
10.  [Tr0ll: 3](https://www.hackingarticles.in/tr0ll-3-vulnhub-walkthrough/)

### **Buffer Overflow**

A buffer is a sequential segment of the memory allocated to hold anything like a character string or an array of integers this particular vulnerability exists when a program tries to put more data in a buffer than it can contain or when a program tries to insert data in memory set past a definitive buffer. Writing outside the bounds of a block of allocated memory can corrupt data, crash the program, or cause the execution of malicious code.  
1\. [Tr0ll 2](https://www.hackingarticles.in/hack-the-tr0ll-2-boot2root-challenge/)  
2\. [IMF](https://www.hackingarticles.in/hack-imf-vm-ctf-challenge/)  
3\. [BSides London 2017](https://www.hackingarticles.in/hack-the-bsides-london-vm-2017boot2root/)  
4\. [PinkyPalace](https://www.hackingarticles.in/hack-the-pinkypalace-vm-ctf-challenge/)  
5\. [ROP Primer](https://www.hackingarticles.in/hack-the-rop-primer-1-0-1-ctf-challenge/)  
6\. [CTF KFIOFAN:2](https://www.hackingarticles.in/ctf-kfiofan-2-vulnhub-walkthorugh/)  
7\. [Kioptrix : Level 1](https://www.hackingarticles.in/hack-the-kioptrix-level-1/)  
8\. [Silky-CTF: 0x02](https://www.hackingarticles.in/silky-ctf-0x02-vulhub-walkthrough/)  

### **Docker**

Docker was introduced to meet all the drawbacks of VMware. Docker has developed the concept of containers, it means whichever application you want to run in a virtual environment, the docker will create a container with the application and it’s every dependency. The only reason it is widely used than VMware is due to its efficiency. In Docker, all of the commands require sudo prefixing them. Docker design modules intrinsically give significant rights to any user who has access to the daemon. The Docker daemon allows access to either the root user or any user in the ‘docker’ group. This means being a member of the ‘docker’ group is same as gaining permanent root access.  

1.  [Donkey Docker](https://www.hackingarticles.in/hack-donkeydocker-ctf-challenge/)
2.  [Game of Thrones](https://www.hackingarticles.in/hack-game-thrones-vm-ctf-challenge/)
3.  [HackinOS : 1](https://www.hackingarticles.in/hackinos1-vulnhub-lab-walkthrough/)