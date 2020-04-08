---
title: 'HA: Dhanush Vulnhub Walkthrough'
date: 2019-11-28T15:54:00+01:00
draft: false
---

Today we are going to solve our Boot to Root challenge called “HA Dhanush”. We have developed this lab for the purpose of online penetration practices. It is based on the weapon that was part of all the wars in medieval times. The Bow and Arrow. As the lab is titled Dhanush. Some information about Indian Mythology and Bows might help. Let’s Solve it!!

**Download [Here](https://www.vulnhub.com/entry/ha-dhanush,396/)**

**Level: Intermediate**

**Task:** To Enumerate the Target Machine and Get the Root Access.

### **Penetration Methodologies**

*   **Network Scanning**
    *   Netdiscover
    *   Nmap Scan
*   **Enumeration**
    *   Browsing HTTP Service
    *   Creating a Dictionary from the Webpage
*   **Exploitation**
    *   Bruteforce the SSH
    *   Generating SSH Public key for another user
    *   Logging in as another user
*   **Privilege Escalation**
    *   Identify Sudo Rights to zip command
    *   Abusing Sudo Rights
*   **Reading Root Flag**

**Walkthrough**

### **Network Scanning**

After downloading, run the Machine in VMWare Workstation. To work on the machine, we will be needing its IP Address. For this, we will be using the netdiscover command. After matching the MAC and IP Address we found the Virtual Machine IP Address to be 192.168.1.101.

```
netdiscover
```

![](https://i2.wp.com/1.bp.blogspot.com/-NmgSmoTI3aA/Xd_RdjqlNZI/AAAAAAAAhs0/HlmwYc0J_9cf76oYqt3PTvOVcPhnHkOkgCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now that we have the Target Machine IP Address, our next logical step would be to do a port scan on the target to get information about the various services that are running on the target machine. We usually do just the Aggressive Scan, but in this case, we are going for all port scan. By default, Nmap scans the most common 1,000 ports for each protocol. So, we can specify **\-p-** to scan ports from 1 through 65535. This is done as it is safe to practice to change the port of a service to an uncommon port. After the scan of all the ports, we see that we have the HTTP service (80), SSH service (65345) running on the Target Machine.

```
nmap -p- -A 192.168.1.101
```

### ![](https://i0.wp.com/1.bp.blogspot.com/-FGb8gfbyQ8Y/Xd_RdqmuJ4I/AAAAAAAAhs4/yMBTh209ccUF1HadDuYZLAS5MZebIQlagCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

Moving on, we observed that we have the HTTP service running. It is probable that a web page is hosted. So, we decided to take a look through our Web Browser. We did thorough browsing of the webpage. We went through its source code and images, but there was no way in or any hint.

![](https://i0.wp.com/1.bp.blogspot.com/-Y282-jlxmn4/Xd_RdWGXpDI/AAAAAAAAhsw/g74UagRC3kktypo8XG21iiel32UQ72xdACLcBGAsYHQ/s1600/3.jpg?w=687&ssl=1)

Now, before moving further, we thought as this webpage contains tons of information over the Dhanush. Also, these can be probably usernames or passwords. So, we decided to make a dictionary using the cewl command.

```
cewl http://192.168.1.101/ -w dict.txt  
cat dict.txt
```

![](https://i2.wp.com/1.bp.blogspot.com/-MZuWNn5zVA8/Xd_ReHDKHgI/AAAAAAAAhs8/-dsHeIyN7EgE_e6D68ZnaFQW5OIjP5QXQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

### **Exploitation**

We decide to start our attempt to exploit this target machine from the port which the author has gone lengths to protect from the naked eye. The port number 65345 with the SSH service. As we have no usernames or the passwords so we decide to bruteforce this ssh login using the dictionary that we just created. We will be using the hydra for the login bruteforce. We are in luck; we got the login credentials for the SSH.

```
Username: pinak  
Password: Gandiv  
hydra -L user.txt -P dict.txt 192.168.1.101 ssh -s 65345 -e nsr
```

![](https://i0.wp.com/1.bp.blogspot.com/-Hc3jJR6tjhs/Xd_ReWvlp6I/AAAAAAAAhtA/58IR_YmNECALTavbSQ1eIFGxdcPIpWauQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Now that we have the login credentials for the SSH, we decided to login and take a look. We ran the sudo -l command to check the sudoers list and found that cp command which works runs as sarang user without any password, hence it can be used. So, we decided to take a look at the user sarang. In the home directory of sarang we see a hidden directory labelled “.ssh”. We tried to open it but it was restricted.

```
ssh pinak@192.168.101 -p 65345  
sudo -l  
cd /home/sarang  
ls -la  
cd .ssh
```

![](https://i1.wp.com/1.bp.blogspot.com/-UvGb7B1z6WA/Xd_RerRGjHI/AAAAAAAAhtE/sYVQwlHmceg2kMsaAfwbWQlqhogd1EwtACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

We decided to use the cp command to get inside the sarang user. To do this we will be needing the ssh keys to be present in the .ssh directory inside the sarang user home directory. Now although the file is restricted to read we can use the cp command to send the keys inside that directory. To do this first we need to generate those keys. We will be using the ssh-keygen for that particular purpose. After working with ssh-keygen, we move into the .ssh directory inside the pinak user home directory to find the id\_rsa public key. We gave it proper permissions. And moved it to the pinak user home directory as shown in the image given.

```
ssh-keygen  
cd .ssh  
ls  
chmod 777 id\_rsa.pub  
cp id\_rsa.pub /home/pinak
```

![](https://i1.wp.com/1.bp.blogspot.com/-5beNO_y2Hts/Xd_RfIl53ZI/AAAAAAAAhtI/jyga9pv0BcA7hBUq8dDdpkRgMWENHShLgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Now that we have transferred the public key, its time use the cp command as user sarang to copy the public key inside the .ssh directory in sarang user home directory. We need to use sudo along with the cp command and provide the source directory and destination directory. After doing this, all we need it to login as sarang with the key that we just transferred. We can see that it works nicely. After the successful login as the user sarang, we ran the sudo -l command again as this user is not root and out target is to get root. We see that the zip command has the sudo right that can be abused to escalate privilege on this machine.

```
sudo -u sarang /bin/cp ./id\_rsa.pub /home/sarang/.ssh/authorized\_keys  
ssh sarang@127.0.0.1 -i /.ssh/id\_rsa -p 65345  
sudo -l
```

![](https://i0.wp.com/1.bp.blogspot.com/-4wWVbk0mWaE/Xd_RfUWoRqI/AAAAAAAAhtM/jZ3E9RSUr3M-mBhv0BDZ8gJ2ZPh-kd25ACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

### **Privilege Escalation**

We use recently logged in through ssh as user sarang. Then we use the sudo command to list all the commands the user can run with root privileges and we can see that the user can run zip commands as root without the need to enter any password.

So, now in the process of escalating the privileges from “sarang” to “root”. At first, we create a file ‘raj’ than we perform three different tasks in a single line of code: first, we zip the file ‘raj’ second move it to /home/raj.zip folder and lastly unzip it which will pop the root shell.

```
touch raj  
pwd  
sudo zip /tmp/raj.zip /home/sarang/raj -T --unzip-command="sh -c /bin/bash"  
cd /root  
ls  
cat flag.txt
```

Finally, we get ‘flag.txt’ inside the root directory. Hence, we accomplished our mission to get the root shell on this Boot2Root Machine.

![](https://i1.wp.com/1.bp.blogspot.com/-NOjCzRKtBbM/Xd_RfpoUxmI/AAAAAAAAhtQ/5nDzwxmnbkk8uHpqZKnvOo28Ly0bR1OxwCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

**Author: Pavandeep Singh** is a Technical Writer, Researcher and Penetration Tester Contact **[here](https://www.linkedin.com/in/pavandeep-singh-6b1074132)**

The post [HA: Dhanush Vulnhub Walkthrough](https://www.hackingarticles.in/ha-dhanush-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/33qaehJ