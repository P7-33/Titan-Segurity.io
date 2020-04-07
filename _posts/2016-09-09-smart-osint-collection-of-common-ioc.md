---
title: 'Smart OSINT Collection of Common IOC Types'
date: 2020-01-31T11:29:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-1Y-nt2tWUTI/XjP0a4e9k1I/AAAAAAAAGmw/xHdZlzNAGJElVZDUlzSvreCYk2PZcBKdACLcBGAsYHQ/s1600/Mimir%2BOSINT%2BCollections.png)](https://1.bp.blogspot.com/-1Y-nt2tWUTI/XjP0a4e9k1I/AAAAAAAAGmw/xHdZlzNAGJElVZDUlzSvreCYk2PZcBKdACLcBGAsYHQ/s1600/Mimir%2BOSINT%2BCollections.png)

  

Smart OSINT Collection of Common IOC (Indicator of compromise) Types
--------------------------------------------------------------------

  
This application is designed to assist security analysts and researchers with the collection and assessment of common IOC types. Accepted IOCs currently include IP addresses, domain names, URLs, and file hashes.  
  
The title of this project is named after Mimir, a figure in Norse mythology renowned for his knowledge and wisdom. This application aims to provide you knowledge into IOCs and then some added "wisdom" by calculating risk scores per IOC, assigning a common malware family name to hash lookups based off of reports from VirusTotal and OPSWAT, and leveraging machine learning tools to determine if an IP, URL, or domain is likely to be malicious.  
  

### Base Collection

For network based IOCs, Mimir gathers basic information including:  

*   Whois
*   ASN
*   Geolocation
*   Reverse DNS
*   Passive DNS
*   Collection Sources

  
Some of these sources will require an API key, and occasionally only by getting a paid account and tried to limit reliance on paid services as much as possible.  

*   PassiveTotal
*   VirusTotal
*   DomainTools
*   OPSWAT
*   Google SafeBrowsing
*   Shodan
*   PulseDive
*   CSIRTG
*   URLscan
*   HpHosts
*   Blacklist checks
*   Spam blacklist checks
*   Risk Scoring

  
The risk scoring works best when Mimir can gather a decent amount of data points for an IOC; pDNS, well populated url/domain results (communicating samples, associated samples, recent scan data, etc.) and also takes into account the ML malicious-ness prediction result.  
  

### Machine Learning Predictions

The machine learning prediction results come from the CSIRT Gadgets projects csirtg-domainsml-py, csirtg-ipsml-py, csirtg-urlsml-py.  
  

### Output

Mimir offers results output in various options including local file reports or exporting the results to an external service.  
  
**stdout (console output)**  
normalizes result data, printed with headers and subheaders per module  
  
**JSON file**  
beautified output to local file  
  
**Excel**  
uses multiple sheets per IOC type  
  
**MISP**  
commit new indicators  
  
**ThreatConnect**  
commit new indicators with confidence and threat ratings (optionally assign tags, a description, and a TLP setting)  
  
[Download Smart OSINT Collection](https://github.com/deadbits/mimir)

  
  
from Hackers Online Club (HOC) https://ift.tt/37KAW7U