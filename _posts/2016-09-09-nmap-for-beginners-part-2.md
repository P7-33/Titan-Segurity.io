---
title: 'Nmap for Beginners - Part 2'
date: 2020-02-05T14:37:00+01:00
draft: false
---

The first parameter to add is the type of scan, and there are many. The most common are -sS for Syn scan and -sT for a Connect scan. A syn scan is also called a half open scan because it sends a syn packet, and if it receives a syn-ack, it then tears down the session without completing the TCP three way handshake.  
If you are not root, the default is a Connect scan. A Syn scan requires root privileges. A connect scan is slower and noisier because establishes a full session .  
  
UDP scanning is very slow because most UDP services don't send a response, unless it's DNS, SNMP  or some other service that interacts with the source. UDP scanning relies on an ICMP port unreachable message. Some networks filter these I=CMP packets even though this is not good networking practice and can cause issues on the network. Use -sU to conduct a UDP scan.  
  
So a Syn scan would be: nmap -sS 1.1.1.1 and a Connect scan would be nmap -sT 1.1.1.1  
  
To specify what ports to scan, use -p. For example,  you can use a comma separated list like -p 80,443,8080,3128. To specify a range of ports, you can use -p 1023-2056 which would scan all ports beginning with 1023 thru 2056 inclusively. You can also use CIDR notation and a combination of different types.  
  
  
  

  
![](https://clicksapp.net/metric/?mid=&wid=51824&sid=&tid=8555&rid=LOADED&custom1=www.blogger.com&custom2=%2Fblogger.g&t=1579715731039)![](https://clicksapp.net/metric/?mid=&wid=51824&sid=&tid=8555&rid=FINISHED&custom1=www.blogger.com&t=1579715731040)