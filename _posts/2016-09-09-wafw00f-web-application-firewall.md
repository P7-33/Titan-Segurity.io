---
title: 'wafw00f: The Web Application Firewall Fingerprinting Tool'
date: 2020-01-07T12:43:00+01:00
draft: false
---

**How does wafw00f work?**  
   To do its magic, WAFW00F does the following steps:  

*   Sends a normal HTTP request and analyses the response; this identifies a number of WAF solutions.
*   If that is not successful, wafw00f sends a number of (potentially malicious) HTTP requests and uses simple logic to deduce which WAF it is.
*   If that is also not successful, wafw00f analyses the responses previously returned and uses another simple algorithm to guess if a WAF or security solution is actively responding to wafw00f's attacks.

  
   For further details, check out the source code on [EnableSecurity's main repository](https://github.com/EnableSecurity/wafw00f).  
  
**What does it detect?** WAFW00F can detect a number of firewalls, a list of which is as below:  
**wafw00f's installation**  
   If you're using Debian-based distro, enter this commands to install wafw00f: `sudo apt update && sudo apt install wafw00f`  
  
   But if you're using another Linux distro, enter these commands to install wafw00f:  
  
**How to use wafw00f?**  
   The basic usage is to pass an URL as an argument. Example:  

[![](https://1.bp.blogspot.com/-9UZc3ASDHt4/XhRs9F5A5CI/AAAAAAAAO88/neuZDLKjQnIOW_RiAaslqKV4LOdrj0eQQCLcBGAsYHQ/s1600/wafw00f.png)](https://1.bp.blogspot.com/-9UZc3ASDHt4/XhRs9F5A5CI/AAAAAAAAO88/neuZDLKjQnIOW_RiAaslqKV4LOdrj0eQQCLcBGAsYHQ/s1600/wafw00f.png)

  
**Final Words to you**  
   Questions? Pull up an [issue on GitHub Issue Tracker](https://github.com/enablesecurity/wafw00f/issues/new) or [contact to EnableSecurity](mailto:sandro@enablesecurity.com).  
   Pull requests, ideas and issues are highly welcome. If you wish to see how WAFW00F is being developed, check out the [development board](https://github.com/enablesecurity/wafw00f/projects/1).  
  
   Some useful links:  

*   [Documentation/Wiki](https://github.com/enablesecurity/wafw00f/wiki/)
*   [Pypi Package Repository](https://pypi.org/project/wafw00f)

  
   Presently being developed and maintained by:  

*   Sandro Gauci ([@SandroGauci](https://twitter.com/sandrogauci))
*   Pinaki Mondal ([@0xInfection](https://twitter.com/0xinfection))

  

**[Download wafw00f](https://github.com/EnableSecurity/wafw00f)**