---
title: 'Multiple Vulnerabilities found in SATCOM internet access terminal
Cobham EXPLORER 710'
date: 2019-10-12T19:04:00+01:00
draft: false
---

  

[![](https://1.bp.blogspot.com/-nT46cRsK4i0/XaHvDL-Xy2I/AAAAAAAAAS4/WfxqKTlkiRIFzWHUlbXI2NAwvsb66gvUQCLcBGAsYHQ/s640/wlan-1494537_960_720.jpg)](https://1.bp.blogspot.com/-nT46cRsK4i0/XaHvDL-Xy2I/AAAAAAAAAS4/WfxqKTlkiRIFzWHUlbXI2NAwvsb66gvUQCLcBGAsYHQ/s1600/wlan-1494537_960_720.jpg)

  
CERT/CC researchers found multiple vulnerabilities as they examined Satcom terminal Cobham EXPLORER 710 as an extension of IOActive’s findings in 2014. These new vulnerabilities could affect both the device and firmware.  
  
These frailties could give attackers unauthentic access to sensitive information, control of the device, create or implant backdoor, DoS attack and more.  
  
Cobham EXPLORER 710 is a portable satellite terminal, broadband global area network (bgan) through telephony. The device provides internet connection through satellite communications setting new standards for size, speed and features.  
  
 EXPLORER 710 is a sophisticated communication tool for broadcasting, streaming and other IP based industry applications with a speed of 1 Mbps and higher. It is used in various sectors as Commercial aerospace, military defenses, space systems, SATCOM and more.  
  
 **The sat-com terminal, firmware version 1.07 is affected with 6 vulnerabilities listed below-**  
** • CVE-2019-9529 – Authentication Failure **  
  
This failure arises due to the web portal having no authentication by default, this could lead to any attacker connected to the device to gain access to the portal and perform changes.  
  
 • **CVE-2019-9530 – Unrestricted Directory Access**  
  
There are no restrictions on access to the webroot directory, creating a liability as hackers can read, access or download any file in the webroot directory.  
  
 **• CVE-2019-9531 – Authentication Failure to port 5454 **  
  
This vulnerability allows attackers to connect to port 5454 through Telnet and execute 86 Attention (AT) commands, and gain illegal access.  
  
 • **CVE-2019-9532 – Text Data Exchange **  
  
The web application portal passes the login password in cleartext, it could easily give way to miscreant to intercept the password.  
** • CVE-2019-9533 – Default Login Credentials**  
  
The root password is the same for all devices, this could allow to reverse-engineer the password in all available versions.  
  
** • CVE-2019-9534 – Validate Failure**  
  
According to CERT/CC researchers, "The device does not validate its firmware image. Development scripts left in the firmware can be used to upload a custom firmware image that the device runs. This could allow an unauthenticated, local attacker to upload their own firmware that could be used to intercept or modify traffic, spoof or intercept GPS traffic, exfiltrate private data, hide a backdoor, or cause a denial-of-service."  
  
Apart from the above gaps in security, the researchers also discovered some configuration issues, missing security headers and problems in default wifi password ( being same as same as serial number) which are gravely dangerous to the device and leave it susceptible to cross-site scripting and clickjacking.  
  
 The researchers said they currently don't have any practical solutions to these problems.

  
  
from E Hacking News - Latest Hacker News and IT Security News https://ift.tt/2IL5JH6