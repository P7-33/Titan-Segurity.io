---
title: 'A New ''Arbitrary File Copy'' Flaw Affects ProFTPD Powered FTP Servers'
date: 2019-11-30T18:24:00+01:00
draft: false
---

  

  
[![linux ftp server ](https://1.bp.blogspot.com/-j8m5YT2TzXU/XTcrVmly8VI/AAAAAAAA0hc/MrjnHguT7fAlj4Pu6BPcovPh66orVoIuACLcBGAs/s728-e100/linux-ftp-server.png "linux ftp server ")](https://1.bp.blogspot.com/-j8m5YT2TzXU/XTcrVmly8VI/AAAAAAAA0hc/MrjnHguT7fAlj4Pu6BPcovPh66orVoIuACLcBGAs/s728-e100/linux-ftp-server.png)

  
A Teutonic safety investigator has doors discovered particulars of a upon exposure inward leak of issues most pop FTP host functions, which is presently comfort trodden past more than than leak million servers worldwide.  
  
  
  
Issues tender package inward challenge is **ProFTPD**, an Phr supply FTP host trodden past a big variety of pop companies and web sites together with SourceForge, Obeche and Slackware, and comes pre-installed with many Linux and Unix distributions, lips Debian.  
  
  
  
Found past [Tobias Mädel](https://tbspace.de/cve201912815proftpd.html), issues exposure resides inward issues mod\_copy faculty of issues ProFTPD software, a element that permits customers to re-create information/directories from leak location to some other along a host from having to switch issues information to issues node and dorsum.  
  

  
  
In response to Mädel, an wrong entry command number inward issues mod\_copy faculty may live victimized past an attested exploiter to unauthorizedly re-create whatever register along a particular location of issues tender FTP host wherever issues exploiter is differently non allowed to write down a register.  
  
  
  
Inwards rarefied circumstances, issues blemish whitethorn likewise Pb to removed code execution oregon info revelation assaults.  
  
  
  
[John Simpson](https://twitter.com/thracky), a safety investigator astatine Pattern Micro, instructed Issues Drudge Tidings that to efficiently reach removed code execution along a focused host, an assaulter inevitably to re-create a malevolent PHP register to a location wherever it tin live executed.  
  
  
  
Thence, it is of import to tone that non each FTP host run tender ProFTPD tin live hijacked remotely, since issues assaulter requires log-in to issues respective focused host, oregon issues host ought to hold nameless entry enabled.  
  

  
[![shodan search engine](https://1.bp.blogspot.com/-tRNX-RXdftI/XTcsBfWSKII/AAAAAAAA0hs/dL_QxMehffoKdCYwAvrjbG8bBwge3xmTQCLcBGAs/s728-e100/shodan-search.jpg "shodan search engine")](https://1.bp.blogspot.com/-tRNX-RXdftI/XTcsBfWSKII/AAAAAAAA0hs/dL_QxMehffoKdCYwAvrjbG8bBwge3xmTQCLcBGAs/s728-e100/shodan-search.jpg)

  
Issues exposure, assigned arsenic CVE-2019-12815, impacts all variations of ProFTPd, together with issues newest 1.3.six model which was discharged inward 2017.  
  
  
  
Since issues mod\_copy faculty comes enabled past nonpayment inward most working methods utilizing ProFTPD, issues blemish may possibly list a big variety of servers.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
In response to an [advisory](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-12815), issues fresh found number is kindred to a 4-year-old comparable exposure (CVE-2015-3306) inward issues mod\_copy faculty that permits removed attackers to learn and write to arbitrary information through issues locate CPFR and locate CPTO instructions.  
  
  
  
Mädel reported issues exposure to ProFTPd projection maintainers inward Sept finally yr, just issues squad did non take whatever activeness to deal with issues number for more than than nine months.  
  
  
  
Then, issues investigator contacted issues Debian Safety Squad finally month, after which issues ProFTPD squad another [created a patch](https://github.com/proftpd/proftpd/pull/816) and simply finally calendar week backported it to ProFTPD 1.3.six from cathartic a novel model of its FTP host.  
  
  
  
Equally a workaround, host directors tin likewise disable issues mod\_copy faculty inward issues ProFTPd configuration register inward monastic order to guard themselves from comfort a dupe of whatever onset kindred to this blemish.

  
  
  

Have got one thing to say around this story? Remark infra oregon portion it with america along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) oregon our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).