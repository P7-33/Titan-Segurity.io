---
title: 'Learn from your attackers with a high interactivity SSH Honey Pot'
date: 2020-01-04T05:06:00+01:00
draft: false
---

> This post has been transferred from my old blog and was originally published on Monday 28th November 2016.

### Safety Advice

Remember running a Honey Pot is all about letting the bad guys in, therefore you’ll want to take steps to ensure the Honey Pot has no way of accessing your other systems. Remember it is solely your responsibility to ensure you secure your data and systems properly, and the author of this guide cannot be held responsible for any data loss or compromises you receive as a result of running a Honey Pot. Also bear in mind the attacker is likely to try and access stuff in the outside world or could try to use your Honey Pot to host content with legal implications, ensure you suitably firewall the front door to your Honey Pot also to just allow SSH access.

### Introduction

In a world of evolving and targeted cyber threats understanding your attacker’s intentions and tools has never been more crucial. By deliberately maintaining vulnerable systems, or Honey Pots, and letting the attackers in you can analyse their activity and gather intelligence so you can be ahead of the game if you ever have a compromise. When running an SSH Honey Pot you can gain a full log of the commands an attacker attempts to run on your system and any files which they attempt to download and can be a great way to obtain samples of malicious software for analysis or understand the techniques used by an attacker to scour your data.

### **Selecting a HoneyPot**

There are several different SSH Honey Pots out there which offer a variety of different features. These can be split in to low and high interactivity Honey Pots.

