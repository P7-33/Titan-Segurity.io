---
title: 'In Plain Sight:1: Vulnhub Walkthrough'
date: 2019-12-08T18:04:00+01:00
draft: false
---

In today’s article we will face an Intermediate challenge. Introducing the In Plain Sight:1 virtual machine, created by “[bzyo\_](https://twitter.com/bzyo_)” and is available on Vulnhub. This is another Capture the Flag challenge where we have to escalate privileges to find the root flag to complete the challenge.

Since these labs are available on the Vulnhub Website. We will be downloading the lab file from this [link](https://www.vulnhub.com/entry/in-plain-sight-1,400/).

### Penetration Testing Methodology

*   **Network Scanning**
    *   netdiscover
    *   nmap port scan
*   **Enumeration**
    *   FTP Enumeration
    *   Browsing HTTP Service
    *   Enumerating the wordpress
*   **Exploitation**
    *   Get a meterpreter session
*   **Post exploitation**
    *   Reading passwords from file
    *   Login into MySQL to find hashes
    *   Using john to crack the hashes
*   **Privilege escalation**
    *   Using su command
    *   Finding password
    *   Checking for SUID

### Walkthrough

### Network Scanning

The first step is to identify the target. So, to identify our target we will use the following command:

```
netdiscover
```

![](https://i1.wp.com/1.bp.blogspot.com/--Z1u0a1VaeM/Xe0dtrjGsWI/AAAAAAAAh1Q/aF08lD-IVagN4jJD-TxReCMIW1tSjGckACEwYBhgL/s1600/1.png?w=687&ssl=1)

Now we will use Nmap to gain information about the open ports and the services running on the target machine and for this, type the following command :

```
nmap -p- 192.168.43.8
```

![](https://i1.wp.com/1.bp.blogspot.com/-PW91KRfChOo/Xe0dxQQLR-I/AAAAAAAAh1U/kt42gCdx_hEp_lCPklGnluA9fB4Js315gCEwYBhgL/s1600/2.png?w=687&ssl=1)

From the nmap scan we can see that the Port 21, 22, 80 is open, it means we have the FTP, SSH and HTTP services running simultaneously. Firstly, let’s try enumeration with anonymous login on FTP.

![](https://i1.wp.com/1.bp.blogspot.com/-TYkbqWi-4QA/Xe0d1fWlBCI/AAAAAAAAh1Q/tqhDBg664qMDyed1jLnLl-k0li1hnxodQCEwYBhgL/s1600/3.png?w=687&ssl=1)

After logging in anonymously, we can see that there is a file todo.txt. Download this file using the get command. The content of todo.txt file doesn’t seem to be useful. You can read the file by using cat command.

As FTP wasn’t useful to us, we can now browse the website to see if we can find some information. And for this, open the IP address in our browser.

![](https://i1.wp.com/1.bp.blogspot.com/-TYkbqWi-4QA/Xe0d1fWlBCI/AAAAAAAAh1Q/tqhDBg664qMDyed1jLnLl-k0li1hnxodQCEwYBhgL/s1600/3.png?w=687&ssl=1)

This is an Apache2 Ubuntu Default page but after exploring it carefully we can see a line hinting to “/var/www/html/index.html”. So, let’s explore this page.

![](https://i1.wp.com/1.bp.blogspot.com/-ZBoFUZRX3SI/Xe0d2sty_uI/AAAAAAAAh1U/CIX3ox0eHB4oM-CQYyGrTtFRKvmM0Hl_QCEwYBhgL/s1600/5.png?w=687&ssl=1)

This page looks like a normal page but when we click anywhere on the page then it will lead us to the following new webpage :

![](https://i1.wp.com/1.bp.blogspot.com/-72xwqqOFSp0/Xe0d2-ucatI/AAAAAAAAh1M/8gSpEIo91wA5oGYwk5IevyVuGJ-yPOuDQCEwYBhgL/s1600/6.png?w=687&ssl=1)

As we can see that this webpage lets you to upload any image. So here we tried to upload the image and we succeed but when we try to upload a .php file the webpage give us an error. Upon exploring more, the URL of the webpage caught our attention and you can see that it looks like a hash so we copied it and tried to crack it by using john.

![](https://i2.wp.com/1.bp.blogspot.com/-ZA_Z8tlXlgA/Xe0d3dRftxI/AAAAAAAAh1M/9hgISdeloAwf9pBF0noH7RwL0ZRdGXEjwCEwYBhgL/s1600/7.png?w=687&ssl=1)

It was **“goodluck”**. At this point we were just being trolled.

We then tried to upload a simple .php file and when uploading a .php file we come across the following error :

![](https://i0.wp.com/1.bp.blogspot.com/-41t2wGnhNHg/Xe0d3dgb0AI/AAAAAAAAh1Q/SqK-P8LO6Pc_LNp3BGdeSGJ9YOex29z_QCEwYBhgL/s1600/8.png?w=687&ssl=1)

But this error leads us to a new page “upload.php”. Let’s check the source code of this page.

![](https://i1.wp.com/1.bp.blogspot.com/-sT-h9xniBm8/Xe0d3k4UjpI/AAAAAAAAh1Q/0FSP0vSSKowyn5nmlB7QaWUSJmlq3FjCACEwYBhgL/s1600/9.png?w=687&ssl=1)

Yes! There is a comment at the end of the source code. And this is a base64 encoded text, so let’s try to decode it by using the following command :

```
echo c28tZGV2LXdvcmRwcmVzcw== | base64 -d
```

![](https://i0.wp.com/1.bp.blogspot.com/-kSRTBj9izhM/Xe0dtkf5dgI/AAAAAAAAh1A/ZmupdkyzdhsJ17_RVKfo6Wqpw_QDpRDnACEwYBhgL/s1600/10.png?w=687&ssl=1)

When the text is decoded, it looks like a directory or a webpage. But before exploring it let’s see if there are more pages or not. Hence, use dirbuster.

![](https://i0.wp.com/1.bp.blogspot.com/-qfGsI0-lGtU/Xe0dtptsFrI/AAAAAAAAh1E/uhCqzSVnZLYNz5Wq7jA8w5mYuiZzSkilACEwYBhgL/s1600/11.png?w=687&ssl=1)

There are many pages and as the result shows us that CMS is wordpress, therefore, we can use wpscan to plough through the two specified pages that mentions wordpress. And for that use the following command :

```
wpcan --url "http://192.168.43.8/wordpress" --enumerate
```

![](https://i1.wp.com/1.bp.blogspot.com/-79bUxxMV-DY/Xe0du5zliBI/AAAAAAAAh1U/1yACRnXyQWoU5Py74erIcUSXkzNm04IDwCEwYBhgL/s1600/12.png?w=687&ssl=1)

Similarly, let’s enumerate the other page.

```
wpcan --url "http://192.168.43.8/so-dev-wordpress" --enumerate
```

![](https://i0.wp.com/1.bp.blogspot.com/-NfmPDkBkb9E/Xe0duwBwcaI/AAAAAAAAh1M/cngjfO-TzZgeU7aAbnGvwUSpx4hnmc7vQCEwYBhgL/s1600/13.png?w=687&ssl=1)

As you can see in the above image there are three users. And we have there usernames, we can simply use bruteforce to find their respective passwords and for that type :

```
wpscan --url "http://192.168.43.8/wordpress" -U bossperson -P /usr/share/wordlists/dirb/common.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-Nxo4QhKMsf0/Xe0du7SAQeI/AAAAAAAAh08/SP4roR10X0IDnRKyh9X-z7qxvLCjwhE8QCEwYBhgL/s1600/14.png?w=687&ssl=1)

Alas, we couldn’t find any password but not to worry as we can run the same command for the other page, let’s try it by typing :

```
wpscan --url "http://192.168.43.8/so-dev-wordpress" -U admin,mike -P /usr/share/wordlists/dirb/common.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-Nxo4QhKMsf0/Xe0du7SAQeI/AAAAAAAAh08/SP4roR10X0IDnRKyh9X-z7qxvLCjwhE8QCEwYBhgL/s1600/14.png?w=687&ssl=1)

And so, we finally found the password for the user admin. So now, let’s try to upload a shell using msfconsole. And through Metasploit we will use **exploit/unix/webapp/wp\_admin\_shell\_upload**.

![](https://i0.wp.com/1.bp.blogspot.com/-2BfMqwpo9yc/Xe0ieSH9IVI/AAAAAAAAh10/oWVM47tFdPMPJ-W8EBQ5_jOU8zjD5rCkwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

Once the exploit is intiated, type the set of following commands :

```
set PASSWORD admin  
set RHOST 192.168.43.8  
set USERNAME admin  
set TARGETURI /so-dev-wordpress  
exploit
```

![](https://i0.wp.com/1.bp.blogspot.com/-AWHHm4mVWMI/Xe0ieuZMIKI/AAAAAAAAh14/JAqDbdOigjIL_uq3G6igzZPB64gZdGMXACLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

As you can see, we are successful in getting our session, lets move onto shell of the target system and for that type shell and hit enter. And the next thing you know is you are in the shell of the target system. Now to get a proper authenticated session of shell type the following command :

```
python3 -c 'import pty;pty.spawn("/bin/sh")'
```

![](https://i0.wp.com/1.bp.blogspot.com/-WZTNuoOCnms/Xe0ie_8uSQI/AAAAAAAAh18/9QvbubQUSWYZzmWnumSe5QJDkCGG_KajACLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

As we have managed to get a shell. So now, we will explore the system more to find some useful files.

![](https://i0.wp.com/1.bp.blogspot.com/-QtmPzku1_FU/Xe0ifYXLYMI/AAAAAAAAh2A/sEJQZVcnjvoYedIEZUIX6J1ulRmwybozwCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

Upon changing the directory, we found wp-config.php. as it is a config file, there’s bound to be usefull information. Thus, we will try to read it’s content using the cat command :

```
cat wp-config.php
```

![](https://i0.wp.com/1.bp.blogspot.com/-PYSpgvs99Ss/Xe0if7ljCYI/AAAAAAAAh2I/B1BYOlI1CcALJwb4OL4WJtE4tJ4nfHNCACLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

These credentials are of mysql as you can see the prefix DB used which probably stands for DataBsase. So, we can try to login into mysql using these credentials and therefore, use the following commands :

```
bash  
mysql -u sodevwp -p
```

![](https://i0.wp.com/1.bp.blogspot.com/-wDRUFyH1ZkY/Xe0igfA1pcI/AAAAAAAAh2M/ix0MozKiRk0ho0r09MHXvFbWoHqgBTCfgCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

Yes, we are in! Let’s try and explore it further.

![](https://i0.wp.com/1.bp.blogspot.com/-i3DwmJ_AXk8/Xe0ihDFKu8I/AAAAAAAAh2Q/hML-kBUPQkIeDBbQQQY5xAl9Ll0AScj-gCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

We found a database “sodevwp” and hence, to change the database type :

```
show databases;  
use sodevwp  
show tables;  
select \* from sodevwp\_users;
```

![](https://i2.wp.com/1.bp.blogspot.com/-MsCCPz-gIhs/Xe0ihblrwCI/AAAAAAAAh2U/ygjKeim6FAsy9PBoJnKumOIQ-q2GuzlqQCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

Once the above commands are used successfully, you will find the following two hashes :

**$P$BD/ZmfBIhgjHKtkLpPKfhr2t5EDgZA. (for user admin)**

**$P$B3halPOgh4jqI1tDelkv5TGAHnaOC01 (for user mike)**

![](https://i1.wp.com/1.bp.blogspot.com/-4wCIuofw6qc/Xe0ihqgwe3I/AAAAAAAAh2Y/1pJm64pKPJoR2g2jkF-VPPQDyDrc8BcUACLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

We will now use john the riper with rockyou wordlist to crack these hashes and for that type :

```
john cracker -wordlist=/usr/share/wordlists/rockyou.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-4wCIuofw6qc/Xe0ihqgwe3I/AAAAAAAAh2Y/1pJm64pKPJoR2g2jkF-VPPQDyDrc8BcUACLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

As you can see in the image above that we found our passwords to the two major users and those are :

**admin:admin1**

**mike: skuxdelux**

Now, try and switch the user to mike and you can observe in the image below  that you can successfully do that; which means cracking the passwords was successful.

![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

Let’s move on for privilege escalation. Now, when you change your directory to /home and there you found a new user **“joe”**

And without wasting any time we traversed through **etc/passwd**.

![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

With etc/passwd we found out that password to **‘joe’** is **SmashMouthNoThanks**. So now, lets switch the user to joe with the foretold password.

![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

And just like that we have the access of the user ‘joe’.

Now to move forward the only thing we have to do is to get the last flag of the target. And to get the it we check for **SUID** using the command find. -perm /4000. Before executing this command, we will change our directory to “/” and after running the command we find the following useful binaries.

![](https://i1.wp.com/1.bp.blogspot.com/-R0Wvwx9MXDY/Xe0iiopWysI/AAAAAAAAh2g/CXg7CQIOfckf3a5b48LiCBk8hT3zD_ouwCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

And in **/bwrap** we found our last flag which you can observe from the image below :

![](https://i0.wp.com/1.bp.blogspot.com/-DEH_iF05O50/Xe0ij5SZhFI/AAAAAAAAh20/gBFPeBDapREAwi3-10GzzY54j5_LSt5FgCLcBGAsYHQ/s1600/30.png?w=687&ssl=1)

Read the flag using cat command as shown in the image below :

![](https://i0.wp.com/1.bp.blogspot.com/-aMXwRFiKERg/Xe0ik4QrKfI/AAAAAAAAh24/8E9dR1aggBwx23NtLv-6QDGjAyqT4g1uQCLcBGAsYHQ/s1600/31.png?w=687&ssl=1)

VOILA!! We have completed the challenge.

**Author: Yash Saxena **an undergraduate student pursuing B. Tech in Computer science and engineering with a specialization in cybersecurity and forensics from DIT University, Dehradun.** Contact ****[here](https://www.linkedin.com/in/yash-saxena-412349161/)**.

The post [In Plain Sight:1: Vulnhub Walkthrough](https://www.hackingarticles.in/in-plain-sight1-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/38mGRkq