---
title: 'BruteSpray: A Brute-forcer From Nmap Output And Automatically Attempts Default Creds On Found Services'
date: 2019-10-10T16:40:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-Ktg6Dld8d_A/XZ7xPXgr5LI/AAAAAAAAO3c/tphdcZsQ_A4iZhjNLDsVHJdsRhHCIwNGQCLcBGAsYHQ/s1600/Brutespray.png)](https://1.bp.blogspot.com/-Ktg6Dld8d_A/XZ7xPXgr5LI/AAAAAAAAO3c/tphdcZsQ_A4iZhjNLDsVHJdsRhHCIwNGQCLcBGAsYHQ/s1600/Brutespray.png)

**About BruteSpray:** BruteSpray takes nmap GNMAP/XML output or newline seperated JSONS and automatically brute-forces services with default credentials using Medusa. BruteSpray can even find non-standard ports by using the `-sV` inside Nmap.  

  

**BruteSpay's Installation**

   With Debian users, the only thing you need to do is this command:  
`sudo apt install brutespray`

  
   For Arch Linux user, you must install Medusa first: `sudo pacman -S medusa`  
  
   And then, enter these commands to install BruteSpray:  
  
**Supported Services:** ssh, ftp, telnet, vnc, mssql, mysql, postgresql, rsh, imap, nntpp, canywhere, pop3, rexec, rlogin, smbnt, smtp, svn, vmauthdv, snmp.  
  
**How to use BruteSpray?**  

[![](https://1.bp.blogspot.com/-H8Oi1XoOe9k/XZ72dJS7k2I/AAAAAAAAO30/CC47BDYaEDgb1oW6lYiNMfWu74oXVURSwCLcBGAsYHQ/s1600/BruteSpray%2Bhelping%2Bmenu.png)](https://1.bp.blogspot.com/-H8Oi1XoOe9k/XZ72dJS7k2I/AAAAAAAAO30/CC47BDYaEDgb1oW6lYiNMfWu74oXVURSwCLcBGAsYHQ/s1600/BruteSpray%2Bhelping%2Bmenu.png)

   First do an Nmap scan with `-oG nmap.gnmap` or `-oX nmap.xml`.  
   Command: `python3 brutespray.py -h`  
   Command: `python3 brutespray.py --file nmap.gnmap`  
   Command: `python3 brutesrpay.py --file nmap.xml`  
   Command: `python3 brutespray.py --file nmap.xml -i`  
  
   You can watch more details here:  

  
**Examples**  

[![](https://1.bp.blogspot.com/-m9GWothn1AY/XZ71VKbLU3I/AAAAAAAAO3o/jetzuNhQ12QPC7BY9Tta5-rets_rAoSZgCLcBGAsYHQ/s1600/Medusa%2Bbrute%2Bforcing.png)](https://1.bp.blogspot.com/-m9GWothn1AY/XZ71VKbLU3I/AAAAAAAAO3o/jetzuNhQ12QPC7BY9Tta5-rets_rAoSZgCLcBGAsYHQ/s1600/Medusa%2Bbrute%2Bforcing.png)

   **_Using Custom Wordlists:_**  
`python3 brutespray.py --file nmap.gnmap -U /usr/share/wordlist/user.txt -P /usr/share/wordlist/pass.txt --threads 5 --hosts 5`  
  
   **_Brute-Forcing Specific Services:_**  
`python3 brutespray.py --file nmap.gnmap --service ftp,ssh,telnet --threads 5 --hosts 5`  
  
   **_Specific Credentials:_**  
`python3 brutespray.py --file nmap.gnmap -u admin -p password --threads 5 --hosts 5`  
  
   **_Continue After Success:_**  
`python3 brutespray.py --file nmap.gnmap --threads 5 --hosts 5 -c`  
  
   **_Use Nmap XML Output:_**  
`python3 brutespray.py --file nmap.xml --threads 5 --hosts 5`  
  
   **_Use JSON Output:_**  
`python3 brutespray.py --file out.json --threads 5 --hosts 5`  
  
   **_Interactive Mode:_** `python3 brutespray.py --file nmap.xml -i`  
  
**Data Specs**  
`{"host":"127.0.0.1","port":"3306","service":"mysql"}  
{"host":"127.0.0.10","port":"3306","service":"mysql"}  
...`  
  
**Changelog:** Changelog notes are available at [CHANGELOG.md](https://github.com/x90skysn3k/brutespray/blob/master/CHANGELOG.md).  
  

**You might like these similar tools:**

*   [BruteDum: Brute Force attacks SSH, FTP, Telnet, PostgreSQL, RDP, VNC with Hydra, Medusa and Ncrack](http://bit.ly/2ISotWY)
*   [FTPBruter: A FTP Server Brute forcing tool written in Python 3](http://bit.ly/2IzrGtk)
*   [Blazy - Crack Website Logins in seconds with Bruteforce attacks](http://bit.ly/2owpqYx)
*   [SocialBox: A Bruteforce Attack Framework for Social Networks](http://bit.ly/2NJ6GnQ)
*   [Ncrack: An High-speed Open-source Network cracking tool](http://bit.ly/2BxF3Y8)
*   [Medusa: A Speedy, Parallel And Modular Login Brute-forcing Tool](http://bit.ly/2BbF1U9)

  

**[Download BruteSpray](https://github.com/x90skysn3k/brutespray)**