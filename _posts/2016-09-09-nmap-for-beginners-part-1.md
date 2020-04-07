---
title: 'Nmap for Beginners - Part 1'
date: 2020-01-19T18:52:00+01:00
draft: false
---

Nmap is the most well known and most used port scanner in existence. It's not the fastest.. MassScan and UnicornScan are much faster. Masscan is a duplex scanner, using one port to send  packets and another to listen for responses. However, nmap has made great progress over the years in speed. One advantage of nmap is its ability to determine the operating system and applications running on the target. There are other tools like p0f that do this as well, but this capability is built into nmap.  
But the best feature of nmap besides port scanning is its scripting engine. nmap has hundreds of scripts, written in NSE, the Nmap Scripting Engine, that can check for vulnerable versions, test for misconfigurations that allow techniques like SQL injections and cross site scripting and dozens of other tests.  
Using nothing but nmap, you can do a  Nessus like vulnerability scan of an end host.  
  
The simplest scan would be nmap . That's most basic nmap scan you can do. Takes all the defaults. Syn scan if you are root, Connect scan if not. Uses the Nmap default ports which is a mixture of server and ephemeral ports the author, Fyodor, has deemed the most common. Output to stdout. I'm on MacOS here but the commands I use would be the same for Linux.  
  

[![](https://1.bp.blogspot.com/-9nFtSR-0Fpo/XiSWOUPq1nI/AAAAAAAAaVE/nLv0ru8tBhYoiGrIvr6DjIBjw2zgbQfJgCLcBGAsYHQ/s640/Greenshot%2B2020-01-19%2B12.46.40.png)](https://1.bp.blogspot.com/-9nFtSR-0Fpo/XiSWOUPq1nI/AAAAAAAAaVE/nLv0ru8tBhYoiGrIvr6DjIBjw2zgbQfJgCLcBGAsYHQ/s1600/Greenshot%2B2020-01-19%2B12.46.40.png)