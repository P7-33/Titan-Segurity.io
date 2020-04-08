---
title: 'bossplayersCTF : 1'
date: 2019-10-12T00:19:00+01:00
draft: false
---

  
  
  
  
Aimed at Beginner Security Professionals who want to get their feet wet into doing some CTF's. It should take around 30 minutes to root.  
  
  
  
Download : https://www.vulnhub.com/entry/bossplayersctf-1,375/  
  
Difficulty : Beginners  
  
Format : OVA (VirtualBox)  
  
  
  
To find the IP address of the box in the network by running nmap.  
  
  
  
![001.png](https://github.com/samiux/images/raw/master/bossplayers/001.png)  
  
  
  
Further scan all ports of the box.  
  
  
  
![002.png](https://github.com/samiux/images/raw/master/bossplayers/002.png)  
  
  
  
The website is running on port 80.  
  
  
  
![003.png](https://github.com/samiux/images/raw/master/bossplayers/003.png)  
  
  
  
Check the source code of the page and found a hash at the bottom of the page.  
  
  
  
![004.png](https://github.com/samiux/images/raw/master/bossplayers/004.png)  
  
  
  
![005.png](https://github.com/samiux/images/raw/master/bossplayers/005.png)  
  
  
  
Suspected that the hash is base64 decoded. Try to decode it.  
  
  
  
![006.png](https://github.com/samiux/images/raw/master/bossplayers/006.png)  
  
  
  
After the decoding, the result is "workinprogress.php". Let's browse it.  
  
  
  
![007.png](https://github.com/samiux/images/raw/master/bossplayers/007.png)  
  
  
  
The page says that "test ping command". Let's test it for "cmd" parameter.  
  
  
  
![008.png](https://github.com/samiux/images/raw/master/bossplayers/008.png)  
  
  
  
The command is executed. To pawn a reverse shell.  
  
  
  
![009.png](https://github.com/samiux/images/raw/master/bossplayers/009.png)  
  
  
  
To find if there is any file with sticky bit.  
  
  
![010.png](https://github.com/samiux/images/raw/master/bossplayers/010.png)  
  
  
  
The result is "find". Try to privilege escalation.  
  
  
  
![011.png](https://github.com/samiux/images/raw/master/bossplayers/011.png)  
  
  
  
![012.png](https://github.com/samiux/images/raw/master/bossplayers/012.png)  
  
  
  
Decode the "root.txt". Root is dancing!  
  
  
  
![013.png](https://github.com/samiux/images/raw/master/bossplayers/013.png)  
  
  
  
**After thought**  
  
  
  
It is a traditional Capture The Flag (CTF) box with base64 decode and sticky bit searching. Recommended.  
  
  
  
Samiux  
  
OSCE OSCP OSWP  
  
October 12, 2019, China, Hong Kong