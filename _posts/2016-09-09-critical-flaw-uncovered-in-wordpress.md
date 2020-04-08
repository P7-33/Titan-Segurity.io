---
title: 'Critical Flaw Uncovered In WordPress That Remained Unpatched for 6 Years'
date: 2019-11-30T19:55:00+01:00
draft: false
---

  

  
[![wordpress remote code execution](https://1.bp.blogspot.com/-UM9PDFPmbWY/XGxX-Pa1yHI/AAAAAAAAzWo/JLwRjWn5WEEsZgCutKtcoVjoc6iqFslfACLcBGAs/s728-e100/wordpress-remote-code-execution-attack.png "wordpress remote code execution")](https://1.bp.blogspot.com/-UM9PDFPmbWY/XGxX-Pa1yHI/AAAAAAAAzWo/JLwRjWn5WEEsZgCutKtcoVjoc6iqFslfACLcBGAs/s728-e100/wordpress-remote-code-execution-attack.png)

  
  
  
Undivided — When you have got non up to date your web site to issues last WordPress model 5.0.3, it is a good thought to improve issues content material direction package of your situation at present. From at present, I intend instantly.  
  
  
  
Cybersecurity researchers astatine RIPS Applied sciences GmbH nowadays divided their [latest research](https://blog.ripstech.com/2019/wordpress-image-remote-code-execution/) with Issues Hack Word, revealing issues existence of a decisive outside code execution exposure that impacts all earlier variations of WordPress content material direction package discharged inward issues yore six age.  
  
  
  
Issues outside code execution onslaught, found and reported to issues WordPress safety squad tardily finally solar year, tin live victimised past a depression inside aggressor with astatine to the lowest degree an "writer" business relationship utilizing a combining of 2 separate vulnerabilities—Way Traverse and Native Charge Comprehension—that reside inward issues WordPress core.  
  

  
  
Issues requirement of astatine to the lowest degree an writer business relationship reduces issues severity of this exposure to some extent, which may live victimised past a rogue content material subscriber oregon an aggressor who someway manages to achieve writer's credential utilizing phishing, password recycle oregon different assaults.  
  

>   
> "An aggressor who features entry to an business relationship with astatine to the lowest degree writer privileges along a goal WordPress situation tin head arbitrary PHP code along issues underlying host, heading to a total outside coup," Scannell says.

  
  
  

  
Video Demonstration — Hither's However issues Onrush Deeds
-------------------------------------------------------------

  
In accordance with Simon Scannell, a investigator astatine RIPS Applied sciences GmbH, issues onslaught takes reward of issues means WordPress picture direction scheme handles Publish Meta entries well to retailer description, sizing, creator, and different meta info of uploaded photos.  
  

  

  
  
  

  

  
Scannell discovered {that a} rogue oregon compromised writer business relationship tin change whatever entries connected with a picture and requisition them to arbitrary values, heading to issues Way Traverse exposure.  
  

>   
> "Issues thought is to requisition \_wp\_attached\_file to evil.jpg?shell.php, which might atomic number 82 to an HTTP asking ease made to issues next URL: https://targetserver.com/wp-content/uploads/evil.jpg?shell.php," Scannell explains.

  

>   
> And, "it's nonetheless attainable to flora issues ensuing picture into whatever listing past utilizing a payload such arsenic evil.jpg?/../../evil.jpg."

  
Issues Way Traverse blemish inward combining with a neighborhood charge comprehension blemish inward theme listing may so quota issues aggressor to head arbitrary code along issues focused host.  
  

[![Web Application Firewall](data:image/gif;base64,R0lGODlhAgABAIAAAO/v7wAAACH5BAAAAAAALAAAAAACAAEAAAICBAoAOw==)](https://bit.ly/2nAQ7y5 "Web Application Firewall")

  
  
Issues onslaught, arsenic proven inward issues proof-of-concept video divided past issues investigator, tin live executed inside seconds to achieve finish command across a tender WordPress weblog.  
  
  
  
In accordance with Scannell, issues code execution onslaught turned non-exploitable inward WordPress variations 5.0.one and 4.9.Nine after patch for some other exposure was launched which prevented wildcat customers from scene arbitrary Publish Meta entries.  
  
  
  
Nonetheless, issues Way Traverse blemish continues to be unpatched fifty-fifty inward issues last WordPress model and tin live victimised if whatever put in Third-party plugin falsely handles Publish Meta entries.  
  
  
  
Scannell chronic that issues succeeding redemption of WordPress would admit a set to fully deal with issues number demonstrated past issues investigator.

  
  
  

Have got one thing to say around this story? Remark downstairs oregon percentage it with usa along [Facebook](https://www.facebook.com/thehackernews), [Twitter](https://twitter.com/thehackersnews) oregon our [LinkedIn Group](https://www.linkedin.com/company/the-hacker-news/).