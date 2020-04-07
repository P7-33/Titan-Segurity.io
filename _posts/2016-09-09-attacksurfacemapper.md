---
title: 'AttackSurfaceMapper'
date: 2020-01-09T12:41:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-e8LXMbivcl4/XgAjZmRclOI/AAAAAAAARME/UPYAld6x9UgDBJavCH7GZ1zx2AFYFBMWACNcBGAsYHQ/s640/AttackSurfaceMapper_4.png)](https://1.bp.blogspot.com/-e8LXMbivcl4/XgAjZmRclOI/AAAAAAAARME/UPYAld6x9UgDBJavCH7GZ1zx2AFYFBMWACNcBGAsYHQ/s1600/AttackSurfaceMapper_4.png)

**AttackSurfaceMapper - A Tool That Aims To Automate The Reconnaissance Process**

  

  
Attack Surface Mapper is a [reconnaissance](https://www.kitploit.com/search/label/Reconnaissance "reconnaissance") tool that uses a mixture of open source intellgence and active techniques to expand the attack surface of your target. You feed in a mixture of one or more domains, subdomains and IP addresses and it uses numerous techniques to find more targets. It enumerates subdomains with [bruteforcing](https://www.kitploit.com/search/label/Bruteforcing "bruteforcing") and passive lookups, Other IPs of the same network block owner, IPs that have multiple domain names pointing to them and so on.  
Once the target list is fully expanded it performs passive reconnaissance on them, taking screenshots of websites, generating visual maps, looking up [credentials](https://www.kitploit.com/search/label/Credentials "credentials") in public breaches, passive [port scanning](https://www.kitploit.com/search/label/Port%20Scanning "port scanning") with Shodan and scraping employees from LinkedIn.  
  
  
**Demo**

  
**Setup**  
As this is a Python based tool, it should theoretically run on Linux, ChromeOS ([Developer Mode](https://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/generic "Developer Mode")), macOS and Windows.  
\[1\] Download AttackSurfaceMapper

```
$ git clone [https://github.com/superhedgy/AttackSurfaceMapper](https://github.com/superhedgy/AttackSurfaceMapper)
```

\[2\] Install Python dependencies

```
$ cd AttackSurfaceMapper  
$ python3 -m pip install --no-cache-dir -r requirements.txt
```

\[3\] Add optional API keys to enable more data gathering  
Register and obtain an API key from:

*   [VirusTotal](https://www.virustotal.com/gui/join-us "VirusTotal")
*   [ShodanIO](https://account.shodan.io/register "ShodanIO")
*   [HunterIO](https://hunter.io/users/sign_up "HunterIO")
*   [WeLeakInfo](https://weleakinfo.com/register "WeLeakInfo")
*   [LinkedIn](https://www.linkedin.com/start/join "LinkedIn")
*   [GrayHatWarfare](https://buckets.grayhatwarfare.com/register "GrayHatWarfare")

Edit and enter the keys in keylist file

```
$ nano keylist.asm
```

  
**Example run command**

```
$ python3 asm.py -t [your.site.com](http://your.site.com/) -ln -w resources/top100_sublist.txt -o demo_run
```

  
**Optional Parameters**  
Additional optional parameters can also be set to choose to include active reconnaissance modules in addition to the default passive modules.

```
|<------ AttackSurfaceMapper - Help Page ------>|  
  
positional arguments:  
  targets               Sets the path of the target IPs file.  
  
optional arguments:  
  -h, --help            show this help message and exit  
  -f FORMAT, --format FORMAT  
                        Choose between CSV and TXT output file formats.  
  -o OUTPUT, --output OUTPUT  
                        Sets the path of the output file.  
  -sc, --screen-capture  
                        Capture a screen shot of any associated Web Applications.  
  -sth, --stealth       Passive mode allows reconaissaince using [OSINT techniques](https://www.kitploit.com/search/label/OSINT%20techniques "OSINT techniques") only.  
  -t TARGET, --target TARGET  
                        Set a single target IP.  
  -V, --version         Displays the current version.  
  -w WORDLIST, --wordlist WORDLIST  
                        Specify a lis   t of subdomains.  
  -sw SUBWORDLIST, --subwordlist SUBWORDLIST  
                        Specify a list of child subdomains.  
  -e, --expand          Expand the target list recursively.  
  -ln, --linkedinner    Extracts emails and employees details from linkedin.  
  -v, --verbose         Verbose ouput in the terminal window.  
  
Authors: Andreas Georgiou (@superhedgy)  
  Jacob Wilkin (@greenwolf)
```

  
**Authors**

*   [Andreas Georgiou](https://twitter.com/superhedgy "Andreas Georgiou")
*   [Jacob Wilkin](https://github.com/Greenwolf "Jacob Wilkin")

  

**[Download AttackSurfaceMapper](http://libittarc.com/3FWM "Download AttackSurfaceMapper")**

**Regards**

**Kang Asu**