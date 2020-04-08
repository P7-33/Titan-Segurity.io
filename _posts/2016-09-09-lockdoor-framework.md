---
title: 'Lockdoor Framework'
date: 2019-10-14T22:01:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-TXJYwIziXEI/XZkFE67eNcI/AAAAAAAABuQ/RksqhCbZmu4QnRabTu_po_vM1MCZaV8QQCLcBGAsYHQ/s1600/Lockdoor-Framework_1_logo205x250.gif)](https://1.bp.blogspot.com/-TXJYwIziXEI/XZkFE67eNcI/AAAAAAAABuQ/RksqhCbZmu4QnRabTu_po_vM1MCZaV8QQCLcBGAsYHQ/s1600/Lockdoor-Framework_1_logo205x250.gif)

**Lockdoor Framework - A Penetration Testing Framework With Cyber Security Resources**

Lockdoor Framework : A Penetration Testing Framework With Cyber Security Resources.  
  
  
**09/2019 : 1.0Beta**

*   Information Gathring Tools (21)
*   Web Hacking Tools(15)
*   Reverse Engineering Tools (15)
*   Exploitation Tools (6)
*   Pentesting & Security Assessment Findings Report Templates (6)
*   Password Attack Tools (4)
*   Shell Tools + Blackarch's Webshells Collection (4)
*   Walk Throughs & Pentest Processing Helpers (3)
*   Encryption/Decryption Tools (2)
*   Social Engineering tools (1)
*   All you need as [Privilege Escalation](https://www.kitploit.com/search/label/Privilege%20Escalation "Privilege Escalation") scripts and exploits
*   Working on Kali,Ubuntu,Arch,Fedora,Opensuse and Windows (Cygwin)

[](https://www.blogger.com/u/1/null)  

[![](https://1.bp.blogspot.com/-JPmd-p1zG5g/XZLPVgdnGBI/AAAAAAAAQfM/tkbGlA9_ueIy_QqDd4W-C_6odKaq14gUgCNcBGAsYHQ/s640/Lockdoor-Framework_13_test.gif)](https://1.bp.blogspot.com/-JPmd-p1zG5g/XZLPVgdnGBI/AAAAAAAAQfM/tkbGlA9_ueIy_QqDd4W-C_6odKaq14gUgCNcBGAsYHQ/s1600/Lockdoor-Framework_13_test.gif)

  
  
**09/2019 : 0.6**

*   Information Gathring tools (13)
*   Web Hacking Tools (9)
*   Working on Kali,Ubuntu,Arch,Fedora,Opensuse and Windows (Cygwin)
*   Some bugs That I'm fixing with time so don't worry about that.

  

[![](https://1.bp.blogspot.com/-HLeYSrvF-hU/XZLPb0hzR_I/AAAAAAAAQfQ/DEsBsCcrUe86oWpshRVfOduBYVoN3zuDACNcBGAsYHQ/s640/Lockdoor-Framework_14_kali.gif)](https://1.bp.blogspot.com/-HLeYSrvF-hU/XZLPb0hzR_I/AAAAAAAAQfQ/DEsBsCcrUe86oWpshRVfOduBYVoN3zuDACNcBGAsYHQ/s1600/Lockdoor-Framework_14_kali.gif)

  
  
**Check the Wiki Pages to know more about the tool**  
  

*   The Wiki pages :

*   [Lockdoor Wiki page Home](https://github.com/SofianeHamlaoui/Lockdoor-Framework/wiki "Lockdoor Wiki page Home")
*   [Lockdoor Demos](https://github.com/SofianeHamlaoui/Lockdoor-Framework/wiki/Demos "Lockdoor Demos")
*   [Lockdoor Screenshots](https://github.com/SofianeHamlaoui/Lockdoor-Framework/wiki/Screenshots "Lockdoor Screenshots") 

  
  
  
**Overview**  
_LockDoor_ is a Framework aimed at **helping penetration testers, bug bounty hunters And cyber security engineers**. This tool is designed for Debian/Ubuntu/ArchLinux based distributions to create a similar and familiar distribution for Penetration Testing. But containing the favorite and the most used tools by Pentesters. As pentesters, most of us has his personal ' /pentest/ ' directory so this Framework is helping you to build a perfect one. With all of that ! It automates the Pentesting process to help you do the job more quickly and easily.  
  
  
**Features**  
Added value : (what makes it different from other frameworks).  
  
**Pentesting Tools Selection:**

*   **Tools ?**: **Lockdoor** doesn't contain all pentesting tools (Added value) , let's be honest ! Who ever used all the Tools you find on all those Penetration Testing distributions ? Lockdoor contains only the favorite (Added value) and the most used toolsby Pentesters (Added value).
*   **what Tools ?**: the tools contains **Lockdoor** are a collection from the best tools (Added value) on Kali,Parrot Os and BlackArch. Also some private tools (Added value) from some other hacking teams (Added value) like InurlBr, iran-cyber. Without forgeting some cool and amazing tools I found on Github made by some perfect human beigns (Added value).
*   **Easy customization**: Easily add/remove tools. (Added value)
*   **Installation**: You can install the tool automatically using the installer.sh , Manually or on Docker \[COMING SOON\]

  
**Resources and cheatsheets: (Added value)**

*   **Resources**: That's what makes **Lockdoor** Added value, Lockdoor Doesn't contain only tools ! Pentesing and Security Assessment Findings Reports templates (Added value) , Pentesting walkthrough examples and tempales (Added value) and more.
*   **Cheatsheets**: Everyone can forget something on processing or a tool use, or even some trciks. Here comes the Cheatsheets (Added value) role ! there are cheatsheets about everything, every tool on the framework and any enumeration,exploitation and post-exploitation techniques.

  
**Installation:**

*   Automatically  
    
    ```
    git clone [https://github.com/SofianeHamlaoui/Lockdoor-Framework.git](https://github.com/SofianeHamlaoui/Lockdoor-Framework.git) && cd Lockdoor-Framework  
    chmod +x ./install.sh  
    ./install.sh
    ```
    
*   Manually  
    *   Installing requirments  
        
        ```
        python python-pip python-requests python2 python2-pip gcc ruby php git wget bc curl netcat subversion jre-openjdk make automake gcc linux-headers gzip
        ```
        
    *   Installing Go  
        
        ```
        wget [https://dl.google.com/go/go1.13.linux-amd64.tar.gz](https://dl.google.com/go/go1.13.linux-amd64.tar.gz)  
        tar -xvf go1.13.linux-amd64.tar.gz  
        mv go /usr/local  
        export GOROOT=/usr/local/go  
        export PATH=$GOPATH/bin:$GOROOT/bin:$PATH  
        rm go1.13.linux-amd64.tar.gz
        ```
        
    *   Installing Lockdoor  
        
        ```
        # Clonnig  
        git clone [https://github.com/SofianeHamlaoui/Lockdoor-Framework.git](https://github.com/SofianeHamlaoui/Lockdoor-Framework.git) && cd Lockdoor-Framework  
        # Create the config file  
        # INSTALLDIR = where you want to install Lockdoor (Ex : /opt/sofiane/pentest)  
        echo "Location:"$installdir > $HOME"/.config/lockdoor/lockdoor.conf"  
        # Moving the resources folder  
        mv ToolsResources/* INSTALLDIR  
        # Installing Lockdoor from PyPi  
        pip3 install lockdoor
        ```
        
*    Docker Installation  
    COMING SOON

  
**Lockdoor Tools contents:**  
  
****Information Gathering**:**

*    Tools:  
    *   dirsearch : A Web path scanner
    *   brut3k1t : security-oriented bruteforce framework
    *   gobuster : DNS and VHost busting tool written in Go
    *   Enyx : an SNMP IPv6 Enumeration Tool
    *   Goohak : Launchs Google Hacking Queries Against A Target Domain
    *   Nasnum : The NAS Enumerator
    *   Sublist3r : Fast subdomains enumeration tool for penetration testers
    *   wafw00f : identify and fingerprint Web Application Firewall
    *   Photon : ncredibly fast crawler designed for OSINT.
    *   Raccoon : offensive security tool for reconnaissance and vulnerability scanning
    *   DnsRecon : DNS Enumeration Script
    *   Nmap : The famous security Scanner, Port Scanner, & Network Exploration Tool
    *   sherlock : Find usernames across social networks
    *   snmpwn : An SNMPv3 User Enumerator and Attack tool
    *   Striker : an offensive information and vulnerability scanner.
    *   theHarvester : E-mails, subdomains and names Harvester
    *   URLextractor : Information gathering & website reconnaissance
    *   denumerator.py : Enumerates list of subdomains
    *   other : other Information gathering,recon and Enumeration scripts I collected somewhere.
*    Frameworks:  
    *   ReconDog : Reconnaissance Swiss Army Knife
    *   RED\_HAWK : All in one tool for Information Gathering, [Vulnerability Scanning](https://www.kitploit.com/search/label/Vulnerability%20Scanning "Vulnerability Scanning") and Crawling
    *   Dracnmap : Info Gathering Framework

  
****Web Hacking**:**

*    Tools:
    *   Spaghetti : Spaghetti - Web Application Security Scanner
    *   CMSmap : CMS scanner
    *   BruteXSS : BruteXSS is a tool to find XSS vulnerabilities in web application
    *   J-dorker : Website List grabber from Bing
    *   droopescan : scanner , identify , CMSs , Drupal , Silverstripe.
    *   Optiva : Web Application Scanne
    *   V3n0M : Pentesting scanner in Python3.6 for SQLi/XSS/LFI/RFI and other Vulns
    *   AtScan : Advanced dork Search & Mass Exploit Scanner
    *   WPSeku : Wordpress Security Scanner
    *   Wpscan : A simple Wordpress scanner written in python
    *   XSStrike : Most advanced XSS scanner.
    *   Sqlmap : automatic SQL injection and database takeover tool
    *   WhatWeb : the Next generation web scanner
    *   joomscan : Joomla [Vulnerability Scanner](https://www.kitploit.com/search/label/Vulnerability%20Scanner "Vulnerability Scanner") Project
*    Frameworks:
    *   Dzjecter : Server checking Tool

  
****Privilege Escalation**:**

*    Tools:
    *    Linux:
        *    Scripts:
            *   linux\_checksec.sh
            *   linux\_enum.sh
            *   linux\_gather\_files.sh
            *   linux\_kernel\_exploiter.pl
            *   linux\_privesc.py
            *   linux\_privesc.sh
            *   linux\_security\_test
        *   Linux\_exploits folder
    *    Windows :
        *   windows-privesc-check.py
        *   windows-privesc-check.exe
    *    MySql:
        *   raptor\_udf.c
        *   raptor\_udf2.c

  
****Reverse Engineering**:**

*   Radare2 : unix-like reverse engineering framework
*   VirtusTotal : VirusTotal tools
*   Miasm : Reverse engineering framework
*   Mirror : reverses the bytes of a file
*   DnSpy : .NET debugger and assembly
*   AngrIo : A python framework for analyzing binaries ( Suggested by @Hamz-a )
*   DLLRunner : a smart DLL execution script for malware analysis in sandbox systems.
*   Fuzzy Server : a Program That Uses Pre-Made Spike Scripts to Attack VulnServer.
*   yara : a tool aimed at helping malware researchers toidentify and classify malware samples
*   Spike : a protocol fuzzer creation kit + audits
*   other : other scripts collected somewhere

  
****Exploitation**:**

*   Findsploit : Find exploits in local and online databases instantly
*   Pompem : Exploit and Vulnerability Finder
*   rfix : Python tool that helps RFI exploitation.
*   InUrlBr : Advanced search in search engines
*   Burpsuite : Burp Suite for security testing & scanning.
*   linux-exploit-suggester2 : Next-Generation Linux Kernel Exploit Suggester
*   other : other scripts I collected somewhere.

  
****Shells**:**

*   WebShells : BlackArch's Webshells Collection
*   ShellSum : A defense tool - detect web shells in local directories
*   Weevely : Weaponized web shell
*   python-pty-shells : Python PTY backdoors

  
****Password Attacks**:**

*   crunch : a wordlist generator
*   CeWL : a Custom Word List Generator
*   patator : a multi-purpose brute-forcer, with a modular design and a flexible usage

  
****Encryption - Decryption**:**

*   Codetective : a tool to determine the crypto/encoding algorithm used
*   findmyhash : Python script to crack hashes using online services

  
****Social Engineering**:**

*   scythe : an accounts enumerator

  
**Lockdoor Resources contents:**  
  
****Information Gathering**:**

*   [Cheatsheet\_SMBEnumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/Cheatsheet_SMBEnumeration.txt "Cheatsheet_SMBEnumeration")
*   [configuration\_management](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/configuration_management.md "configuration_management")
*   [dns\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/dns_enumeration.md "dns_enumeration")
*   [file\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/file_enumeration.md "file_enumeration")
*   [http\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/http_enumeration.md "http_enumeration")
*   [information\_gathering\_owasp\_guide](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/information_gathering_owasp_guide.md "information_gathering_owasp_guide")
*   [miniserv\_webmin\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/miniserv_webmin_enumeration.md "miniserv_webmin_enumeration")
*   [ms\_sql\_server\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/ms_sql_server_enumeration.md "ms_sql_server_enumeration")
*   [nfs\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/nfs_enumeration.md "nfs_enumeration")
*   [osint\_recon\_ng](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/osint_recon_ng.md "osint_recon_ng")
*   [passive\_information\_gathering](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/passive_information_gathering.md "passive_information_gathering")
*   [pop3\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/pop3_enumeration.md "pop3_enumeration")
*   [ports\_emumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/ports_emumeration.md "ports_emumeration")
*   [rpc\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/rpc_enumeration.md "rpc_enumeration")
*   [scanning](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/scanning.md "scanning")
*   [smb\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/smb_enumeration.md "smb_enumeration")
*   [smtp\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/smtp_enumeration.md "smtp_enumeration")
*   [snmb\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/snmb_enumeration.md "snmb_enumeration")
*   [vulnerability\_scanning](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/INFO-GATH/CHEATSHEETS/vulnerability_scanning.md "vulnerability_scanning")

  
****Crypto**:**

*   [Crypto101.pdf](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/ENCRYPTION/Crypto101.pdf "Crypto101.pdf")

  
****Exploitation**:**

*   [computer\_network\_exploits](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/computer_network_exploits.md "computer_network_exploits")
*   [file\_inclusion\_vulnerabilities](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/file_inclusion_vulnerabilities.md "file_inclusion_vulnerabilities")
*   [File\_Transfers](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/File_Transfers.md "File_Transfers")
*   [nc\_transfers](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/nc_transfers.txt "nc_transfers")
*   [networking\_pivoting\_and\_tunneling](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/networking_pivoting_and_tunneling.md "networking_pivoting_and_tunneling")
*   [network\_pivoting\_techniques](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/network_pivoting_techniques.md "network_pivoting_techniques")
*   [pivoting](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/pivoting.md "pivoting")
*   [pivoting\_](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/pivoting_.md "pivoting_")
*   [Public Exploits](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/PublicExploits.md "Public Exploits")
*   [reverse\_shell\_with\_msfvenom](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/EXPLOITATION/CHEATSHEETS/reverse_shell_with_msfvenom.md "reverse_shell_with_msfvenom")

  
****Networking**:**

*   [bpf\_syntax](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/NETWORKING/bpf_syntax.md "bpf_syntax")
*   [Cheatsheet\_Networking](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/NETWORKING/Cheatsheet_Networking.txt "Cheatsheet_Networking")
*   [Cheatsheet\_Oracle](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/NETWORKING/Cheatsheet_Oracle.txt "Cheatsheet_Oracle")
*   [networking\_concept](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/NETWORKING/networking_concept "networking_concept")
*   [nmap\_quick\_reference\_guide](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/NETWORKING/nmap_quick_reference_guide.pdf "nmap_quick_reference_guide")
*   [tcpdump](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/NETWORKING/tcpdump.pdf "tcpdump")

  
****Password Attacks**:**

*   [password\_attacks](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PASSWORD/CHEATSHEETS/password_attacks.md "password_attacks")
*   [Some-Links-To-Wordlists](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PASSWORD/CHEATSHEETS/Some-Links-To-Wordlists.txt "Some-Links-To-Wordlists")

  
****Post Exploitation**:**

*   [Cheatsheet\_AVBypass](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/POST-EXPL/CHEATSHEETS/Cheatsheet_AVBypass.txt "Cheatsheet_AVBypass")
*   [Cheatsheet\_BuildReviews](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/POST-EXPL/CHEATSHEETS/Cheatsheet_BuildReviews.txt "Cheatsheet_BuildReviews")
*   [code-execution-reverse-shell-commands](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/POST-EXPL/CHEATSHEETS/code-execution-reverse-shell-commands.txt "code-execution-reverse-shell-commands")
*   [important-linux-serv-files](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/POST-EXPL/CHEATSHEETS/important-linux-serv-files.txt "important-linux-serv-files")

  
****Privilege Escalation**:**

*   [Cheatsheet\_LinuxPrivilegeEsc](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PrivEsc/CHEATSHEETS/Cheatsheet_LinuxPrivilegeEsc.txt "Cheatsheet_LinuxPrivilegeEsc")
*   [linux\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PrivEsc/CHEATSHEETS/linux_enumeration.md "linux_enumeration")
*   [windows\_enumeration](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PrivEsc/CHEATSHEETS/windows_enumeration.md "windows_enumeration")
*   [windows\_priv\_escalation](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PrivEsc/CHEATSHEETS/windows_priv_escalation.md "windows_priv_escalation")
*   [windows\_priv\_escalation\_practical](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/PrivEsc/CHEATSHEETS/windows_priv_escalation_practical.md "windows_priv_escalation_practical")

  
****Pentesting & Security Assessment Findings Report Templates**:**

*   [Demo Company - Security Assessment Findings Report.docx](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REPORT/TEMPLATES/DemoCompany-SecurityAssessmentFindingsReport.docx "Demo Company - Security Assessment Findings Report.docx")
*   [linux-template.md](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REPORT/TEMPLATES/linux-template.md "linux-template.md")
*   [PWKv1-REPORT.doc](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REPORT/TEMPLATES/PWKv1-REPORT.doc "PWKv1-REPORT.doc")
*   [pwkv1\_report.doc](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REPORT/TEMPLATES/pwkv1_report.doc "pwkv1_report.doc")
*   [template-penetration-testing-report-v03.pdf](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REPORT/TEMPLATES/template-penetration-testing-report-v03.pdf "template-penetration-testing-report-v03.pdf")
*   [windows-template.md](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REPORT/TEMPLATES/windows-template.md "windows-template.md")

  
****Reverse Engineering**:**

*   [Buffer\_Overflow\_Exploit](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/Buffer_Overflow_Exploit.md "Buffer_Overflow_Exploit")
*   [buffer\_overflows](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/buffer_overflows.md "buffer_overflows")
*   [gdb\_cheat\_sheet](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/gdb_cheat_sheet.pdf "gdb_cheat_sheet")
*   [r2\_cheatsheet](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/r2_cheatsheet.pdf "r2_cheatsheet")
*   [win32\_buffer\_overflow\_exploitation](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/win32_buffer_overflow_exploitation.md "win32_buffer_overflow_exploitation")
*   [64\_ia\_32\_jmp\_instructions](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/64_ia_32_jmp_instructions.pdf "64_ia_32_jmp_instructions")
*   [course\_notes](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/course_notes.md "course_notes")
*   [debuging](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/debuging.md "debuging")
*   [IntelCodeTable\_x86](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/IntelCodeTable_x86.pdf "IntelCodeTable_x86")
*   [Radare2 cheat sheet](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/Radare2cheatsheet.txt "Radare2 cheat sheet")
*   [x86\_assembly\_x86\_architecture](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/x86_assembly_x86_architecture.pdf "x86_assembly_x86_architecture")
*   [x86\_opcode\_structure\_and\_instruction\_overview](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/REVERSE/CHEATSHEETS/assembly/x86_opcode_structure_and_instruction_overview.png "x86_opcode_structure_and_instruction_overview")

  
****Social Engineering**:**

*   [social\_engineering](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/SOCIAL_ENGINEERING/CHEATSHEETS/social_engineering.md "social_engineering")

  
****Walk Throughs**:**

*   [Cheatsheet\_PenTesting.txt](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WALK/Cheatsheet_PenTesting.txt "Cheatsheet_PenTesting.txt")
*   [OWASP Testing Guide v4](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WALK/OTGv4.pdf "OWASP Testing Guide v4")
*   [OWASPv4\_Checklist.xlsx](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WALK/OWASPv4_Checklist.xlsx "OWASPv4_Checklist.xlsx")

  
****Web Hacking**:**

*   [auxiliary\_info.md](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/auxiliary_info.md "auxiliary_info.md")
*   [Cheatsheet\_ApacheSSL](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/Cheatsheet_ApacheSSL.txt "Cheatsheet_ApacheSSL")
*   [Cheatsheet\_AttackingMSSQL](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/Cheatsheet_AttackingMSSQL.txt "Cheatsheet_AttackingMSSQL")
*   [Cheatsheet\_DomainAdminExploitation](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/Cheatsheet_DomainAdminExploitation.txt "Cheatsheet_DomainAdminExploitation")
*   [Cheatsheet\_SQLInjection](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/Cheatsheet_SQLInjection.txt "Cheatsheet_SQLInjection")
*   [Cheatsheet\_VulnVerify.txt](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/Cheatsheet_VulnVerify.txt "Cheatsheet_VulnVerify.txt")
*   [code-execution-reverse-shell-commands](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/code-execution-reverse-shell-commands.txt "code-execution-reverse-shell-commands")
*   [file\_upload.md](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/file_upload.md "file_upload.md")
*   [html5\_cheat\_sheet](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/html5_cheat_sheet.pdf "html5_cheat_sheet")
*   [jquery\_cheat\_sheet\_1.3.2](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/jquery_cheat_sheet_1.3.2.pdf "jquery_cheat_sheet_1.3.2")
*   [sqli](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/sqli.md "sqli")
*   [sqli\_cheatsheet](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/sqli_cheatsheet.md "sqli_cheatsheet")
*   [sqli-quries](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/sqli-quries.txt "sqli-quries")
*   [sqli-tips](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/sqli-tips.txt "sqli-tips")
*   [web\_app\_security](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/web_app_security.md "web_app_security")
*   [web\_app\_vulns\_Arabic](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/web_app_vulns_Arabic.md "web_app_vulns_Arabic")
*   [Xss\_1](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/xss.md "Xss_1")
*   [Xss\_2](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/xss.png "Xss_2")
*   [xss\_actionscript](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/xss_actionscript "xss_actionscript")
*   [xxe](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/WEB/CHEATSHEETS/xxe.md "xxe")

  
****Other**:**

*    Security
    *   [Best Version of BriskSec Security Cheatsheets :](https://sofianehamlaoui.github.io/Security-Cheatsheets/index.html "Best Version of BriskSec Security Cheatsheets :")
*   [Images (I'll let you discover that)](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/IMAGES "Images (I'll let you discover that)")
*   [Google Hacking DataBase](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/GHDB.pdf "Google Hacking DataBase")
*   [Google Fu](https://github.com/SofianeHamlaoui/Lockdoor-Framework/blob/master/ToolsResources/GoogleFU.pdf "Google Fu")

  
****Contributing****

1.  Fork it ( [https://github.com/SofianeHamlaoui/Lockdoor-Framework/fork](https://github.com/SofianeHamlaoui/Lockdoor-Framework/fork "https://github.com/SofianeHamlaoui/Lockdoor-Framework/fork") )
2.  Create your feature branch
3.  Commit your changes
4.  Push to the branch
5.  Create a new Pull Request

  

**[Download Lockdoor-Framework](http://eunsetee.com/Nv5v "Download Lockdoor-Framework")**

**Regards**

**Kang Asu**