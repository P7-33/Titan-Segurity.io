---
title: 'Medusa: A Speedy, Parallel And Modular Login Brute-forcing Tool'
date: 2019-10-10T16:36:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-JbQbMLTTMj4/XZ9J7MJCXTI/AAAAAAAAO4I/jPVJeEckPHgvgJJGVfLgTRLYzK2n8tbQACLcBGAsYHQ/s1600/Medusa.png)](https://1.bp.blogspot.com/-JbQbMLTTMj4/XZ9J7MJCXTI/AAAAAAAAO4I/jPVJeEckPHgvgJJGVfLgTRLYzK2n8tbQACLcBGAsYHQ/s1600/Medusa.png)

**About Medusa**  
   Medusa is a speedy, parallel, and modular, login brute-forcer. The goal is to support as many services which allow remote authentication as possible. The author considers following items as some of the key features of this application:  
  
   Thread-based parallel testing. Brute-force testing can be performed against multiple hosts, users or passwords concurrently.  
  
   Flexible user input. Target information (host/user/password) can be specified in a variety of ways. For example, each item can be either a single entry or a file containing multiple entries. Additionally, a combination file format allows the user to refine their target listing.  
  
   Modular design. Each service module exists as an independent `.mod` file. This means that no modifications are necessary to the core application in order to extend the supported list of services for brute-forcing.  
  
   Multiple protocols supported. Many services are currently supported (e.g. SMB, HTTP, MS-SQL, POP3, RDP, SSHv2, among others).  
  
   See [doc/medusa.htm](https://github.com/jmk-foofus/medusa/blob/master/doc/medusa.html)l for Medusa documentation. For additional information:  

*   [Medusa | Foofus.Net](http://foofus.net/?page_id=51)
*   [Medusa Parallel Network Login Auditor](http://foofus.net/goons/jmk/medusa/medusa.html)

  
**Building on macOS**  
  
`#getting the source  
git clone https://github.com/jmk-foofus/medusa  
cd medusa  
  
#macOS dependencies  
brew install freerdp  
$ export FREERDP2_CFLAGS='-I/usr/local/include'  
$ export FREERDP2_LIBS='-I/usr/local/lib/freerdp'  
  
#building  
./configure  
make  
  
#executing  
  
./src/medusa  
`**Medusa's Installation**  
   Medusa is already installed on Kali Linux, Parrot Security OS, BlackArch and any other Linux distros based for security pentesting purposes.  
  
   For Debian-based distro users, open your Terminal and enter this command:  
`sudo apt install medusa`  
   For Arch Linux-based distro users, enter this command: `sudo pacman -S medusa`  
  
**About the author:**  

*   Email: [jmk@foofus.net](mailto:jmk@foofus.net)
*   Github: [jmk-foofus](https://github.com/jmk-foofus)
*   Website: [Foofus.net](http://foofus.net/)

  

**You might like these similar tools:**

*   [BruteDum: Brute Force attacks SSH, FTP, Telnet, PostgreSQL, RDP, VNC with Hydra, Medusa and Ncrack](http://bit.ly/2ISotWY)
*   [FTPBruter: A FTP Server Brute forcing tool written in Python 3](http://bit.ly/2IzrGtk)
*   [Blazy - Crack Website Logins in seconds with Bruteforce attacks](http://bit.ly/2owpqYx)
*   [SocialBox: A Bruteforce Attack Framework for Social Networks](http://bit.ly/2NJ6GnQ)
*   [Ncrack: An High-speed Open-source Network cracking tool](http://bit.ly/2BxF3Y8)
*   [BruteSpray: A Brute-forcer From Nmap Output And Automatically Attempts Default Creds On Found Services](http://bit.ly/2q0kXl3)

**[Download Medusa](https://github.com/jmk-foofus/medusa)**