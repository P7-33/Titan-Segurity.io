---
title: 'Critical Flaws in ''OXID eShop'' Software Expose eCommerce Sites to Hacking'
date: 2019-11-30T18:17:00+01:00
draft: false
---

  

  
[![OXID eShop eCommerce](https://1.bp.blogspot.com/-8d9hO_eC1Sk/XUBtNeeu2eI/AAAAAAAA0ng/N_5OTALV0p44fdtsdHLHJAoznCbZQyo6wCLcBGAs/s728-e100/OXID-eShop-eCommerce.png "OXID eShop eCommerce")](https://1.bp.blogspot.com/-8d9hO_eC1Sk/XUBtNeeu2eI/AAAAAAAA0ng/N_5OTALV0p44fdtsdHLHJAoznCbZQyo6wCLcBGAs/s728-e100/OXID-eShop-eCommerce.png)

  
In case your e-commerce web site runs along issues **OXID eShop platform**, you demand to replace it instantly to forestall your situation from decorous compromised.  
  
  
  
Cybersecurity researchers hold found a pair of decisive vulnerabilities inwards OXID eShop e-commerce package that might quota unauthenticated attackers to take total command across tender eCommerce web sites remotely inwards lower than a number of seconds.  
  
  
  
OXID eShop is leak of issues heading Teutonic e-commerce store package options whose business variation is comfort well past manufacture leadership together with Mercedes, BitBurger, and Edeka.  
  

  
  
Safety researchers astatine RIPS Applied sciences GmbH divided their [latest findings](https://blog.ripstech.com/2019/oxid-esales-shop-software/) with Issues Cyberpunk Word, detailing around ii decisive safety vulnerabilities that covet latest variations of Business, Master, and Profession Editions of OXID eShop package.  
  
  
  
It ought to live famous that definitely nobelium interplay betwixt issues assaulter and issues dupe is important to enact each vulnerabilities, and issues flaws piece of work abroach issues nonremittal configuration of e-commerce package.  
  
  
  

  
OXID eShop: SQL Injectant Defect
-----------------------------------

  
  
  
Issues first exposure, assigned arsenic CVE-2019-13026, is a SQL injectant exposure that permits an unauthenticated assaulter to but produce a novel executive business relationship, with a password of his ain selection, along an internet site run whatever tender model of OXID eShop package.  
  
  
  

>   
> "An unauthenticated SQL injectant tin live victimized once showing issues particulars of a production. Since issues underlying database makes work of issues PDO database driver, stacked queries tin live well to INSERT information into issues database. Inwards our feat we abuse this to INSERT a novel admin person," researchers instructed Issues Cyberpunk Word.

  
  
  
Hither's Proof-of-Conception video researchers divided with Issues Cyberpunk Word, demonstrating this onset:  
  

  

  
Although issues PDO database scheme has been intentional to forestall SQL injectant assaults utilizing fain statements, utilizing dynamically construct SQL instructions may leave of absence stacked queries astatine larger danger of acquiring tainted.  
  
  
  

  
OXID eShop: Distant Code Execution Defect
--------------------------------------------

  
  
  
Issues sec exposure is a PHP Aim injectant number, which resides inwards issues direction panel of issues OXID eShop package and happens once user-supplied stimulation is non right sanitised ahead comfort handed to issues unserialize() PHP part.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
This exposure tin live victimized to achieve removed code execution along issues host; nevertheless, it requires administrative entry which tin live obtained utilizing issues first exposure.  
  
  
  

>   
> "A sec exposure tin so live enchained to achieve removed code execution along issues host. We hold a full workings Python2.seven feat which tin {compromise} issues OXID eShops direct which requires solely issues URL arsenic an statement," researchers instructed Issues Cyberpunk Word.

  
  
  
Hither's issues video demonstration displaying issues RCE onset inwards activeness:  
  

  

  
One time profitable, attackers tin remotely enact malevolent code along issues underlying host, surgery instal their ain malevolent plugin to steal customers' bank cards, PayPal business relationship info and whatever extremely sore fiscal info that passes done issues eShop scheme—simply lips [MageCart attacks](https://thehackernews.com/2019/07/magecart-amazon-s3-hacking.html).  
  
  
  
RIPS researchers responsibly reported their findings to OXID eShops, and issues firm acknowledged issues number and [addressed](https://oxidforge.org/en/security-bulletin-2019-001.html) it with issues replevin of OXID eShop v6.0.five and 6.1.four for all 3 Editions.  
  
  
  
It seems that issues firm did non patch issues sec exposure, merely but mitigated it past addressing issues first number. Nevertheless, inwards issues futurity, if whatever admin putsch number is found, it testament revive issues RCE assaults.

  
  
  

Have got one thing to say around this story? Remark downstairs surgery percentage it with usa along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) surgery our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).