---
title: 'Privilege Escalation on Linux with example'
date: 2019-09-26T18:32:00+01:00
draft: false
---

Introduction
------------

One of the most important phase during penetration testing or vulnerability assessment is [Privilege Escalation](http://searchsecurity.techtarget.com/definition/privilege-escalation-attack). During that step, hackers and security researchers attempt to find out a way (exploit, bug, misconfiguration) to escalate between the system accounts. Of course, vertical privilege escalation is the ultimate goal. For many security researchers, this is a fascinating phase.  
In the next lines, we will see together several real examples of privilege escalation. We will use labs that are currently hosted at [Vulnhub](https://www.vulnhub.com/). Of course, we are not going to review the whole exploitation procedure of each lab. Instead, we will suppose that we have already gained access to the machine and, together, we will move from an unprivileged user into the root.  
We will perform all the privilege escalation techniques manually. This means that no automatic tools will be used to escalate the privileges. Of course, though, tools and papers will be given as reference at the end of the article. Before you begin reading the next lines, I suggest you have a look at my personal Privilege Escalation Bible: [G0tmi1k: Basic Linux Privilege Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/) written by the very talented [g0tmi1k](https://twitter.com/g0tmi1k).  
The purpose of the article is to give you an idea of how privilege escalation looks and works on real machines. We will not attempt to explain all the available techniques as this would require several articles and at the same time, g0tmi1k and other people have done this before, perfectly.  

Lab 1: [VulnOS 2](https://www.vulnhub.com/entry/vulnos-2,147/)
--------------------------------------------------------------

VulnOS version 2 is a very common boot to root lab available at Vulnhub. Once someone manages to exploit the vulnerability and gain a shell, we will probably see something like the following:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs1.png)

The things that we should do first are:  

1.  Check the OS Release of the vulnerable system
2.  View its Kernel Version
3.  Check the available users and the current user privileges
4.  List the SUID files. Read more here: [Common Linux Misconfigurations – InfoSec Resources – InfoSec Institute](http://resources.infosecinstitute.com/linux-misconfigurations/)
5.  View the installed packages, programs and running services. Outdated versions might be vulnerable.

Of course, each time we will be looking for other information but for now, the above will do the job.  
Let’s try to view the OS Release of the lab machine. By executing:  
**_$ lsb\_release -a_**  
We can see something like the following:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs2.png)

Moreover, by running:  
**_$ uname -a_**  
We can also see the Kernel Version:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs3.png)

During privilege escalation, we will find ourselves testing again and again. We will be searching for possible techniques to escalate and each time one comes to our mind; we will attempt to apply it. We will be testing exploits against the system, exploits against services, we will brute force credentials and in general, we will be testing all the time.  
Now that we know the OS Release Information, _Ubuntu 14.04.4 LTS_, and the Kernel Version, _3.13.0-24-generic_, the first thing we can try is the popular exploit called: [**overlayfs**](https://www.exploit-db.com/exploits/37292/). This exploit is supposed to work on _Ubuntu 12.04/14.04/14.10/15.04_ and Linux Kernel after 3.13.0 and before 3.19. So, it should work fine. Let’s test it.  
We first move to the _tmp_ directory which we will be able to create a file, paste the exploit code and then compile it.  
The commands we should run are:  
**_$ cd /tmp_**  
**_$ touch exploit.c_**  
**_$ vim exploit.c_**  
Then, we should paste the exploit code inside the file, save and exit. Now, we have to compile the exploit. To do this we run:  
**_$ gcc exploit.c -o exploit_**  
And now we only have to execute the exploit file to see if our exploit works. By running:  
**_$ ./exploit_**  

We can see something like the following:

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs4.png)

As you can see, the exploit has been executed successfully, and we have root access. The python command you can see was used to get a proper shell. The command used:  
**_$ python -c ‘import pty; pty.spawn(“/bin/bash”)’_**  
Even if this wasn’t a difficult lab to perform privilege escalation, the method used is one of the most common techniques, and it applies to several systems. I personally suggest you to always check if the overlayfs exploit works. Keep in mind that there are several versions of this exploit which apply even to newer kernel versions. Have a look here:  

1.  [Linux Kernel 3.13.0 < 3.19 (Ubuntu 12.04/14.04/14.10/15.04) – ‘overlayfs’ Local Root Shell](https://www.exploit-db.com/exploits/37292/)
2.  [Linux Kernel 4.3.3 (Ubuntu 14.04/15.10) – ‘overlayfs’ Local Root Exploit](https://www.exploit-db.com/exploits/39166/)
3.  [Linux Kernel 4.3.3 – ‘overlayfs’ Local Privilege Escalation](https://www.exploit-db.com/exploits/39230/)

Make sure you use the proper one according to the kernel version!  

Lab 2: [Mr.Robot](https://www.vulnhub.com/entry/mr-robot-1,151/)
----------------------------------------------------------------

Mr.Robot is another boot to root challenge and one of the author’s most favorite. I decided to show its privilege escalation part because it will help you understand the importance of the SUID files. If you don’t know what SUID files are, please have a look [here](https://en.wikipedia.org/wiki/Setuid).  
Once we manage to access the shell, we can see something like this:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs5.png)

Here, we have accessed an account with username “**daemon**“. Let’s see how we will manage to escalate from **daemon** to **root**.  
This box is an _Ubuntu 14.04 trusty_ with Linux Kernel version: _3.13.0-55-generic._ All the exploits against the OS and the Linux Kernel have failed.  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs6.png)

Thus, we should come up with a new idea. As mentioned previously, we should always be checking the SUID files available in the system. By running:  
**_$ find / -perm -u=s -type f 2>/dev/null_**  
We can see something like the following:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs7.png)

Here, we have listed all the SUID files. Can you notice something strange? Why would [Nmap](https://nmap.org/) have the SUID flags? Let’s see.  
First, we should run the following command to learn Nmap’s version:  
**_$ /usr/local/bin/nmap –version_**  
And the output is:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs8.png)

An outdated version of nmap is installed! But how can this help us escalate to a privileged user?  
Back in the day, Nmap supported an option called “_**interactive**.”_ With this option, users were able to execute shell commands by using a nmap “shell” (**interactive shell**). Many times, security researchers were using this option to avoid logging their nmap commands in the bash history log file. Here is how nmap interactive looks like:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs9.png)

As we can see, we can execute shell commands by typing “**!**” followed by the command we would like to execute.  
Thus, the: **“!sh”** command should normally pop a shell. And as nmap has the SUID flags, we should normally get a root shell.  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs10.png)

And, we are in! We can now execute commands as root.  
It is true that during your tests you will -probably- never find Nmap 3.48 with SUID flags set. This example was demonstrated to make you understand how important is to check for SUID in Linux. There are several labs at Vulnhub based on this technique. Every time, different programs have been assigned with the SUID flags so that you can experiment with them. Feel free to try them.  

Lab 3: [PwnLab-Init](https://www.vulnhub.com/entry/pwnlab-init,158/)
--------------------------------------------------------------------

**Pwnlab** is another lab hosted by [Vulnhub](https://www.vulnhub.com/). Again, one of the author’s favorite challenges. Once the attacker manages to get a shell (for several accounts but not root), he can see something like this:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs11.png)

Currently, we are logged in as user “**kane**“. Unfortunately for us, the OS Release wasn’t vulnerable to any documented attack. At the same time, none of the kernel exploits helped. Moreover, the SUID files were looking fine except a file located under Kane’s home directory named “**_msgmike._**”  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs12.png)

So, let’s attempt to list the files under the home directory to see what we have.  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs13.png)

From what we can see, we have an [**_ELF 32-bit LSB executable_**](http://manoharvanga.com/hackme/). When executing the file, we get the following error:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs14.png)

This let us know that the program is trying to call the [**_cat_**](http://www.linfo.org/cat.html) command to view the contents of a file called **_msg.txt_** available under the home directory of a user called **_mike_**. Moreover, let’s recall the the file is SUID. What should we do now?  
There is a popular [technique](http://www.dankalia.com/tutor/01005/0100501004.htm) where attackers manage to manipulate the [**$PATH**](http://www.linfo.org/path_env_var.html) bash environmental to escalate their privileges. Imagine what would happen if we edit the $PATH variable and instead of the default value we put a new one, a simple dot (**.**). Whenever a program (executable) is called, bash will look at the “.” directory for the program instead of **_/usr/local/bin, /usr/bin_** and more. Let’s see what this mean.  
  

A normal PATH variable looks like this:

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs15.png)

Whenever I call a program – like cat – bash will look for the above directories for it. Let’s make a file called **cat** with the following contents inside:  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs16.png)

Of course, we must make it executable with the following command:  
**_$ chmod +x cat_**  
Now, let’s change our PATH variable to “.”. This will make bash look at the “.” (current) directory every time it needs to run a program.  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs17.png)

Can you imagine what would happen if we execute the _msgmike_ program again? As you can recall, _msgmike_ executes the cat command to view the contents of a file (_/home/mike/msg.txt_). Now that we have changed the PATH variable, though, it will look for the cat program inside the current directory. As we have created an executable file called cat – which pops a shell – our cat file will be executed, and we should normally get a shell as mike. Let’s see!  

![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/082316_2247_PrivilegeEs18.png)

As you can see, we have successfully logged in as mike! The real challenge doesn’t stop here, though. The next steps to log in as root are not hard, but we will not cover them as they deal with [Command Injection attacks](https://www.owasp.org/index.php/Command_Injection) something that is out of the scope of this article.  
The reason we examined this lab-example is to understand that several times we should think of non-common techniques to perform privilege escalation. It goes without saying that we should first check for common ways to perform privilege escalation but several times you will deal with machines like the previous one.  
I hope you enjoyed this article as much as I did. If you have any questions, please, do not hesitate to comment!