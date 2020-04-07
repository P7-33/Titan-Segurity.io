---
title: 'DC: 9: Vulnhub Walkthrough'
date: 2020-01-11T06:36:00+01:00
draft: false
---

In this article, we are going to crack the DC: 9 Boot to Root Challenge and present a detailed walkthrough. The machine depicted in this Walkthrough is hosted on Vulnhub. Credit for making this machine goes to [DCAU](https://twitter.com/DCAU7). Download this lab by clicking **[here](https://www.vulnhub.com/entry/dc-9,412/)**.

### **Penetration Testing Methodology**

*   **Network Scanning**
    *   Netdiscover Scan
    *   Nmap Scan
*   **Enumeration**
    *   Browsing HTTP Service
*   **Exploitation**
    *   Connection via SSH
*   **Post Exploitation**
    *   Enumeration for Sudo Permissions
*   **Reading Root Flag**

### **Walkthrough**

### **Network Scanning**

We downloaded, imported and ran the virtual machine (.ova file) on the VMWare Workstation, the machine will automatically be assigned an IP address from the network DHCP. To begin we will find the IP address of our target machine, for that use the following command as it helps to see all the IP’s in an internal network:

```
netdiscover
```

![](https://i1.wp.com/1.bp.blogspot.com/-tVYIfgbBPao/XhlYGboGfII/AAAAAAAAiKc/qUWWQxhQUo8J0_A0TjszOIzGK7qOe1P1QCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

We found the target’s IP Address 192.168.1.8. The next step is to scan the target machine by using the Nmap tool. This is to find the open ports and services on the target machine and will help us to proceed further.

```
nmap -A 192.168.1.8
```

![](https://i0.wp.com/1.bp.blogspot.com/-xcsaHROdUHQ/XhlYKbdHQEI/AAAAAAAAiLE/RZPibl4Kpn43xDnKcupY6VmWC2Nz61gUACLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

Here, we performed an Aggressive Port Scan because we wanted to grab all the information. After the scan, we saw that port 22 was detected but filtered, this says that we do have the SSH service but something is blocking it from the inside. We have the port 80 with the Apache httpd service. This was the lay of the land. Now let’s get to enumeration.

### **Enumeration**

We started from port 80 and tried to browse the webpage on our browser. With the history of the series of DC Machines, the Drupal CMS is used. But this was not Drupal. I must say there was some work done here to make the webpage look like one provided by the Drupal. Smart Move. We have the Home page depicted in the image given below. We also have the “Display All Records” tab, which consists record of some users. We have the Manage tab, but it requires some credentials to manage users.

![](https://i1.wp.com/1.bp.blogspot.com/-ipKb33l-jec/XhlYLv_W7II/AAAAAAAAiLU/3J4s5f157sQw7-G48I0jBChZGOWGaEu2ACLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

During our Enumeration, we didn’t find anything much to move ahead. We had a Form in the Search Tab. Forms are susceptible to Injection Attacks. To test for the SQL Injection on this search attack, we will search for some text inside the search form and capture the request by clicking on Search Button. We will capture the request using the BurpSuite Tool.

![](https://i1.wp.com/1.bp.blogspot.com/-tCwwxrUOv98/XhlYMEnEHfI/AAAAAAAAiLY/pjgiNHhbQqIcM8Y9zOXiqswpZH3HPfCVACLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

We copied the captured request and pasted in inside a text file and named it raj.txt. We did so to use the captured request with the sqlmap. Now we will start the sqlmap to check if the search form is vulnerable to SQL Injection or not. If it is vulnerable, this will enumerate some databases form this machine.

```
sqlmap -r raj.txt --dbs --batch
```

![](https://i1.wp.com/1.bp.blogspot.com/-v0I8AF0hOFQ/XhlYMPrqsFI/AAAAAAAAiLc/1VQHJZgqMkAU4gD1NbsU7i9iq_657PfGQCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

After working for some time, sqlmap told us that the search form is vulnerable. We see that the back-end DBMS configured is MySQL 5.0.12. We also see that some databases that are extracted by sqlmap. We have the **“information\_schema”**, **“Staff”** and **“user”** named databases.  Now let’s enumerate these databases, as sqlmap doesn’t allow multiple databases at the same time. We will enumerate the Staff Database first.

```
sqlmap -r raj.txt -D Staff --dump-all --batch
```

![](https://i0.wp.com/1.bp.blogspot.com/-E4dqtGt6x98/XhlYMseEGNI/AAAAAAAAiLg/lgaBh5Ri8ps3LIVHbDcg7YSkBpuzqS8vACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

The Staff Database contains 2 tables. First Table consists of email ids, phone numbers, First Name, Last Name and Positions of users and the Second Table consist of a username and a password hash. The username is “**admin**”. So, it hints at us that this might be an important account.

![](https://i1.wp.com/1.bp.blogspot.com/-fO_pFyYQCTw/XhlYMwsXt3I/AAAAAAAAiLo/NFbBKm9gNwwUhrnlhbkbc-Zl5Aw4EIeiQCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Before moving on with the hash cracking, let’s enumerate another database as well. The database named is users. We will again use the sqlmap in a similar way that we did earlier but change the database name against the -D parameter as depicted below.

```
sqlmap -r raj.txt -D users --dump-all --batch
```

After working on the enumeration, the sqlmap extracts a table named UserDetails from the user database. We have ids, First Names, Last Names, usernames, and passwords. This is important data that could be used further down the road. But let’s get back to our hash.

![](https://i0.wp.com/1.bp.blogspot.com/-KX_nLsZ9XNU/XhlYMwmS-RI/AAAAAAAAiLk/wy3lCY1jbuwdBAUHvELfWqjEIGikQOXlwCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

We went on our favorite hash cracker website, “[Hashkiller](https://hashkiller.co.uk/Cracker/MD5)”. We entered the hash and it told us that the hash is MD5 in nature. The cracked password is “**transorbital1**”.

![](https://i1.wp.com/1.bp.blogspot.com/-xy6kcbbCTpQ/XhlYNQFfV1I/AAAAAAAAiLs/9k3mw8FQofgd8qee0bDYcaaRHQGEyhsfwCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Now that we have the admin credentials, let’s look back at the Web Application that we were presented by the Machine. We had a Manage Tab which contains a login authentication page. We enter the credentials that we just cracked. We see that we have some additional features unlocked now like manage and Add Record. But what struck our eye was the footer. It now says that “File does not exist”. This means there must be a file that was being included to the footer which is now missing or misplaced. We know that where we have the include function, we have a probability of finding an LFI Vulnerability.

![](https://i1.wp.com/1.bp.blogspot.com/-m9H0KT_OEws/XhlYGi_0CTI/AAAAAAAAiKg/PrQ--6dQ-Mk4uLT1vH3i4tQtnV_RnbwKgCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

We try to test it using the most common LFI testing URL parameter. We insert the testing parameter in the URL followed by the welcome.php file. We do add “?file=” so that it can be pointed to a Local File on the Server. We try to look for the /etc/passwd file. We see that it is accessible. This proves that we do have the LFI Vulnerability.

```
http://192.168.1.8/welcome.php?file=../../../../../../../etc/passwd
```

![](https://i0.wp.com/1.bp.blogspot.com/-kd-8Iuwsu0Y/XhlYGWdKhjI/AAAAAAAAiKY/Nex3jPdFGVs0Z3pazyCSoe5nsO53uPQuACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

We started to enumerate different files on the Target Machine. This is when we stumbled upon the knockd.conf. This means that the is Port Knocking Involved. We see that we have the openSSH configured here with a sequence. We note this sequence and knock the SSH Port In this sequence to get it up and running.

```
http://192.168.1.8/welcome.php?file=../../../../../../../etc/knockd.conf
```

![](https://i0.wp.com/1.bp.blogspot.com/-PgLIxZYDEZY/XhlYHMxX8CI/AAAAAAAAiKk/cM3sPKl_zAYwxG1kEVU0v-DOtWdv9vHZACLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

### **Exploitation**

We use the knock command for the Port Knocking. This can be done by a bunch of different methods. After Knocking the ports in the sequence, we ran the NMAP scan again to ensure that our knocking worked and SSH Port should be open now. We have the SSH port open. This is our way in.

```
knock 192.168.1.8 7469 8475 9842  
nmap -p22 192.168.1.8
```

![](https://i1.wp.com/1.bp.blogspot.com/-TDNnposNewA/XhlYHS9429I/AAAAAAAAiKo/-EqXU6O88XIA3vT83xECTVYGblCR2aH9wCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

Now that we have the SSH service, we need login credentials to get inside. We tried the same credentials that we used on WebApp but it was a no go. We went back to the user database that we enumerated earlier and made 2 dictionaries for the bruteforce of the SSH Service. We used the usernames and passwords columns form that table for this procedure.

After creating the user.txt and pass.txt dictionaries, we used the hydra tool for the bruteforce against the SSH service on the Target Machine. After some tries, we see that the user janitor is the user with the SSH Access. We now have the proper credentials to login via SSH.

```
hydra -L user.txt -P pass.txt 192.168.1.8 ssh
```

![](https://i0.wp.com/1.bp.blogspot.com/-jCR6eAQiiTo/XhlYHip9HxI/AAAAAAAAiKs/bno5ajOTja4NoJgR8npzFA-svW2OEMmJACLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

We logged in using the following credentials.

**Username: janitor**

**Password: Ilovepeepee**

After logging in we being our Enumeration of the Machine for steps through which we can elevate our access on the machine. In the process of Enumeration, we ran the Directory Listing command, and we see that we have a hidden directory labeled “**secrets-for-putin**”.

```
ssh janitor@192.168.1.8  
Ilovepeepee  
ls -al
```

![](https://i2.wp.com/1.bp.blogspot.com/-VLajXmhhIAE/XhlYIB997EI/AAAAAAAAiKw/aORP1tjq714WC9hYdU3WJ8ryQg4B2X-ZQCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

We traversed inside the newly found hidden directory using the cd command. We again list all the contents inside this directory to find a text file named “**passwords-found-on-post-it-notes.txt**”. More Passwords, Cool! We read this text file using the cat command.

![](https://i0.wp.com/1.bp.blogspot.com/-zeVN-soVuvM/XhlYINEMuqI/AAAAAAAAiK0/NX72-ssft1Un0lc2LdTmSBv6dfx_jaXpwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

We went back to our native terminal and edited the pass.txt file and appended it with this newly found passwords. Now with recent developments, we ran the hydra bruteforce again. This time we see that we have some additional valid login credentials.

![](https://i0.wp.com/1.bp.blogspot.com/-_arTU43UnNI/XhlYIS1J4-I/AAAAAAAAiK4/ryPQVjMh7gcut90wzpB2AEnqefQ3ox9pwCLcBGAsYHQ/s1600/17.png?w=687&ssl=1)

### **Post Exploitation**

Let’s login using the first credential we found. It was the user fredf. We used the su command on the previous SSH session we had using the following credentials.

**Username: fredf**

**Password: B4-Tru3-001**

After logging in as the user fredf, we check if what kind of sudo rights does this fredf user have? We see that it can run a program called **test** as a root user without entering any password. We ran the test program but nothing happened.

```
su fredf  
B4-Tru3-001  
sudo -l
```

![](https://i2.wp.com/1.bp.blogspot.com/-EADCMVSgQ4Q/XhlYJcWEOhI/AAAAAAAAiK8/OeynUEBw-0493qwLIceU6scNeOjXZ_OXQCLcBGAsYHQ/s1600/18.png?w=687&ssl=1)

To inspect what went wrong, we went to the location where we see that the test is saved. We found the test.py. On taking a closer look we see that it is a simple data append program. It will take 2 files as parameters and then append the contents of the first file inside the second file.

```
cd /opt/devstuff/  
ls -al  
cat test.py
```

![](https://i0.wp.com/1.bp.blogspot.com/-f9bN0NOAwKI/XhlYJ4obpgI/AAAAAAAAiLA/j_cgEpe8qSg1o7CFXdRmDWqlb87u1DQ1ACLcBGAsYHQ/s1600/19.png?w=687&ssl=1)

### **Privilege Escalation**

Now to escalate privileges, we thought that we will create a new user with root access and make the entry of the user inside the /etc/passwd file using the test file. Let’s create a user and its password hash. We accomplish this task using openssl. Here we created a user named pavan with the password 123456. We get our hash, let’s move on to the target machine.

```
openssl passwd -1 -salt pavan 123456
```

![](https://i1.wp.com/1.bp.blogspot.com/-WWplg3-JRc8/XhlYKkJN7oI/AAAAAAAAiLI/jexnrtyJf2oxDWzKsQh3XLfPla31RbN8QCLcBGAsYHQ/s1600/20.png?w=687&ssl=1)

We add username, colons (:), and “:0:0::” to make the entry that could act as a root user. After that, we used the echo command to create a file named in the  /tmp directory named raj. Then we used the test program that we found earlier with the raj file and appended that user hash that we just created inside the /etc/passwd file. After this we login in as the user pavan that we created. We enter the password and we have the root access on the machine.

```
echo 'pavan:$1$pavan$qv9M3fBmtDPrOTBZflNl81:0:0::/root:/bin/bash' >> /tmp/raj  
sudo test /tmp/raj /etc/passwd  
su pavan
```

![](https://i1.wp.com/1.bp.blogspot.com/-aC1ztTANi94/XhlYLHQxNPI/AAAAAAAAiLM/dSCvZ491cwIxtfG5mUQnYIIRHIW0IkiHwCLcBGAsYHQ/s1600/21.png?w=687&ssl=1)

### **Accessing the Root Flag**

We moved to the home of the root user and found the final root flag. This was a nice machine. We enjoyed every bit of it. We are sad to see this nice series come to end. But we thank the author for putting so much effort into our learning. 

![](https://i1.wp.com/1.bp.blogspot.com/-PEjuWwM93mg/XhlYLavwDSI/AAAAAAAAiLQ/VJaoYnXskdY0v6qveM0SR4gtg1_5e1_hwCLcBGAsYHQ/s1600/22.png?w=687&ssl=1)

**Author: Pavandeep Singh** is a Technical Writer, Researcher and Penetration Tester. Can be Contacted on [Twitter](https://twitter.com/pavan2318) and [LinkedIn](https://www.linkedin.com/in/pavandeep-singh-6b1074132)

The post [DC: 9: Vulnhub Walkthrough](https://www.hackingarticles.in/dc-9-vulnhub-walkthrough/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/30bycNU