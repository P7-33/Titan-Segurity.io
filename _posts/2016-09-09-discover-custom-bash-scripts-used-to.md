---
title: 'discover: A Custom Bash Scripts Used To Perform Pentesting Tasks With Metasploit'
date: 2019-09-26T10:28:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-hjLsH1N-tQw/XYx6N_8rghI/AAAAAAAAOyw/QiOkTHMxAEE7HREJ-_k2aqRTwdhkrUrvQCLcBGAsYHQ/s1600/Discover.png)](https://1.bp.blogspot.com/-hjLsH1N-tQw/XYx6N_8rghI/AAAAAAAAOyw/QiOkTHMxAEE7HREJ-_k2aqRTwdhkrUrvQCLcBGAsYHQ/s1600/Discover.png)

**About discover:** discover is a custom bash scripts used to automate various penetration testing tasks including recon, scanning, parsing, and creating malicious payloads and listeners with [Metasploit Framework](http://bit.ly/2JkoOl9). For use with Kali Linux, Parrot Security OS and the [Penetration Testers Framework (PTF)](http://bit.ly/2K3rsYS).  
  
**About authors:**  

*   Lee Baird: [@discoverscripts](https://twitter.com/discoverscripts)
*   Jay "L1ghtn1ng" Townsend: [@jay\_townsend1](https://twitter.com/jay_townsend1)
*   Jason Ashton: [@ninewires](https://twitter.com/ninewires)

  

**discover Installation and Updating**

  

  

**About RECON in discover**  
**_Domain_**

`RECON`  
`  
1. Passive`  
`2. Active`  
`3. Import names into an existing recon-ng workspace`  
`4. Previous menu`  
  
   Passive uses ARIN, dnsrecon, goofile, goog-mail, goohost, theHarvester, [Metasploit Framework](http://bit.ly/2JkoOl9), URLCrazy, Whois, multiple websites, and recon-ng.

  

   Active uses dnsrecon, WAF00W, traceroute, [Whatweb](http://bit.ly/2H8IvZK), and recon-ng.  
   _\[\*\]_ Acquire API keys for Bing, Builtwith, Fullcontact, GitHub, Google, Hashes, Hunter, SecurityTrails, and Shodan for maximum results with recon-ng and theHarvester.

  

`API key locations:`  
`recon-ng`  
`   show keys`  
`   keys add bing_api`  
`theHarvester`  
`   /opt/theHarvester/api-keys.yaml`

  
   **_Person:_** Combines info from multiple websites.  
  
`RECON`  
`  
First name:`  
`Last name:`  
**_   Parse salesforce:_** Gather names and positions into a clean list.  
  
`Create a free account at salesforce (https://connect.data.com/login).`  
`Perform a search on your target company > select the company name > see all.`  
`Copy the results into a new file.`  
`Enter the location of your list:`  
  
**About SCANNING in discover**  
_**Generate target list:**_ Use different tools to create a target list including Angry IP Scanner, arp-scan, netdiscover and nmap pingsweep.  
  
`SCANNING`  
`1. Local area network`  
`2. NetBIOS`  
`3. netdiscover`  
`4. Ping sweep`  
`5. Previous menu`  
  
_**   CIDR, List, IP, Range, or URL**_  
  
`Type of scan:`  
`  
1. External`  
`2. Internal`  
`3. Previous menu`  
  

*   External scan will set the nmap source port to 53 and the max-rrt-timeout to 1500ms.
*   Internal scan will set the nmap source port to 88 and the max-rrt-timeout to 500ms.
*   Nmap is used to perform host discovery, port scanning, service enumeration and OS identification.
*   Matching nmap scripts are used for additional enumeration.
*   Addition tools: enum4linux, smbclient, and ike-scan.
*   Matching Metasploit auxiliary modules are also leveraged.

  
**About WEB in discover**  
   **_Insecure direct object reference_**  
  
`Using Burp, authenticate to a site, map & Spider, then log out.  
Target > Site map > select the URL > right click > Copy URLs in this host.`  
`Paste the results into a new file.  
  
`  
`Enter the location of your file:`  
  
   **Open multiple tabs in Firefox**  
  
`Open multiple tabs in Firefox with:`  
`  
1. List`  
`2. Directories from robots.txt.`  
`3. Previous menu`  
  

*   Use a list containing IPs and/or URLs.
*   Use wget to pull a domain's robot.txt file, then open all of the directories.

  
**_Nikto_**  
  
`Run multiple instances of Nikto in parallel.`  
`1. List of IPs.`  
`2. List of IP:port.`  
`3. Previous menu`  
**_   SSL: _**Use sslscan and sslyze to check for SSL/TLS certificate issues.  
  
`Check for SSL certificate issues.`  
`  
Enter the location of your list:`  
  
**About MISC in discover**  
   **_Parse XML_**  
  
`Parse XML to CSV.`  
`  
1. Burp (Base64)`  
`2. Nessus (.nessus)`  
`3. Nexpose (XML 2.0)`  
`4. Nmap`  
`5. Qualys`  
`6. revious menu`  
  
   **_Generate a malicious payload_**  
  
`Malicious Payloads`  
`1. android/meterpreter/reverse_tcp`  
`2. cmd/windows/reverse_powershell`  
`3. java/jsp_shell_reverse_tcp (Linux)`  
`4. java/jsp_shell_reverse_tcp (Windows)`  
`5. linux/x64/meterpreter_reverse_https`  
`6. linux/x64/meterpreter_reverse_tcp`  
`7. linux/x64/shell/reverse_tcp`  
`8. osx/x64/meterpreter_reverse_https`  
`9. osx/x64/meterpreter_reverse_tcp`  
`10. php/meterpreter/reverse_tcp`  
`11. python/meterpreter_reverse_https 12. python/meterpreter_reverse_tcp`  
`13. windows/x64/meterpreter_reverse_https`  
`14. windows/x64/meterpreter_reverse_tcp`  
`15. Previous menu`  
  
   **_Start a Metasploit listener_**  
  
`Metasploit Listeners`  
`1. android/meterpreter/reverse_tcp`  
`2. cmd/windows/reverse_powershell`  
`3. java/jsp_shell_reverse_tcp`  
`4. linux/x64/meterpreter_reverse_https`  
`5. linux/x64/meterpreter_reverse_tcp`  
`6. linux/x64/shell/reverse_tcp`  
`7. osx/x64/meterpreter_reverse_https`  
`8. osx/x64/meterpreter_reverse_tcp`  
`9. php/meterpreter/reverse_tcp`  
`10. python/meterpreter_reverse_https`  
`11. python/meterpreter_reverse_tcp`  
`12. windows/x64/meterpreter_reverse_https`  
`13. windows/x64/meterpreter_reverse_tcp`  
`14. Previous menu`  
  

**[Download discover](https://github.com/leebaird/discover)**