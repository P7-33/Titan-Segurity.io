---
title: 'View2aKill: Vulnhub Walkthrough'
date: 2020-02-01T15:46:00+01:00
draft: false
---

Today we’ll be sharing another CTF challenge walkthrough. This lab is highly inspired by the James Bond movie- “A View to a Kill.” The lab is made by creosote and hosted on Vulnhub.

You can download the lab [here](https://www.vulnhub.com/entry/view2akill-1,387/)

According to the Author:

Mission: Millionaire psychopath Max Zorin is a mastermind behind a scheme to destroy Silicon Valley in order to gain control over the international microchip market. Get root and stop this madman from achieving his goal!

*   Difficulty: **Intermediate**
*   Flag is /root/flag/flag.sh
*   Use in VMware. DHCP enabled.
*   Learning Objectives: Web Application Security, Scripting, Linux enumeration and more.

### **Penetration Testing Methodologies**

*   **Network Scanning**
    *   netdiscover
    *   Nmap scan
    *   Finding ports
*   **Enumeration**
    *   Enumerating directories
    *   Finding backup archive
    *   Enumerating username and finding the password
    *   Finding /sentrifugo
*   **Exploitation**
    *   Exploiting file upload vulnerability in sentrifugo
    *   Gaining shell
    *   Enumerating users and their home directories
    *   Logging in Jenny
*   **Post Exploitation**
    *   Finding aView.py script with Jenny’s group permissions
    *   Reading note.txt using this script
    *   Discovering algorithm for secret directories and finding directories by creating a custom script
    *   Finding remote
    *   Gaining root shell

Let’s begin then,

On netdiscover scan, we found the IP address of the machine to be 192.168.238.161

![](https://i0.wp.com/1.bp.blogspot.com/-FnKwCvsJrgY/XjV4qInfc3I/AAAAAAAAiiU/ln8XXywAuuwvLnQA-lklGMnb2wONGi4LACLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

On running a nmap scan, we found 4 ports to be open. There was a webpage as well and nmap had also enumerated 4 disallowed entries in robots.txt

![](https://i1.wp.com/1.bp.blogspot.com/-EsUxdu6Xfww/XjV4tFLqpgI/AAAAAAAAijA/h62dLXspk6Q2gtu8Je1_yzUD0kBLErgPwCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

We opened these 4 directories one by one and saw HR acquisition portal on

![](https://i0.wp.com/1.bp.blogspot.com/--c_cpZbmny4/XjV4xGYaEgI/AAAAAAAAijs/eGaoZ_TbgmgceHiahx1sWjVG1n3sse4bQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

On /dev there was an index listing of multiple files. There were PDFs on some kind of RFID device, text file, images and most importantly we saw a backup archive. We downloaded it.

![](https://i1.wp.com/1.bp.blogspot.com/-BSfPsb4DCpM/XjV4zLJhRzI/AAAAAAAAikA/VT4WjG624x4_Yl7VqQA5MhkjhicAY8lmwCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Inside that archive were 4 text files among which, one important text file caught our eye which had info about a new employee chuck.

![](https://i2.wp.com/1.bp.blogspot.com/-eDY2pkJWa6I/XjV4zct_t6I/AAAAAAAAikI/6ccU7QT80L0y9DsVukfaTZBIn29KrDsgACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Now, in /dev directory the PDFs were starting to make sense! The password=secret word in a video+transmid freq of HID reader

In one of the PDFs, we saw a manual on HID proxcard reader and found the frequency to be **125Hz**

![](https://i0.wp.com/1.bp.blogspot.com/-1g4gkYaoQ8s/XjV4z9WbdBI/AAAAAAAAikM/k-y-kV0579sjK2iGjZDj9mPEypYhsUSSwCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

I didn’t see any video in /dev but there was a gif file which had a detonator in it. It said the word **helicopter**

![](https://i2.wp.com/1.bp.blogspot.com/-qMeNF17RhtM/XjV40cNLkkI/AAAAAAAAikQ/-wXUg7FFNHccEeWE5JHaezhtTSqvVBrYACLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

So, the valid credentials were: [chuck@localhost.com](mailto:chuck@localhost.com) and pass: helicopter125

We tried to log it in the HR portal on /zorin

![](https://i2.wp.com/1.bp.blogspot.com/-xeKFmJYXZws/XjV40RR-yJI/AAAAAAAAikU/ghaShoqBfgEQVOt-FvOuWZRvyWkeE2KEACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

It said that /sentrifugo was where temporarily HR portal had moved. We moved there to find a login screen

![](https://i2.wp.com/1.bp.blogspot.com/-2w9YnKfthZk/XjV40kSEIPI/AAAAAAAAikY/FkG6MK_d6ZoOEfrmC0_zes_7l9weAMi3ACLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

It successfully logged us in with the found credentials! Now it was certain that exploitation had to begin from here. We tried to find any kind of vulnerability in sentrifugo platform and luckily we found one on exploit-db

![](https://i0.wp.com/1.bp.blogspot.com/-RQ9ymdCZdfU/XjV4qRWWP3I/AAAAAAAAiic/VRdAVeCIeoUTHnv94nhC0si1wq9IjZiVwCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

We went on to the portal>expenses>add>receipts and added our php-reverse-shell with double extension methodology

![](https://i1.wp.com/1.bp.blogspot.com/-bK8Z2ndg_KY/XjV4qYSCWgI/AAAAAAAAiiY/AB_M25FR30wslQz6NEHIY-3G2TUhX5zpQCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

It’s the webshell available in /usr/share/webshells. Just change the code to your own IP and make it double extension to .php.doc

![](https://i2.wp.com/1.bp.blogspot.com/-Rohtf1VLD8Y/XjV4q0R_cKI/AAAAAAAAiig/fa5UTCKp3rI0eVVLT0qBAhIGjp5a2zUjgCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

Now we intercepted the upload using burpsuite and passed it on as php and it successfully accepted it!

![](https://i1.wp.com/1.bp.blogspot.com/-t2HHcdWbzxI/XjV4rU-BWNI/AAAAAAAAiik/VVTjAsGeopc8UatuNhzRvd9CsebQbWGzwCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

We changed the extension from .php.doc to simply PHP and changed our IP from burpsuite only.

![](https://i1.wp.com/1.bp.blogspot.com/-_b_If0Sd8sw/XjV4reiVdvI/AAAAAAAAiio/Ea0TnkE4wKca5dn4MZzNtL6A67DTL34LwCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

Once our shell was uploaded we started a reverse netcat listener on port 1234 and accepted the connection! We got our connection simply by viewing the shell that got uploaded.

![](https://i2.wp.com/1.bp.blogspot.com/-_-5H0_hvqRk/XjV4sCtWUAI/AAAAAAAAii0/dYUNZ66BgZw9ToMhhHlfMJQLP998vLZsgCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

First things first, we imported a pseudo teletype using python one-liner.

```
python -c 'import pty;pty.spawn("/bin/bash")'
```

![](https://i1.wp.com/1.bp.blogspot.com/-v4zqTsV8FHI/XjV4sJ9p3EI/AAAAAAAAiiw/04UkC14vbQsoRl2MRjLYeVH48AhFxJtBACLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

Next, we traversed to the home directory and found there were 4 user directories there. In /home/jenny there was an archive named **dsktp\_backup.zip** which seemed interesting so we unzipped it and found two text files. One had jenny’s password in it and other had some instructions among which there was a mention of a script called **aView.py**

![](https://i2.wp.com/1.bp.blogspot.com/-m16_qbSgg38/XjV4s7RqJGI/AAAAAAAAii4/CsCucHgA2vcV5kGwG5XhPNwkrhk83euvQCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

We logged into jenny with a password **!!!sfbay!!!** and traversed to /home/max to find that python script. Viewed the source code and found that it was simply printed out some text.

![](https://i1.wp.com/1.bp.blogspot.com/-2qCoufFnfCM/XjV4tLbK9PI/AAAAAAAAii8/N6_MpVePyikLSxeG_9nCX7BrmKAazdRaACLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

But the interesting thing to note was that it was running commands as max. And there was a note.txt in the same directory which jenny couldn’t read. So we added some code into the preexisting python script that would simply stdout the note.txt file in hope that it will be useful for privilege escalation. I wrote a script av.py that had the same content as existing script plus command to print out note.txt

You can clone this script from our GitHub Repo by clicking [here](https://github.com/Ignitetechnologies/view2akill/blob/master/av.py).

![](https://i2.wp.com/1.bp.blogspot.com/-S6l-9h5FYIw/XjV4t_e_BgI/AAAAAAAAijE/8ntZZRteIsEZ9GIiU_psTbqcODCDUA4pwCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

On the victim’s /tmp directory I downloaded this script using wget command. Then I traversed back in /home/max to simply stdout av.py and redirect it’s output in aView.py so that when jenny runs it, it also displays note.txt

![](https://i1.wp.com/1.bp.blogspot.com/-f46yDwFERuE/XjV4uXh0_II/AAAAAAAAijI/28yXg2fvg2UNwJ0uEDnKgHOXsLFqUzoigCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

Now, in note, scarpine wrote that a secret directory exists which is hashed using the algorithm:

```
sha1(lower\_alpha+”view”+digit+digit)
```

This directory existed on port 8191 and had to be found out. I used a tool called mp64 to create this list using given algorithm in clear text and then coded a python script to covert this list into its respective SHA1 hashes.

```
mp64 ?lview?d?d > fuzz.txt  
python fuzzing.py > new\_fuzz.txt
```

We can then use a simple python/c script to convert the strings into sha1 hashes or use one of the online tools such as [http://www.sha1-online.com/](http://www.sha1-online.com/)

This could also be done by this following code which isn’t that complicated. 

You can clone this script from our GitHub from our Repo by clicking [here](https://github.com/Ignitetechnologies/view2akill/blob/master/new.py).

![](https://i2.wp.com/1.bp.blogspot.com/-VQp5bCtdUuk/XjV4vB5OlxI/AAAAAAAAijU/X789YsdyCvQwLjcN7NbcdlYIVA2bb3ouACLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

By using the second method, we saved the hashes in directories.txt file and ran dirb scan using this list

![](https://i2.wp.com/1.bp.blogspot.com/-G3MP4MgKoXc/XjV4vUb_YCI/AAAAAAAAijY/YmO-Otzxs2YoXF5FryvBd9ixi2Dghoj6QCLcBGAsYHQ/s1600/25.png?w=687&ssl=1)

Wow. A bunch of files were found. We tried to open the first directory and looks like the author got us here!

![](https://i0.wp.com/1.bp.blogspot.com/-z6mUVYSGh7Y/XjV4vaoFbWI/AAAAAAAAijc/fTGlGmu2CHYWcszOFX3w1JHB7jGtZ8JvgCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

But wait, there was a directory that had unusual length as compared to other directories. Maybe this had something

![](https://i2.wp.com/1.bp.blogspot.com/-wq72GAfRtDE/XjV4wNc5CSI/AAAAAAAAijk/qXhqyiwtt_sHh8bKdJ6sH12UiInjyUlZQCLcBGAsYHQ/s1600/28.png?w=687&ssl=1)

Looks like we found the remote! We executed this using the button and a script called **run.php** seemed to run.

![](https://i0.wp.com/1.bp.blogspot.com/-9zuil13o-NI/XjV4wWetAcI/AAAAAAAAijo/eUZKGviabUE7j6Y7wNeKFjCV2Z40JXwTgCLcBGAsYHQ/s1600/29.png?w=687&ssl=1)

Hey! This text seems familiar. You remember **aView.py** file? It seems like this run.php file was taking the stdout from aView.php file and displaying it. Now when I remember, the comment in aView.py also said: “executed from php app…”

So we decided to replace some of the code in aView.py by pentestmonkey’s python one-liner reverse shell!

We SSHed in jenny first and used nano to display contents of aView.py

![](https://i2.wp.com/1.bp.blogspot.com/-U7vb19uJNC4/XjV4xRtdmOI/AAAAAAAAijw/xjIZXvUVUuwu0--_7v8cL15V1Sa666iXQCLcBGAsYHQ/s1600/30.png?w=687&ssl=1)

We replaced aView.py with this code, which can be cloned from our GitHub Repo by clicking [here](https://github.com/Ignitetechnologies/view2akill/blob/master/aView.py). 

![](https://i1.wp.com/1.bp.blogspot.com/-XiEIIiVRpXc/XjV4yMxTU7I/AAAAAAAAij4/lOvoFn9wGlQjiuIj2a-HZ7aSb-ceOWKAwCLcBGAsYHQ/s1600/32.png?w=687&ssl=1)

We set up a reverse listener on port 1234 and waited for shell and voila! Seems like run.php had root permissions since we got a root shell! We traversed to /root to read the flag

![](https://i0.wp.com/1.bp.blogspot.com/-l4KvtDG65Kc/XjV4yRGssHI/AAAAAAAAij8/2fivb7bQvpsPKYZHS_FqyxdOQkVOwAWnQCLcBGAsYHQ/s1600/33.png?w=687&ssl=1)

Lets open :8007 on our browser and read congratulatory flag!

![](https://i1.wp.com/1.bp.blogspot.com/-fcVaT7cYufw/XjV4zC6jTHI/AAAAAAAAikE/-8E9Dk8OI4so_i-Jjpb0zbVLJpynv88yACLcBGAsYHQ/s1600/34.png?w=687&ssl=1)

So, this was how we solved this lab. In my opinion, if you know some things like a bit of python scripting and knowledge of basic Linux permissions and tools, lab won’t feel hard. It was certainly lengthy though due to the requirement of scripting but I thoroughly enjoyed the lab. Thanks to creosote for this!

**Author: Harshit Rajpal **is an InfoSec researcher and left and right brain thinker. Contact** [here](https://in.linkedin.com/in/harshit-rajpal-79bb43103)**

The post [View2aKill: Vulnhub Walkthrough](https://www.hackingarticles.in/view2akill-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/31hqORF