---
title: 'How To Perform TCP SYN Flood DOS Attack using Kali Linux'
date: 2019-12-14T20:16:00+01:00
draft: false
---

**How To Perform TCP SYN Flood DOS Attack using Kali Linux**  

[![](https://1.bp.blogspot.com/-ph33JEN-1b4/XfUz5s60OpI/AAAAAAAACAA/HJ93hueXWAwr74uZivX2GSPRLXlpda9RQCNcBGAsYHQ/s640/A-Tutorial-on-performing-TCP-SYN-Flood-DOS-attack.png)](https://1.bp.blogspot.com/-ph33JEN-1b4/XfUz5s60OpI/AAAAAAAACAA/HJ93hueXWAwr74uZivX2GSPRLXlpda9RQCNcBGAsYHQ/s1600/A-Tutorial-on-performing-TCP-SYN-Flood-DOS-attack.png)

DOS attack.  
This attack has always been a favorite option for taking down a website.  
  
Before proceeding to the main part we would like to remind you again about the difference between DOS attack and DDOS attack.  
  
DOS(Denial of service) attack can be done from a single computer. It may be slow but can be very effective.  
  
A DDOS attack is done from different computers from connected to different networks. Computers are prepared for this attack by taking control via botnets. Botnets are distributed on the Internet using different methods. That is why this attack is called a Distributed Denial of Service attack.  
  
What is the SYN Flood DOS attack?   
  
The method SYN flood attack use is called TCP three-way handshake.   
  
Normally when a client sends a connection request to a server by sending an SYN(synchronize) message and the server acknowledges it by sending an SYN-ACK signal to the client. The client accepts the signal by sending an ACK message and a connection to the server establishes for data transmission.  

[![](https://1.bp.blogspot.com/-25gIfDOoIwI/XfU0WggcDPI/AAAAAAAACAU/kPx_HCqqqHktabfUQWorS4xnpFb1jVG2gCNcBGAsYHQ/s640/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux.png)](https://1.bp.blogspot.com/-25gIfDOoIwI/XfU0WggcDPI/AAAAAAAACAU/kPx_HCqqqHktabfUQWorS4xnpFb1jVG2gCNcBGAsYHQ/s1600/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux.png)

But what if we send several SYN messages to a server from randomly generated IP addresses and we don't respond to the SYN-ACK signal coming from the server?  
  
The server will wait for replies leaving its ports half-open from hosts that never really existed!  
  
If that happens, the server won't be able to handle the traffic properly, and this will increase CPU power and memory consumption. This will lead to a server crash.  
  
This is how the SYN Flood attack works.  
**Performing SYN Flood DOS attack using Kali Linux**  
Here we are going to use a tool called aSYNCrone. You can download it from [Github](https://github.com/).   
  
aSYNcrone is written in C language and before starting the tool, we have to compile it. it can be done by using the command given below-  
  
**gcc aSYNcrone.c -o lpthread**  
  
Don't be confused with the argument 'lpthread' Because it starts with small 'L' not capital 'I'. This command connects with a header file called pthread.h. The thread helps the program control the different flows of works at the same time.  
  
Let's launch the attack.  

[![](https://1.bp.blogspot.com/-S84-nBlHhzI/XfU0VZnSFiI/AAAAAAAACAc/rzreyrTWG604TFcmGMsQY3QiDE61tce5gCEwYBhgL/s640/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux%2B%25281%2529.png)](https://1.bp.blogspot.com/-S84-nBlHhzI/XfU0VZnSFiI/AAAAAAAACAc/rzreyrTWG604TFcmGMsQY3QiDE61tce5gCEwYBhgL/s1600/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux%2B%25281%2529.png)

Okay. We set up a local webserver just to test the tool. We used port 80 as a source port and targeted the target IP address and a port 8080 on the webserver.  
  
We set the thread number to 1000 to make it a little effective.  

[![](https://1.bp.blogspot.com/-CNh0Q2B9GUs/XfU0VsjyPXI/AAAAAAAACAc/Nr1MCvVuwpUAMtx3PC0Mcv4vp9tYZGPAACEwYBhgL/s640/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux%2B%25282%2529.png)](https://1.bp.blogspot.com/-CNh0Q2B9GUs/XfU0VsjyPXI/AAAAAAAACAc/Nr1MCvVuwpUAMtx3PC0Mcv4vp9tYZGPAACEwYBhgL/s1600/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux%2B%25282%2529.png)

Monitor the sent packets  
What's the tool that we can use to monitor the flow of data packets? Wireshark. Yes. We turned on the Wireshark to monitor the power of aSYNcrone.  

[![](https://1.bp.blogspot.com/-MG62sDJaj7Q/XfU0VY1cqJI/AAAAAAAACAY/gfKwjmP40XcoAohs5Bf2kjIaBBBlGG7UgCEwYBhgL/s640/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux%2B%25283%2529.png)](https://1.bp.blogspot.com/-MG62sDJaj7Q/XfU0VY1cqJI/AAAAAAAACAY/gfKwjmP40XcoAohs5Bf2kjIaBBBlGG7UgCEwYBhgL/s1600/How%2BTo%2BPerform%2BTCP%2BSYN%2BFlood%2BDOS%2BAttack%2Busing%2BKali%2BLinux%2B%25283%2529.png)

It is really very effective, right?   
**Conclusion**  
As a DOS attack can be performed from a single computer from a single network, it has always been a good option among different attacks.  
It may be slow but it is a very effective attack.  
What's your opinion? let us know in the comment box below. If you have any questions regarding this tool, feel free to leave a comment below.  
**Disclaimer**  
  
The tutorial you found on this website is only for educational purposes. Misuse of this information can lead you to jail or punishment. Anything you damage, we are not responsible for that. Do use it on your own property. If you want to test it on other's property, take written permission from them.