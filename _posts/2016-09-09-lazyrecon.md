---
title: 'Lazyrecon'
date: 2019-12-28T23:53:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-2iUMLx3GliY/XfmOeO6K0zI/AAAAAAAARI4/riQSEcR97aQ9r63OAlq97_0mAUBnn5v1QCNcBGAsYHQ/s640/lazyrecon_1_recon.gif)](https://1.bp.blogspot.com/-2iUMLx3GliY/XfmOeO6K0zI/AAAAAAAARI4/riQSEcR97aQ9r63OAlq97_0mAUBnn5v1QCNcBGAsYHQ/s1600/lazyrecon_1_recon.gif)

**Lazyrecon - Script To Automate Your Reconnaissance Process In An Organized Fashion**

  

  
LazyRecon is a script written in Bash, it is intended to automate some tedious tasks of [reconnaissance](https://www.kitploit.com/search/label/Reconnaissance "reconnaissance") and information gathering. This tool allows you to gather some information that should help you identify what to do next and where to look.  
  
**Usage**  
`./lazyrecon.sh -d [target.com](http://target.com/)`  
  
**Main Features**

*    Create a dated folder with recon notes
*    Grab [subdomains](https://www.kitploit.com/search/label/Subdomains "subdomains") using:  
    ```
    * Sublist3r, certspotter and cert.sh  
    * Dns [bruteforcing](https://www.kitploit.com/search/label/Bruteforcing "bruteforcing") using massdns
    ```
*    Find any CNAME records pointing to unused cloud services like aws
*    Probe for live hosts over ports 80/443
*    Grab a screenshots of responsive hosts
*    Scrape wayback for data:  
    ```
    * Extract javascript files  
    * Build custom parameter wordlist, ready to be loaded later into Burp intruder or any other tool  
    * Extract any urls with .jsp, .php or .aspx and store them for further inspection
    ```
*    Perform nmap on specific ports
*    Get dns information about every subdomain
*    Perform dirsearch for all subdomains
*    Generate a HTML report with output from the tools above
*    Improved reporting and less output while doing the work
*    Dark mode for html reports

  
**New features**

*   Directory search module is now MULTITHREADED (up to 10 subdomains scanned at a time)
*   Enhanced html reports with the ability to search for strings, endpoints, reponse sizes or status codes

  
**DEMO**  

[![](https://1.bp.blogspot.com/-Mt-1d8nArE8/XfmOgb7f0PI/AAAAAAAARI8/1bws2rvnuwAN2SF5Rtg7lee_SkxDeg-TwCNcBGAsYHQ/s640/lazyrecon_2_report.gif)](https://1.bp.blogspot.com/-Mt-1d8nArE8/XfmOgb7f0PI/AAAAAAAARI8/1bws2rvnuwAN2SF5Rtg7lee_SkxDeg-TwCNcBGAsYHQ/s1600/lazyrecon_2_report.gif)

  

[![](https://1.bp.blogspot.com/-2iUMLx3GliY/XfmOeO6K0zI/AAAAAAAARI4/riQSEcR97aQ9r63OAlq97_0mAUBnn5v1QCNcBGAsYHQ/s640/lazyrecon_1_recon.gif)](https://1.bp.blogspot.com/-2iUMLx3GliY/XfmOeO6K0zI/AAAAAAAARI4/riQSEcR97aQ9r63OAlq97_0mAUBnn5v1QCNcBGAsYHQ/s1600/lazyrecon_1_recon.gif)

  
**Installation & Requirements**

*   Download the install script from [https://github.com/nahamsec/bbht](https://github.com/nahamsec/bbht "https://github.com/nahamsec/bbht").
*   Go version 1.10 or later.

  
**System Requirements**

*   Recommended to run on vps with 1VCPU and 2GB ram.

  
**Authors and Thanks**  
This script makes use of tools developped by the following people

*   [Tom Hudson - Tomonomnom](https://github.com/tomnomnom "Tom Hudson - Tomonomnom")
*   [Ahmed Aboul-Ela - Aboul3la](https://github.com/aboul3la "Ahmed Aboul-Ela - Aboul3la")
*   [B. Blechschmidt - Blechschmidt](https://github.com/blechschmidt "B. Blechschmidt - Blechschmidt")
*   [Thomas D. - Maaaaz](https://github.com/maaaaz "Thomas D. - Maaaaz")
*   [Daniel Miessler - Danielmiessler](https://github.com/danielmiessler "Daniel Miessler - Danielmiessler")

  
**TO DO**

*   Report only mode to generate reports for old dirsearch data
*   SubDomain exclusion

**Warning:** This code was originally created for personal use, it generates a substantial amount of traffic, please use with caution.  
  

**[Download Lazyrecon](http://libittarc.com/UOx "Download Lazyrecon")**

**Regards**

**Kang Asu**