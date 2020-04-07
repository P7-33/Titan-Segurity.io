---
title: 'New Qt5 and OpenSSH in Current'
date: 2020-02-15T05:08:00+01:00
draft: false
---

One of the biggest wish for many people in Slackware community has been approved by Patrick this morning (or night depending on your local time). It's Qt5!! It's one of the main dependency for next Plasma 5 and many applications that has been ported to use Qt5 instead of Qt4.  
  
Another big thing happening in -current is the new OpenSSH 8.2 release which will bring some incompatible changes, especially if you are still using ssh-rsa as the algorithm. To test whether your machine is affected, try to run this command in your shell  
  
```
ssh -oHostKeyAlgorithms=-ssh-rsa user@host
```

If you managed to connect using the above command, it means that your OpenSSH software is fine, but if you don't, then it needs to be upgraded.  
  
I'm still waiting for the next big update Plasma 5, PAM, and XFCE 4.14 to be merged soon. I'm not using the PAM for now as i want to test it later when it has been merged into the main tree. That saves time to remove the \_pam packages later on.