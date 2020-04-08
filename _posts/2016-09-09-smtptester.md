---
title: 'SMTPTester'
date: 2019-10-17T11:14:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-yT1JEzkSK5g/XaWca40KuHI/AAAAAAAABus/vYtl0RVl2awOirFejlSD16tnoEi0iMIMQCLcBGAsYHQ/s320/273492.png)](https://1.bp.blogspot.com/-yT1JEzkSK5g/XaWca40KuHI/AAAAAAAABus/vYtl0RVl2awOirFejlSD16tnoEi0iMIMQCLcBGAsYHQ/s1600/273492.png)

**SMTPTester - Tool To Check Common Vulnerabilities In SMTP Servers**

SMTPTester is a python3 tool to test SMTP server for 3 common vulnerabilities:

*   Spoofing - The ability to send a mail on behalf of an internal user
*   Relay - Using this SMTP server to send email to other address outside of the organization
*   user [enumeration](https://www.kitploit.com/search/label/Enumeration "enumeration") - using the SMTP VRFY command to check if specific username and\\or email address exist within the organization.

[](https://www.blogger.com/u/1/null)  
**How to use it**  
First, install the needed dependencies:

```
pip install -r requirments.txt
```

Second, run the tool with the needed flags:

```
python SMTPTester.py --tester [tester email] --targets [SMTP IP or file containing multiple IPs]
```

  
**Options to consider**

*   \-i\\--internal
    *   testing only for mail spoofing
*   \-e\\--external
    *   only [testing](https://www.kitploit.com/search/label/Testing "testing") for mail relay
*   \-v\\--vrfy
    *   only perform user enumeration the tool will perform both internal and external when no specific test type is specified, and will append the output to a log file on the same folder as the SMTPTester.py file.

  
**Issues, bugs and other code-issues**  
Yeah, I know, this code isn't the best. I'm fine with it as I'm not a developer and this is part of my learning process. If there is an option to do some of it better, please, let me know.  
_Not how many, but where._  
v0.1  
  

**[Download SMTPTester](https://github.com/xFreed0m/SMTPTester "Download SMTPTester")**

**Regards**

**Kang Asu**