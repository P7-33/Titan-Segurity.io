---
title: 'Asset Discover'
date: 2019-11-25T22:39:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/--Mopws1I6j4/Xct8HFPO_XI/AAAAAAAAQzo/yivtQtzTV7c2z2XvItS3aAnM-U-URwEBACNcBGAsYHQ/s640/BurpSuite-Asset_Discover_2_Asset_Discovery_Burp_Extension.jpeg)](https://1.bp.blogspot.com/--Mopws1I6j4/Xct8HFPO_XI/AAAAAAAAQzo/yivtQtzTV7c2z2XvItS3aAnM-U-URwEBACNcBGAsYHQ/s1600/BurpSuite-Asset_Discover_2_Asset_Discovery_Burp_Extension.jpeg)

**Asset Discover - Burp Suite Extension To Discover Assets From HTTP Response**

  

  
Burp Suite extension to [discover](https://www.kitploit.com/search/label/Discover "discover") assets from HTTP response using passive scanning. Refer our blog [Asset ](https://redhuntlabs.com/blog/asset-discovery-burp-extension.html "Asset ")[Discovery](https://www.kitploit.com/search/label/Discovery "Discovery") using [Burp](https://www.kitploit.com/search/label/Burp "Burp") Suite for more details.  
The extension is now part of the BApp store and can be installed directly from the Burp Suite. [https://portswigger.net/bappstore/d927f0065171485981d6eb49a860fc3e](https://portswigger.net/bappstore/d927f0065171485981d6eb49a860fc3e "https://portswigger.net/bappstore/d927f0065171485981d6eb49a860fc3e")

[](https://www.blogger.com/u/1/null)  
**Description**  
Passively parses HTTP response of the URLs **in scope** and identifies different type assets such as **domain, subdomain, IP, S3 bucket** etc. and lists them as informational issues.  
  
**Setup**

*   Setup the python environment by providing the [jython.jar](https://www.jython.org/downloads.html "jython.jar") file in the 'Options' tab under 'Extender' in Burp Suite.
*   Download the [extension](https://github.com/redhuntlabs/BurpSuite-Asset_Discover/archive/master.zip "extension").
*   In the 'Extensions' tab under 'Extender', select 'Add'.
*   Change the extension type to 'Python'.
*   Provide the path of the file ‘Asset\_Discover.py’ and click on 'Next'.

  

[![](https://1.bp.blogspot.com/-pNw4fWiOmK0/Xct8Tds_zFI/AAAAAAAAQzw/PGDCQa4HdDA-Ao1gYB_0UN84MRn3qylswCNcBGAsYHQ/s640/BurpSuite-Asset_Discover_3_Add%252520Extension.jpeg)](https://1.bp.blogspot.com/-pNw4fWiOmK0/Xct8Tds_zFI/AAAAAAAAQzw/PGDCQa4HdDA-Ao1gYB_0UN84MRn3qylswCNcBGAsYHQ/s1600/BurpSuite-Asset_Discover_3_Add%252520Extension.jpeg)

  

[![](https://1.bp.blogspot.com/-5F-Bgv7gG4o/Xct8TbRIURI/AAAAAAAAQzs/LUrSTtVgJgoqLRuav0J7VlP9t11IPqgOQCNcBGAsYHQ/s640/BurpSuite-Asset_Discover_4_Add%252520URL%252520to%252520scope.jpeg)](https://1.bp.blogspot.com/-5F-Bgv7gG4o/Xct8TbRIURI/AAAAAAAAQzs/LUrSTtVgJgoqLRuav0J7VlP9t11IPqgOQCNcBGAsYHQ/s1600/BurpSuite-Asset_Discover_4_Add%252520URL%252520to%252520scope.jpeg)

  
**Usage**

*   Add a URL to the 'Scope' under the 'Target' tab. The extension will start identifying assets through passive scan.

  

[![](https://1.bp.blogspot.com/-Q7UO3mV1Pig/Xct8bZZPqdI/AAAAAAAAQz4/LafrUgXE9Mg9hkmKmWyjPHYSuOx71fIggCNcBGAsYHQ/s640/BurpSuite-Asset_Discover_5_Asset%252520Discovery%2525201.jpeg)](https://1.bp.blogspot.com/-Q7UO3mV1Pig/Xct8bZZPqdI/AAAAAAAAQz4/LafrUgXE9Mg9hkmKmWyjPHYSuOx71fIggCNcBGAsYHQ/s1600/BurpSuite-Asset_Discover_5_Asset%252520Discovery%2525201.jpeg)

  

[![](https://1.bp.blogspot.com/-lzLZ6pU2Kb8/Xct8bVnUCaI/AAAAAAAAQz8/p8QQHTVEB7s0-PkcWtmedba2vzJaSi_ngCNcBGAsYHQ/s640/BurpSuite-Asset_Discover_6_Asset%252520Discovery%2525202.jpeg)](https://1.bp.blogspot.com/-lzLZ6pU2Kb8/Xct8bVnUCaI/AAAAAAAAQz8/p8QQHTVEB7s0-PkcWtmedba2vzJaSi_ngCNcBGAsYHQ/s1600/BurpSuite-Asset_Discover_6_Asset%252520Discovery%2525202.jpeg)

  
**Requirements**

*   [Jython 2.7.0](https://www.jython.org/downloads.html "Jython 2.7.0")
*   [Burp Suite Pro v2.1](https://portswigger.net/burp "Burp Suite Pro v2.1")

  
**Code Credits**  
A large portion of the base code has been taken from the following sources:

*   [OpenSecurityResearch CustomPassiveScanner](https://github.com/OpenSecurityResearch/CustomPassiveScanner "OpenSecurityResearch CustomPassiveScanner")
*   [PortSwigger example-scanner-checks](https://github.com/PortSwigger/example-scanner-checks "PortSwigger example-scanner-checks")

  

**[Download BurpSuite-Asset\_Discover](http://hopigrarn.com/3lhl "Download BurpSuite-Asset_Discover")**

**Regards**

**Kang Asu**