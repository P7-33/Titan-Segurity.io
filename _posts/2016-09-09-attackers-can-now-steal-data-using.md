---
title: 'Attackers Can Now Steal Data Using Screen Brightness'
date: 2020-02-09T09:47:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/02/Screen-brightness-hack-feat.jpg)

Over time, hackers have found numerous ways to exfiltrate data from computers without requiring a network connection. But this might be one of the cleverest ways of stealing data from a computer.  

Researchers from the Ben Gurion University of Israel devised a new way to obtain sensitive information from an “air-gapped” computer just by modulating the brightness of the screen, which basically means hackers can use your PC’s screen brightness to hack you. Sounds unreal, right?  

What is An Air-Gapped Computer?
-------------------------------

  

Now, **an “air-gapped” computer is a computing machine that is isolated from any unsecured networks**. That is, you cannot connect it to the internet or any other machines that connect to the internet. A true air-gapped computer is also physically isolated. This means that you have to use physical devices like USB drives or removable media drives to transfer data.  

In his latest [research](https://arxiv.org/pdf/2002.01078.pdf), Mordechai Guri, the head of cybersecurity at the Ben Gurion University, along with other researchers made a secret optical channel that can be used by an attacker to steal computer data from an air-gapped computer without using any network connectivity or physically contacting the machine.  

_“This covert channel is invisible, and it works even while the user is working on the computer. Malware on a compromised computer can obtain sensitive data (e.g., files, images, encryption keys, and passwords), and modulate it within the screen brightness, invisible to users,”_ the researchers said.  

How the Method Works
--------------------

  

To execute the method, **the attacker controls the LCD screen brightness**, which remains invisible to the naked eye, to covertly modulate binary information in a morse-code like patterns. In LCD screens, to produce a single colour, each pixel has a combination of RGB colours. Now, in this proposed modulation, the RGB combination of each pixel is slightly changed. This remains invisible to the naked eye as it happens very fast and for a very short time.  

![hacking-air-gapped-computers](https://beebom.com/wp-content/uploads/2020/02/hacking-air-gapped-computers.jpg)

Now **the attacker can collect this data stream by video recording the victim computer’s display**. The intruder can use any surveillance camera, security camera, smartphone camera or a webcam for the purpose. Then the attacker can reconstruct the information by using any image processing technique. This video shows a demonstration of the hack done by the researchers.  

  

Do You Need To Worry?
---------------------

  

Now, you do not have to worry about anyone stealing your login ID or password through the window anytime. As the method proposes, the attacker would need to physically breach the to-be compromised machine and have a camera that they control installed within the line of sight. This can be useful for intelligence agencies to perform any high priority intrusions. But no attacker would just sit outside your window to take the login credentials of your Facebook account. So you can chill out and let government agencies worry about this method of stealing data.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/attackers-steal-data-using-screen-brightness/)  
\[the\_ad id='1307'\]