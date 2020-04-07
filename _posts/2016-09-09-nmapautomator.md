---
title: 'nmapAutomator'
date: 2020-01-04T11:57:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-l-0lS2A6wRA/XgJ42hXlDMI/AAAAAAAARSA/tDY1SmNd53wy7JM3_EHckAw8jrEdJrShwCNcBGAsYHQ/s640/nmapAutomator.png)](https://1.bp.blogspot.com/-l-0lS2A6wRA/XgJ42hXlDMI/AAAAAAAARSA/tDY1SmNd53wy7JM3_EHckAw8jrEdJrShwCNcBGAsYHQ/s1600/nmapAutomator.png)

**nmapAutomator - Tool To Automate All Of The Process Of Recon/Enumeration**

  
**nmapAutomator**  
A script that you can run in the background!  
  
**Summary**  
The main goal for this script is to automate all of the process of recon/enumeration that is run every time, and instead focus our attention on real pen testing.  
This will ensure two things:  
1) Automate nmap scans. 2) Always have some [recon](https://www.kitploit.com/search/label/Recon "recon") running in the background.  
Once you find the inital ports in around 10 seconds, you then can start manually looking into those ports, and let the rest run in the background with no interaction from your side whatsoever.  
  
  
**Features:**

1.  **Quick:** Shows all open ports quickly (~15 seconds)
2.  **Basic:** Runs Quick Scan, then a runs more thorough scan on found ports (~5 minutes)
3.  **UDP:** Runs "Basic" on UDP ports (~5 minutes)
4.  **Full:** Runs a full range port scan, then runs a thorough scan on new ports (~5-10 minutes)
5.  **Vulns:** Runs CVE scan and nmap Vulns scan on all found ports (~5-15 minutes)
6.  **Recon:** Runs "Basic" scan "if not yet run", then suggests recon commands "i.e. gobuster, nikto, smbmap" based on the found ports, then prompts to automatically run them
7.  **All:** Runs all the [scans](https://www.kitploit.com/search/label/Scans "scans") consecutively (~20-30 minutes)

I tried to make the script as efficient as possible, so that you would get the results as fast as possible, without duplicating any work.  
  
**Requirements:**  
**Required:**[Gobuster](https://www.kitploit.com/search/label/Gobuster "Gobuster") v3.0 or higher, as it is not backward compatible.  
You can update gobuster on [kali](https://www.kitploit.com/search/label/Kali "kali") using:

```
apt-get update  
apt-get install gobuster --only-upgrade 
```

**Recommended:** nmap [vulners](https://www.kitploit.com/search/label/Vulners "vulners") scrip "for CVE scan"  
[https://github.com/vulnersCom/nmap-vulners](https://github.com/vulnersCom/nmap-vulners "https://github.com/vulnersCom/nmap-vulners")  
  
**Examples of use:**  
./nmapAutomator.sh  
./nmapAutomator.sh 10.1.1.1 All  
./nmapAutomator.sh 10.1.1.1 Basic  
./nmapAutomator.sh 10.1.1.1 Recon  
**If you want to use it anywhere on the system, create a shortcut using:**  
`ln -s /PATH-TO-FOLDER/nmapAutomator.sh /usr/local/bin/`  
  

**[Download nmapAutomator](http://libittarc.com/3EHW "Download nmapAutomator")**

**  
Regards**

**Kang Asu**