Low interactivity Honey Pots are fake SSH daemons which emulate an SSH shell, these are very easy to setup, and provides an SSH like experience however the system does not behave like a normal host and hence the attackers are normally very quick to identify and subsequently disconnect from low interactivity Honey Pots. Some low interactivity Honey Pots you can try out include Kippo ([https://github.com/desaster/kippo](https://github.com/desaster/kippo)) and Cowrie ([https://github.com/micheloosterhof/cowrie](https://github.com/micheloosterhof/cowrie)), both Honey Pots provide binary logs of the attackers SSH session which you can play back at a later date and also collection of any files the attacker fetches from the internet via wget or curl commands. You can graph interesting metrics in relation to the attackers sessions using the KippoGraph Web UI ([https://bruteforce.gr/kippo-graph](https://bruteforce.gr/kippo-graph)).

High interactivity Honey Pots are normally fully-fledged hosts that allow the attacker to do everything a user can do on any normal host via SSH. Because of this these hosts generally need a lot of TLC to keep them up and running as they soon get infected with malware, root kits and a variety of other tools of the trade. You also need to keep a close eye on them to ensure they are not able to access the outside world and become part of a bot net or perform any other illicit activities. These hosts are accessed via another host which acts as a gateway, essentially allowing you to perform a man in the middle attack on the SSH connection and obtain valuable data. The gateway host keeps binary logs of the attacker’s sessions for playback along with other stats about the Honey Pot. Although high interactivity Honey Pots sound a lot more complex to run they are generally not spotted by attackers and can collect much more meaningful data than low interactivity equivalents. The most widely used high interactivity Honey Pot is HonSSH by Thomas Nicholson ([https://github.com/tnich/honssh](https://github.com/tnich/honssh)).

This guide covers the installation of a high interactivity Honey Pot based on HonSSH and also shows you how to track and extract basic data from attacker’s sessions.

### Getting Started

First you’re going to need a couple of hosts, one to act as the HonSSH gateway and the other for the hacker to abuse, the hosts can be relatively modest as long as they are capable of running a Linux distribution and Python 2.7. For this guide I have chosen 2 cloud based virtual machines, if you go down the cloud route make sure you use a provider that allows private networks so you can setup the network accordingly. First arrange your physical hosts, or virtual hosts and virtual networks as follows…

![](https://www.robertputt.co.uk/learn-from-your-attackers-ssh-honeypot/)

Remember, the internal network between HonSSH and the Honey Pot should be used solely for the purpose of communication between the gateway and the Honey Pot, do not use your usual internal network else the attacker will have access to your internal hosts. Likewise, the HonSSH server should be connected directly to the internet, any private ranges in front of the HonSSH server prior to being natted to the internet will be accessible to the attacker. Once you have your hosts arranged in the topology as shown above install Linux. In the case of this guide Debian 8 has been used with its “minimal” flavour of install.

### **Configure HonSSH Server**

Please remember to substitute configuration values such as IP addresses with your own IPs. Using the IP address of my Honey Pot given below will not work.

First we will configure the HonSSH Gateway. SSH to the external IP of the host and login with the root user and the password you specified during installation, once logged in we will configure key based authentication for security and move the SSH server to a different port so the Honey Pot may listen on the usual SSH port.

```
$ ssh root@104.120.12.96 root@104.130.12.96's password: root@honssh:~# ssh-keygen Generating public/private rsa key pair. Enter file in which to save the key (/root/.ssh/id_rsa): Enter passphrase (empty for no passphrase): Enter same passphrase again: Your identification has been saved in /root/.ssh/id_rsa. Your public key has been saved in /root/.ssh/id_rsa.pub. The key fingerprint is: 59:be:ad:ca:48:71:5a:76:29:16:93:c1:cb:ba:37:3d root@honssh root@honssh:~# cat /root/.ssh/id_rsa.pub >> /root/.ssh/authorized_keys root@honssh:~# cat /root/.ssh/id_rsa -----BEGIN RSA PRIVATE KEY----- MIIEpQIBAAKCAQEAz8YFtJOtoRT0cjA1HKcjnRIh8AkfSYW1X1lQ90H6dKjUws8o VgwkbZcnd44r2Ot+gcs9LmboHwYdVSMk 4ibooQgZj5N+42IlimoiTS89g+9T1ZIv yj7Bv2pm1c7nUU0RR+Sq2rBYMMHfPfaC+Uu+iIPfR+TH5uXaqdP3YYk6jj5ZfoE+ ZdQckSwHHNmGsHDie7crJbCemQjYCQ+ sWHiSd1m3zFPoW2aeLWNYGTV5w1IkNvt3 ............+ziNzJg+lKHsWeVy3yOghOuI6BqUgdX5ZvfWS3U5EOuxGtoBibd4CQfxYoKQ gmZh8nAXYAaVumVZ62u+e erDAWcLp5gusyBh2jJdRoTZVbipNERBDF4= -----END RSA PRIVATE KEY-----
```

Take a copy of the private key block and logout of the SSH session. Paste the private key into a file on your local workstation and then reconnect to the HonSSH server using the private key.

```
$ ssh –i ~/honssh_privatekey root@104.120.12.96 root@honssh:~#
```

This time you should end up with a root shell on the host without entering any password. If this didn’t work repeat the steps from earlier to configure key based authentication. This is an important security step as password based authentication is inherently weak. Once you can login using your private key we should disable password based authentication and move the administrative SSH server to a different port.

```
root@honssh:~# sed -i 's/PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config root@honssh:~# sed -i 's/Port 22/Port 2222/g' /etc/ssh/sshd_config root@honssh:~# service sshd restart
```

Now disconnect from the SSH session and reconnect on port 2222. Then we will update the package manager cache and upgrade any outdated system packages. If this includes kernel packages make sure you perform a reboot after.

```
$ ssh –i ~/honssh_privatekey root@104.130.12.96 -p2222 root@honssh:~# apt-get update; apt-get upgrade root@honssh:~# reboot
```

Once the host has rebooted we can get to work configuring the HonSSH software. Install git, some essential Python packages and some required dependencies from the package manager, and then create and become a non-root user for HonSSH.

```
root@honssh:~# apt-get install git python python-dev python-pip libffi-dev libssl- dev libgeoip-dev mysql-client root@honssh:~# pip install virtualenv root@honssh:~# mkdir /home/honssh root@honssh:~# useradd honssh root@honssh:~# chown honssh:honssh /home/honssh root@honssh:~# su - honssh $ bash honssh@honssh:~$
```

Check out that latest HonSSH code from the GitHub repository and create a Python virtual environment to run the HonSSH daemon, enter the virtual environment and install HonSSH’s requirements.

```
honssh@honssh:~$ git clone https://github.com/tnich/honssh.git honssh@honssh:~$ virtualenv honssh_env honssh@honssh:~$ source ~/honssh_env/bin/activate (honssh_env) honssh@honssh:~$ pip install -r ~/honssh/requirements
```

Copy the sample configuration files into position.

```
(honssh_env) honssh@honssh:~$ cp ~/honssh/honssh.cfg.default ~/honssh/honssh.cfg (honssh_env) honssh@honssh:~$ cp ~/honssh/users.cfg.default ~/honssh/users.cfg
```

Edit the honssh.cfg file using your favourite editor, update the variables below accordingly.

```
(honssh_env) honssh@honssh:~$ vi ~/honssh/honssh.cfg
```

**Section / Variable**

**Value**

**Description**

honeypot / ssh\_addr

104.130.12.96

Internet facing IP address of HonSSH Gateway server.

honeypot / ssh\_port

2220

SSH Port for running the HonSSH server.

honeypot / client\_addr

0.0.0.0

Instructs HonSSH server to use default route to contact the Honey Pot.

honey-static / sensor\_name

my\_honeypot

Defines a friendly name for your Honey Pot.

honey-static / honey\_ip

172.20.0.1

The internal network IP for the Honey Pot.

honey-static / honey\_port

22

The port the Honey Pot’s SSH service listens on the internal network.

Leave all other variables blank or with their default value. If you want to use the extended functionality of HonSSH feel free to customise as required later.

Next SSH from the HonSSH server to the HoneyPot as root using the password you previously set when configuring the host. Next set the password to some value which is easy to guess for example ‘p455w0rd’ this will allow the attacker to gain access without trying too hard and then we can watch what they are up to.

```
(honssh_env) honssh@honssh:~$ ssh root@172.20.0.1 The authenticity of host '172.20.0.1 (172.20.0.1)' can't be established. ECDSA key fingerprint is 91:fb:67:8e:5d:68:76:67:23:30:bc:1e:59:78:92:77. Are you sure you want to continue connecting (yes/no)? yes Warning: Permanently added '172.20.0.1' (ECDSA) to the list of known hosts. root@172.20.0.1's password: root@honeypot:~# passwd Enter new UNIX password: Retype new UNIX password: passwd: password updated successfully root@honeypot:~#
```

Once completed disconnect from the HoneyPot SSH session to return to the HonSSH host. Change directory into the HonSSH folder and generate some keys for HonSSH to use for cryptography. Note when using ssh-keygen we override the default path with a relative file “id\_rsa” / “id\_dsa”.

```
(honssh_env) honssh@honssh:~$ cd honssh (honssh_env) honssh@honssh:~/honssh$ ssh-keygen Generating public/private rsa key pair. Enter file in which to save the key (/home/honssh/.ssh/id_rsa): id_rsa id_rsa already exists. Enter passphrase (empty for no passphrase): Enter same passphrase again: Your identification has been saved in id_rsa. Your public key has been saved in id_rsa.pub. The key fingerprint is: 85:11:45:f4:00:83:b6:d9:fb:d5:8a:56:23:a3:f9:81 honssh@honssh (honssh_env) honssh@honssh:~/honssh$ ssh-keygen -t dsa Generating public/private dsa key pair. Enter file in which to save the key (/home/honssh/.ssh/id_dsa): id_dsa Enter passphrase (empty for no passphrase): Enter same passphrase again: Your identification has been saved in id_dsa. Your public key has been saved in id_dsa.pub. The key fingerprint is: 64:5c:8f:3c:6d:fd:a9:b8:26:83:75:4c:f9:cb:af:16 honssh@honssh
```

Next start up the HonSSH server, this will start the server up and give a very verbose output, hopefully you should see something similar to the below…

```
(honssh_env) honssh@honssh:~/honssh$ twistd -y honssh.tac -p honssh.pid –n & 2016-05-10 19:53:01+0000 [-] Log opened. 2016-05-10 19:53:01+0000 [-] twistd 16.1.1 (/home/honssh/honssh_env/bin/python 2.7.9) starting up. 2016-05-10 19:53:01+0000 [-] reactor class: twisted.internet.epollreactor.EPollReactor. 2016-05-10 19:53:01+0000 [-] HonsshServerFactory starting on 2220 2016-05-10 19:53:01+0000 [-] Starting factory 2016-05-10 19:53:01+0000 [HonsshSlimClientTransport,client] [CLIENT] - Got SSH Version String: SSH-2.0-OpenSSH_6.7p1 Debian-5 2016-05-10 19:53:01+0000 [HonsshSlimClientTransport,client] Disconnecting with error, code 10 reason: user closed connection 2016-05-10 19:53:01+0000 [HonsshSlimClientTransport,client] connection lost 2016-05-10 19:53:01+0000 [HonsshSlimClientTransport,client] [HONSSH] - HonSSH Boot Sequence Complete - Ready for attacks! 2016-05-10 19:53:01+0000 [-] Stopping factory
```

Open a new terminal window and try SSHing to the HonSSH Gateway server on the listening port of HonSSH, hopefully you should get a connection, try logging in with the password you previously set on the Honey Pot host. Open a new terminal window and try SSHing to the HonSSH Gateway server on the listening port of HonSSH, hopefully you should get a connection, try logging in with the password you previously set on the Honey Pot host.

```
$ ssh root@104.130.12.96 -p2220 Warning: Permanently added '[104.130.12.96]:2220' (RSA) to the list of known hosts. root@104.130.12.96's password: The programs included with the Debian GNU/Linux system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright. Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law. Last login: Tue May 10 19:45:56 2016 from 172.20.0.3 root@honeypot:~#
```

Congratulations, this is your first connection to your Honey Pot, this is the same as what would happen with an attacker. Go back to your previous terminal window and issue an ls command, you should see a sessions directory, in here should be another directory with your sensor name as set in the configuration file. Within this directory are for each client IP which has connected and has a session on the Honey Pot, these directories contain log files for each session. Try catting out one of the logs so we can see what the user got up to.

```
(honssh_env) honssh@honssh:~/honssh$ cat sessions/my_honeypot/109.159.108.13/20160510_195912_678718.log 20160510_195912_678718 - [POT ] my_honeypot - 172.20.0.1:22 20160510_195912_678718 - [SSH ] Incoming Connection from 109.159.108.13:52630 - United Kingdom 20160510_195914_325358 - [SSH ] Login Successful: root:p455w0rd 20160510_195914_503284 - [TERM0] Opened Channel 20160510_195915_262392 - [TERM0] Command Executed: ls 20160510_195918_048578 - [TERM0] Command Executed: cd / 20160510_195918_368344 - [TERM0] Command Executed: ls 20160510_195919_461375 - [TERM0] Closed Channel 20160510_195919_466126 - [SSH ] Lost Connection with 109.159.108.13 (honssh_env) honssh@honssh:~/honssh$
```

However, configuration is sadly not complete, unfortunately SSH servers do not usually listen on port 2220 and you may have noticed that when you are connected to the Honey Pot you are unable to do anything with the internet, try a ping to a website. Also in the case of the Honey Pot above you may have noticed it’s host name is set to ‘honeypot’. It is likely with these tell-tale signs and strange configuration not many hackers will stumble across the host, and if they do they’ll probably quit our right away. Let’s get to work on fixing these items, leave the honssh user’s account on the HonSSH Gateway server and ensure you have a root shell.

```
(honssh_env) honssh@honssh:~/honssh$ exit root@honssh:~# whoami root
```

Next lets configure iptables to forward port 22 to 2220 on the host and also allow outbound nat for the Honey Pot to gain internet access, we also install the iptables persistence package to ensure the rules survive a reboot.

```
root@honssh:~# sed -i 's/#net.ipv4.ip_forward=1/net.ipv4.ip_forward=1/g' /etc/sysctl.conf root@honssh:~# sysctl –p root@honssh:~# echo 1 > /proc/sys/net/ipv4/ip_forward root@honssh:~# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE root@honssh:~# iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 22 -j REDIRECT --to-port 2220 root@honssh:~# apt-get install iptables-persistent
```

When asked if you’d like to save the current rules reply with “yes”. Your configuration is now complete. Remember if you want to login to the Honey Pot connect via Port 22, if you want to administer the gateway connect on port 2222, su to the honssh user and checkout the sessions directory if you want to see whats been going on on the Honey Pot.

You probably need to update a few items on the Honey Pot server to get the internet connectivity working and to set a more reasonable hostname. SSH to the Honey Pot and edit the /etc/network/interfaces file, add the default gateway to the eth0 block of the Honey Pot server.:: When asked if you’d like to save the current rules reply with “yes”. Your configuration is now complete. Remember if you want to login to the Honey Pot connect via Port 22, if you want to administer the gateway connect on port 2222, su to the honssh user and checkout the sessions directory if you want to see whats been going on on the Honey Pot.

You probably need to update a few items on the Honey Pot server to get the internet connectivity working and to set a more reasonable hostname. SSH to the Honey Pot and edit the /etc/network/interfaces file, add the default gateway to the eth0 block of the Honey Pot server.

```
root@honeypot:~# vi /etc/network/interfaces auto eth0 iface eth0 inet static address 172.20.0.1 gateway 172.20.0.3 netmask 255.255.255.0
```

Next edit the /etc/resolv.conf file to have some valid name servers and set the hostname to something more appropriate.

```
root@honeypot:~# vi /etc/resolv.conf nameserver 8.8.4.4 nameserver 8.8.8.8 root@honeypot:~# hostname web01.mywebsite.com root@honeypot:~# echo "web01.mywebsite.com" > /etc/hostname
```

### What Now?

Congratulations you now have an SSH Honey Pot listening on the internet, soon some attackers should start scanning your IP range and perform dictionary attacks as soon as they realise your running an SSH server with password authentication enabled. You should check back periodically and see if there were any active sessions and see what they have been up to, remember be highly suspicious of anything an attacker places on your Honey Pot host and take care when handling these files. It is likely from time to time you will need to rebuild the Honey Pot host as attackers are usually quite brutal with them, and you may also receive complaints from your ISP if an attacker starts doing bad stuff from your Honey Pot. In this case you should proactively manage all of these events. You can always put IPTables rules in place on the HonSSH server to ensure commonly abused outbound ports are limited, it’s also nice to run tcpdump on the HonSSH server so you can capture network traffic for analysis.

You may have noticed its rather cumbersome to collate and manage logs and session data via SSH to the HonSSH Gateway, you can make life a little easier by installing MySQL and configuring MySQL logging within the honssh.cfg file. You can then make some clever queries to make sense of the data.

Reply in the comments if you have any exciting findings from running your own Honey Pot, in the future I may publish another article covering more advanced analysis techniques for the Honey Pot.

### Further Help

If you require any further assistance checkout the HonSSH Docs at [https://docs.honssh.com](https://docs.honssh.com), if you discover a bug or have a feature request please raise an issue on the HonSSH Github repo [https://github.com/tnich/honssh/issues](https://github.com/tnich/honssh/issues).

  
  
from Hacker News https://ift.tt/2QHsX4k