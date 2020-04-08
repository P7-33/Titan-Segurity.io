---
title: 'Penta- Open Source All-in-one CLI To Automate Pentesting'
date: 2019-10-10T21:11:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-8MrR6tx-pIk/XZ9-ag3pCtI/AAAAAAAAGc0/z4cVcINZZ2UWUpz2qbH-svbMn9FMN47kgCLcBGAsYHQ/s1600/Penta.png)](https://1.bp.blogspot.com/-8MrR6tx-pIk/XZ9-ag3pCtI/AAAAAAAAGc0/z4cVcINZZ2UWUpz2qbH-svbMn9FMN47kgCLcBGAsYHQ/s1600/Penta.png)

  

---

Penta (PENTest + Automation tool) is Pentest automation tool using Python3.
---------------------------------------------------------------------------

### Installation

**Install requirements**  
penta requires the following packages.  

*   Python3.7
*   pipenv

  
Resolve python package dependency.  
  
$ pipenv install  
  
If you dislike pipenv..  
  
$ pip install -r requirements.txt  
  

### Usage

$ pipenv run start  
  
If you dislike pipenv...  
  
$ python penta/penta.py  
  
**Usage: List options**  
  
$ pipenv run start -h  
  
usage: penta.py \[-h\] \[-target TARGET\] \[-ports PORTS\] \[-proxy PROXY\]  
  
Penta is Pentest automation tool  
  
**optional arguments:**  

*     -h, --help      show this help message and exit
*     -target TARGET  Specify target IP / domain
*     -ports PORTS    Please, specify the target port(s) separated by comma.
*                     Default: 21,22,25,80,110,443,8080
*     -proxy PROXY    Proxy\[IP:PORT\]

  
**Usage: Main menu**  
  
\[ \] === MENU LIST =================================  
\[0\] EXIT  
\[1\] Port scanning Default: 21,22,25,80,110,443,8080  
\[2\] Nmap & vuln scanning  
\[3\] Check HTTP option methods  
\[4\] Grab DNS server info  
\[5\] Shodan host search  
\[6\] FTP connect with anonymous  
\[7\] SSH connect with Brute Force  
\[99\] Change target host  
  
**1\. Port scanning**  
To check ports for a target. Log output supported.  
  
**2\. Nmap**  
To check ports by additional means using nmap  
  
**3\. Check HTTP option methods**  
To check the methods (e.g. GET,POST) for a target.  
  
**4\. Grab DNS server info**  
To show the info about DNS server.  
  
Shodan host search To collect host service info from Shodan.  
Request [Shodan API key](https://developer.shodan.io/) to enable the feature.  
  
FTP connect with anonymous To check if it has anonymous access activated in port 21. FTP users can authenticate themselves using the plain text sign-in protocol (Typically username and password format), but they can connect anonymously if the server is configured to allow it.  
  
Anyone can log in to the server if the administrator has allowed an FTP connection with an anonymous login.  
  
SSH connect with Brute Force To check ssh connection to scan with Brute Force. Dictionary data is in data/dict.  
  
[Download Now](https://github.com/takuzoo3868/penta)

  
  
from Hackers Online Club (HOC) https://ift.tt/312wxsW