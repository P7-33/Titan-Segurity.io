---
title: 'Quark-Engine'
date: 2020-01-05T12:12:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-ESdt19KkSf4/XgJ2hRQZ-RI/AAAAAAAARRs/LqAGKtak83U7QypPCApnPsb2ViK-o7AogCNcBGAsYHQ/s640/quark.png)](https://asciinema.org/a/288450)

**Quark-Engine - An Obfuscation-Neglect Android Malware Scoring System**

  

  

**Concepts**  
Android [malware analysis](https://www.kitploit.com/search/label/Malware%20Analysis "malware analysis") engine is not a new story. Every [antivirus](https://www.kitploit.com/search/label/Antivirus "antivirus") company has their own secrets to build it. With curiosity, we develop a malware scoring system from the perspective of Taiwan Criminal Law in an easy but solid way.  
We have an order theory of criminal which explains stages of committing a crime. For example, crime of murder consists of five stages, they are determined, conspiracy, preparation, start and practice. The latter the stage the more we’re sure that the crime is practiced.  
According to the above principle, `we developed our order theory of android malware`. We develop five stages to see if the malicious activity is being practiced. They are 1. Permission requested. 2. Native API call. 3. Certain combination of native API. 4. Calling sequence of native API. 5. APIs that handle the same register. We not only define malicious activities and their stages but also develop weights and thresholds for calculating the threat level of a malware.  
Malware evolved with new techniques to gain difficulties for reverse engineering. [Obfuscation](https://www.kitploit.com/search/label/Obfuscation "Obfuscation") is one of the most commonly used techniques. In this talk, we present a Dalvik [bytecode](https://www.kitploit.com/search/label/Bytecode "bytecode") loader with the order theory of android malware to neglect certain cases of obfuscation.  
Our Dalvik bytecode loader consists of functionalities such as 1. Finding cross reference and calling sequence of the native API. 2. Tracing the bytecode register. The combination of these functionalities (yes, the order theory) not only can neglect obfuscation but also match perfectly to the design of our malware scoring system.  
  
  
**Detail Report**  
This is a how we examine a real android malware (candy corn) with one single rule (crime).

```
$ quark -a sample/14d9f1a92dd984d6040cc41ed06e273e.apk \  
                 -r rules/ \  
                 --detail
```

  

[![](https://1.bp.blogspot.com/-v76G1yGTRw4/XgJtxmnRg1I/AAAAAAAARRc/toc0h5qcn9INl6ya_5_LReGb_YWXl4FBwCNcBGAsYHQ/s640/quark-engine_8.png)](https://1.bp.blogspot.com/-v76G1yGTRw4/XgJtxmnRg1I/AAAAAAAARRc/toc0h5qcn9INl6ya_5_LReGb_YWXl4FBwCNcBGAsYHQ/s1600/quark-engine_8.png)

  
**Summary Report**  
Examine with rules.

```
quark -a sample/14d9f1a92dd984d6040cc41ed06e273e.apk \  
               -r rules/ \  
               --easy
```

  

[![](https://1.bp.blogspot.com/-g8phbGX52XI/XgJ2HXTLavI/AAAAAAAARRk/MEwfreTYt2cSS1Z9E76VUOxTEpmWWN5cACNcBGAsYHQ/s640/quark-engine_9.png)](https://1.bp.blogspot.com/-g8phbGX52XI/XgJ2HXTLavI/AAAAAAAARRk/MEwfreTYt2cSS1Z9E76VUOxTEpmWWN5cACNcBGAsYHQ/s1600/quark-engine_9.png)

  
**Installation**

```
$ git clone [https://github.com/quark-engine/quark-engine.git](https://github.com/quark-engine/quark-engine.git); cd quark-engine/quark  
$ pipenv install  
$ pipenv shell  
$ python setup.py install
```

Make sure your python version is `3.7`, or you could change it from `Pipfile` to what you have.  
  
**Usage**

```
$ quark --help  
usage: quark [-h] [-e] [-d] -a APK -r RULE  
  
optional arguments:  
  -h, --help            show this help message and exit  
  -e, --easy            show easy report  
  -d, --detail          show detail report  
  -a APK, --apk APK     APK file  
  -r RULE, --rule RULE  Rules need to be checked
```

  

**[Download Quark-Engine](http://libittarc.com/3Ejg "Download Quark-Engine")**

**  
Regards**

**Kang Asu**