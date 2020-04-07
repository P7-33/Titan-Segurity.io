---
title: 'Haxmas Tools'
date: 2020-01-01T05:11:00+01:00
draft: false
---

One of my favorite winter break traditions is getting some coding in around new years. I don't always get a lot of time, but I try to do at least something each year; this usually means a few really small tools, due to random bits of available time. This year I was able to work on some offensive security helper utilities. These are all quick, single purpose command line utilities or libraries in the effort of speeding up my own internal pentest operations. Specifically, many of these tools further enable [go-netscan](https://github.com/emperorcow/go-netscan), a go [hydra](https://github.com/vanhauser-thc/thc-hydra) rewrite, although they can also be used for hydra the same way.  
  

*   I added two new [scanner modules](https://github.com/emperorcow/go-netscan/tree/master/scanners) for go-netscan, an [ftp scanner](https://github.com/emperorcow/go-netscan/blob/master/scanners/ftp/ftp.go) and an [smtp scanner](https://github.com/emperorcow/go-netscan/blob/master/scanners/smtp/smtp.go). This keeps the momentum rolling on a great credential verification tool, but there are still more scanner modules to add. Since the rewrite from GoRedShell it's very easy to add new modules to go-netscan. If there is a protocol your trying to learn in go I highly suggesting adding the authentication parts to go-netscan!
  
*   I wrote a small utility for [converting nmap xml results into target files](https://github.com/ahhh/nmap-to-netscan/blob/master/toNetscan.go) for go-netscan and hydra. It's a really simple utility, it takes an nmap.xml in file, and you specify a protocol supported by go-netscan, and the tool will output a file of the format "targetip:port" for that service. The idea is we can automate nmap scans, then use this tool to automatically parse the results, and then have go-netscan automatically consuming the target files.
  
*   This is another small [utility for preparing credential files](https://github.com/ahhh/PrepCreds) for go-netscan and hydra. The idea is you have a list of usernames or a list of passwords and you want to quickly generate a file of the format "username:password". This will continue to append new runs to the same out file, allowing you to add a single user at a time with a password list, or combine files of usernames and passwords either via depth (user) or breadth (spray). It's just a switch on some very simple for loops, that shuffle some files together, but this is a task I do so often when credential spraying it is bound to save some time.
  
*   Finally, I wrote a [small DNS over HTTP (DoH) client](https://github.com/ahhh/godns/blob/master/godns.go). I recently saw a presentation on using this technique offensively and I have a strong feeling we are going to see a lot more of this in 2020, and I also predict defenders having some visibility issues here. Classically, whereas DNS was a choke point for defenders I think DoH will allow attacks to establish new C2 quickly with little external monitoring.  
    

  
There you go, just some quick tools to make my 2020 a little easier, and to help me leverage my other tools like [go-netscan](https://lockboxx.blogspot.com/2019/09/go-netscan.html) more. Credential harvesting and spraying is such a common, iterative task on internal red teaming, I was surprised I didn't already have tools for preparing these lists. In fairness I've just written a simple bash loop in the past, but I hope having the tools will allow me to automate more of these actions for rescanning and rechecking harvested credentials. I also predict DNS over HTTP being a troublesome protocol for blue teams in the near future, hence the tooling, as it's something teams should ensure they have insight into now. Let me know if you wrote any tools this break or if these tools inspired you in any way in the comments! See you all in 2020 :\]  
  

[![](https://1.bp.blogspot.com/-DJi0b_Wg3wU/XgwU4rgwHrI/AAAAAAAALIQ/R-THQp51VCw1sThEqbrpg7KnrkjYQA-cQCEwYBhgL/s400/c2020.jpg)](https://1.bp.blogspot.com/-DJi0b_Wg3wU/XgwU4rgwHrI/AAAAAAAALIQ/R-THQp51VCw1sThEqbrpg7KnrkjYQA-cQCEwYBhgL/s1600/c2020.jpg)