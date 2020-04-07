---
title: 'XposedOrNot'
date: 2020-01-18T17:17:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-nX8zkh8SHSw/XhUtzsb6h0I/AAAAAAAARWs/op3mQSEIxTko4imBaNShW-ng1b7cMo_mACNcBGAsYHQ/s640/XposedOrNot_1.png)](https://1.bp.blogspot.com/-nX8zkh8SHSw/XhUtzsb6h0I/AAAAAAAARWs/op3mQSEIxTko4imBaNShW-ng1b7cMo_mACNcBGAsYHQ/s1600/XposedOrNot_1.png)

**XposedOrNot - Tool To Search An Aggregated Repository Of Xposed Passwords Comprising Of ~850 Million Real Time Passwords**

  
XposedOrNot (XoN) tool is to search an aggregated repository of xposed passwords comprising of ~850 million [real time](https://www.kitploit.com/search/label/Real%20Time "real time") passwords. Usage of such compromised passwords is detrimental to individual account security.  
  
**What is Xposed Passwords?**  
The main aim of this project is to give a free platform for the general public to check if their password is exposed and compromised.  
This massive password collection is an accumulation of real passwords exposed in various data breaches around the world. [Passwords](https://www.kitploit.com/search/label/Passwords "Passwords") are curated from exposed breaches like Collection #1, Yahoo, etc. Adding to that, passwords are also commonly exposed in "pastes" in [pastebin.com](http://pastebin.com/). We have taken more than 40,000 such exposures and that is again added to this huge list.  
The collated passwords are hashed with a highly secure [hashing](https://www.kitploit.com/search/label/Hashing "hashing") algorithm SHA-3 ( Keccak-512 ), and stored in a one way hash for verification. No passwords are stored in plain text and the process of checking anonymously is explained in detail in our blog post, 850 million passwords for free explaining the technical and operational controls enforced for enhancing the security posture. Feel free to go through the same.  
[](https://www.blogger.com/u/7/null)

  

  
**How to install?**

```
git clone [https://github.com/Viralmaniar/XposedOrNot.git](https://github.com/Viralmaniar/XposedOrNot.git)  
cd XposedOrNot  
pip install -r requirements.txt  
python XposedorNot.py
```

  
**How to interpret an output?**  
The output will consist of JSON output for easy reference. Primary reasons for giving an output in JSON instead of a yes/no is to ensure that this can be further used by people to develop and improve on the huge list of real time exposed passwords aggregated here.  
Alright, the first element "anon" is added to all password hashes stored in XoN for enabling [privacy](https://www.kitploit.com/search/label/Privacy "privacy") conscious users to search as well. Second element "char" is a list of characteristics of the password, which can be further used for understanding the strength of the password to know if this will meet the [requirements](https://www.kitploit.com/search/label/Requirements "requirements") of applications in need. Many websites have policies on the use of selecting passwords based on number of characters, mixture of alphabets, numbers and special characters.  
The following table explains a bit more about the characteristics in simple terms :

Alphabet

Description

Digits

Count of numbers

Alphabets

Count of alphabets

Special chars

Count of special chars

Length

Length of the password

The last one "count" denotes the number of times, this password was observed in the collected xposed data breaches. For a comprehensive list of all xposed websites, please visit Xposed websites-XoN.  
Also, one another point to note is the use of Keccak-512 hashing for searching and storing data in XoN. Traditional hashing algorithms like MD5 and SHA1 are currently deprecated and also considering the enormous number of records exposed, I have gone ahead with Keccak-512 hashes.

  
Yes, Keccak-512 is 128 characters long and it consumes more storage.  
Two sample Keccak-512 hashes given for easy reference: **test - 1e2e9fc2002b002d75198b7503210c05a1baac4560916a3c6d93bcce3a50d7f00fd395bf1647b9abb8d1afcc9c76c289b0c9383ba386a956da4b38934417789e pass - adf34f3e63a8e0bd2938f3e09ddc161125a031c3c86d06ec59574a5c723e7fdbe04c2c15d9171e05e90a9c822936185f12b9d7384b2bedb02e75c4c5fe89e4d4 **Sample output on not finding the matching password hash:

```
 {  
  "Error": "Not found"  
}
```

  
**Collected Passwords timeline - thanks to DevaOnBreaches**  

[![](https://1.bp.blogspot.com/-JMTxVwdVZHY/XhUt9KKulgI/AAAAAAAARW0/JFfncA1ecUEaoStTFZIQDxfExqoGA-ATgCNcBGAsYHQ/s640/XposedOrNot_2.png)](https://1.bp.blogspot.com/-JMTxVwdVZHY/XhUt9KKulgI/AAAAAAAARW0/JFfncA1ecUEaoStTFZIQDxfExqoGA-ATgCNcBGAsYHQ/s1600/XposedOrNot_2.png)

  

[![](https://1.bp.blogspot.com/-RdsxXK6rJ0Y/XhUt9BaNHWI/AAAAAAAARW4/BuP970jFvbItlQwHtW__a924zbRNnXGOQCNcBGAsYHQ/s640/XposedOrNot_3.png)](https://1.bp.blogspot.com/-RdsxXK6rJ0Y/XhUt9BaNHWI/AAAAAAAARW4/BuP970jFvbItlQwHtW__a924zbRNnXGOQCNcBGAsYHQ/s1600/XposedOrNot_3.png)

  

[![](https://1.bp.blogspot.com/-Tgpz0ZdU_rk/XhUt9MNFNwI/AAAAAAAARWw/B7_zTtGIDhINh0kDYEJjHB_PeYbRx15hQCNcBGAsYHQ/s640/XposedOrNot_4.png)](https://1.bp.blogspot.com/-Tgpz0ZdU_rk/XhUt9MNFNwI/AAAAAAAARWw/B7_zTtGIDhINh0kDYEJjHB_PeYbRx15hQCNcBGAsYHQ/s1600/XposedOrNot_4.png)

  

[![](https://1.bp.blogspot.com/-h4b0AKYEjhI/XhUt-Q9292I/AAAAAAAARW8/5usQ5RdOBG4xaEetbf7bHtrk0duaYAONwCNcBGAsYHQ/s640/XposedOrNot_5.png)](https://1.bp.blogspot.com/-h4b0AKYEjhI/XhUt-Q9292I/AAAAAAAARW8/5usQ5RdOBG4xaEetbf7bHtrk0duaYAONwCNcBGAsYHQ/s1600/XposedOrNot_5.png)

  

[![](https://1.bp.blogspot.com/-Up4JHBG11Jk/XhUt-g8Pf1I/AAAAAAAARXA/itSi_6prjZcHXNuxAMbtMyZUP1H6w1gyACNcBGAsYHQ/s640/XposedOrNot_6.png)](https://1.bp.blogspot.com/-Up4JHBG11Jk/XhUt-g8Pf1I/AAAAAAAARXA/itSi_6prjZcHXNuxAMbtMyZUP1H6w1gyACNcBGAsYHQ/s1600/XposedOrNot_6.png)

  
Detailed list can be seen here: [https://xposedornot.com/xposed](https://xposedornot.com/xposed "https://xposedornot.com/xposed")  
  
**Questions?**  
Twitter: [@ManiarViral](https://twitter.com/maniarviral "@ManiarViral")  
LinkedIn: [https://au.linkedin.com/in/viralmaniar](https://au.linkedin.com/in/viralmaniar "https://au.linkedin.com/in/viralmaniar")  
  
**Credit**  
XposedOrNot is maintained by DevaOnBreaches. Big thanks for creating an API for your service. You can connect with him at [https://www.devaonbreaches.com/](https://www.devaonbreaches.com/ "https://www.devaonbreaches.com/")  
  

**[Download XposedOrNot](http://ellevolaw.com/3jSn "Download XposedOrNot")**

**Regards**

**Kang Asu**