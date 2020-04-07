---
title: '12,000+ Jenkins servers can be used to launch DDoS attacks'
date: 2020-02-12T19:51:00+01:00
draft: false
---

  
According to Radware researchers, a vulnerability (CVE-2020-2100) in 12,000+ Jenkins servers can be exploited to launch and amplify DDoS attacks to internet hosts.  
  

[![](https://1.bp.blogspot.com/-ciVNCa8dSns/Xe0aSKbsGQI/AAAAAAAAMKI/SYwEMJU3LAMyts6Esp0oYDC7MLHXdoyeQCPcBGAYYCw/s640/ball-63527_960_720.jpg)](https://1.bp.blogspot.com/-ciVNCa8dSns/Xe0aSKbsGQI/AAAAAAAAMKI/SYwEMJU3LAMyts6Esp0oYDC7MLHXdoyeQCPcBGAYYCw/s1600/ball-63527_960_720.jpg)

  
  
  
The said vulnerability can also be abused and triggered by a spoofed UDP packet to launch DoS attacks against the internet server in a repeated sequence of replies that can only be stopped by rebooting the server.  
  
 **The vulnerability (CVE-2020-2100) **  
CVE-2020-2100 vulnerability was discovered by Adam Thorn from the University of Cambridge. It is caused by a network discovery service, present by default and enabled in public facing servers.  
  
Radware researchers explains, “The vulnerability allows attackers to abuse Jenkins servers by reflecting UDP requests off port UDP/33848, resulting in an amplified DDoS attack containing Jenkins metadata. This is possible because Jenkins/Hudson servers do not properly monitor network traffic and are left open to discover other Jenkins/Hudson instances”.  
  
 “An attacker can either send a UDP broadcast packet locally to 255.255.255.255:33848 or they could send a UDP multicast packet to JENKINS\_REFLECTOR:33848. When a packet is received, regardless of the payload, Jenkins/Hudson will send an XML response of Jenkins metadata in a datagram to the requesting client, giving attackers the ability to abuse its UDP multicast/broadcast service to carry out DDoS attacks.”  
  
Although the CVE-2020-2100 vulnerability was fixed in Jenkins 2.219 and LTS 2.204.2 two weeks ago.  
  
 “Administrators that need these features can re-enable them again by setting the system property hudson.DNSMultiCast.disabled to false (for DNS multicast) or the system property hudson.udp to 33848, or another port (for UDP broadcast/multicast),” developers from Jenkins explained.  
** The danger from the vulnerability **  
  
Pascal Geenens, Cyber Security Evangelist for Radware said, “Much like was the case with memcached, people that design and develop on the open source Jenkins project assume that these servers will be internally facing”.  
  
But contrary to that, the Jenkins servers were exposed to the public. Nearly 13,000 vulnerable servers were distributed globally including Asia, Europe and North America to the top service providers. “Many DevOps teams depend upon Jenkins to build, test and continuously deploy their applications running in cloud and shared hosting environments such as Amazon, OVH, Hetzner, Host Europe, DigitalOcean, Linode, and many more” Geenens stated.  
  
The researchers concluded, "Combined with over 12,000 exposed Jenkins servers globally, it creates a viable DDoS threat. "

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/31N5dAM