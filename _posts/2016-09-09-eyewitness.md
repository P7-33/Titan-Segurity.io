---
title: 'EyeWitness'
date: 2019-11-17T09:59:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-uk7RyI2pGFo/XbT0yqFyZmI/AAAAAAAAQvk/iMoL59n8htgsoV2B13bpj8oR-vMPV6CfgCNcBGAsYHQ/s640/EyeWitness.png)](https://1.bp.blogspot.com/-uk7RyI2pGFo/XbT0yqFyZmI/AAAAAAAAQvk/iMoL59n8htgsoV2B13bpj8oR-vMPV6CfgCNcBGAsYHQ/s1600/EyeWitness.png)

**EyeWitness - Tool To Take Screenshots Of Websites, Provide Some Server Header Info, And Identify Default Credentials If Possible**

  
EyeWitness is designed to take screenshots of websites provide some server header info, and identify [default credentials](https://www.kitploit.com/search/label/Default%20Credentials "default credentials") if known.  
EyeWitness is designed to run on Kali Linux. It will auto detect the file you give it with the -f flag as either being a text file with URLs on each new line, nmap xml output, or [nessus](https://www.kitploit.com/search/label/Nessus "nessus") xml output. The --timeout flag is completely optional, and lets you provide the max time to wait when trying to render and screenshot a web page.  
A complete usage guide which documents [EyeWitness](https://www.kitploit.com/search/label/EyeWitness "EyeWitness") features and its typical use cases is available here - [https://www.christophertruncer.com/eyewitness-usage-guide/](https://www.christophertruncer.com/eyewitness-usage-guide/ "https://www.christophertruncer.com/eyewitness-usage-guide/")  
[

](https://www.blogger.com/u/1/null)  
**Supported Linux Distros:**  

*   Kali Linux
*   Debian 7+ (at least stable, looking into testing) (Thanks to @themightyshiv)

**E-Mail:** EyeWitness \[@\] christophertruncer \[dot\] com  
  
**Setup:**  

1.  Navigate into the setup directory
2.  Run the setup.sh script

  
**Usage:**  

```
./EyeWitness.py -f filename --timeout optionaltimeout --open (Optional)
```

  
**Examples:**  

```
./EyeWitness -f urls.txt --web  
  
./EyeWitness -x urls.xml --timeout 8 --headless
```

  
**Docker**  
Now you can execute EyeWitness in a docker [container](https://www.kitploit.com/search/label/Container "container") and prevent you from install unnecessary dependencies in your host machine.  
**Note:** execute _docker run_ with the folder path in the host which hold your results (**/path/to/results**)  
**Note2:** in case you want to scan urls from a file, make sure you put it in the volume folder (if you put _urls.txt_ in _/path/to/results_, then the argument should be _\-f /tmp/EyeWitness/urls.txt_)  
  
**Usage**  

```
docker build --build-arg user=$USER --tag eyewitness .  
docker run \  
    --rm \  
    -it \  
    -e DISPLAY=$DISPLAY \                   # optional flag in order to use vnc protocol  
    -v /tmp/.X11-unix:/tmp/.X11-unix \      # optional flag in order to use vnc protocol  
    -v /path/to/results:/tmp/EyeWitness \  
    eyewitness \  
    EyeWitness_flags_and_input
```

  
**Example #1 - headless capturing**  

```
docker run \  
    --rm \  
    -it \  
    -v ~/EyeWitness:/tmp/EyeWitness \  
    eyewitness \  
    --web \  
    --single [http://www.google.com](http://www.google.com/)
```

  
  

**[Download EyeWitness](http://eunsetee.com/mHv1 "Download EyeWitness")**

[![](https://2.bp.blogspot.com/-8mkUYkKhDy4/VZ3stV-VaPI/AAAAAAAAEWc/1K5lkHucNLg/s1600/Categories-applications-utilities-icon.png)](https://www.kitploit.com/ "Kitploit Home")

**  
Regards**

**Kang Asu**