---
title: 'Frida-Wshook - Script Analysis Tool Based On Frida.Re'
date: 2019-09-25T08:06:00+01:00
draft: false
---

[![](https://2.bp.blogspot.com/-hRHqvnrIRMM/W9aG_Q0tAHI/AAAAAAAANDg/z_gZCgDnJ0g8Qs1ul1WV_CX7KYxy5t4fQCLcBGAs/s640/frida.png)](https://2.bp.blogspot.com/-hRHqvnrIRMM/W9aG_Q0tAHI/AAAAAAAANDg/z_gZCgDnJ0g8Qs1ul1WV_CX7KYxy5t4fQCLcBGAs/s1600/frida.png)

  

frida-wshook is an [analysis](http://www.kitploit.com/search/label/Analysis) as well as instrumentation tool which uses [frida.re](https://www.frida.re/) to [hook](http://www.kitploit.com/search/label/Hook) mutual functions oftentimes used past times malicious script files which are run using [WScript](https://technet.microsoft.com/en-us/library/hh875526(v=ws.11).aspx)/[CScript](https://technet.microsoft.com/en-us/library/bb490887.aspx).

The tool intercepts [Windows](http://www.kitploit.com/search/label/Windows) API functions as well as doesn't implement role stubs or proxies inside the targeted scripting language. This allows it to back upwards analyzing a few dissimilar script types such as:

*   .js ([JScript](https://en.wikipedia.org/wiki/JScript))
*   .vbs ([VBScript](https://en.wikipedia.org/wiki/VBScript))
*   .wsf ([WSFile](https://msdn.microsoft.com/en-us/library/ms995854.aspx)) (Initial support/testing. - Does non back upwards specific jobs)

By default script files are run using cscript.exe as well as volition output:

*   COM ProjIds
*   DNS Requests
*   Shell Commands
*   Network Requests

**Warning!!! Ensure that yous run whatever malicious [scripts](http://www.kitploit.com/search/label/Scripts) on a dedicated analysis system.** Ideally, a VM alongside snapshots then yous tin revert if a script gets away from yous as well as yous demand to reset the system.

Although mutual methods convey been hooked, Windows provides numerous APIs which let developers to interact alongside a network, file organization as well as execute commands. So it is exclusively possible to meet scripts leveraging uncommon APIs for these functions.

  
**Install & Setup**  

*   Install [Python 2.7](https://www.python.org/downloads/windows/)
*   Install the [Frida](https://pypi.python.org/pypi/frida) python bindings using pip

```
pip install frida
```

*   Clone (or download) the frida-wshook repository.

  
**Supported OS**  
frida-wshook has been tested on Windows 10 as well as Windows seven as well as _should_ piece of work on whatever Windows seven + environment. On x64 systems CScript is loaded from the C:\\Windows\\SysWow64 directory.  
It _may_ piece of work on WindowsXP, but I suspect that CScript may exercise the legacy API calls as well as would bypass the instrumentation.  
  
**Usage**  
The script supports a discover of optional [commandline](http://www.kitploit.com/search/label/Commandline) arguments that let yous to command what APIs the scripting host tin call.  
```
usage: frida-wshook.py [-h] [--debug] [--disable_dns] [--disable_com_init]                        [--enable_shell] [--disable_net]                        script  frida-wshook.py your friendly WSH Hooker  positional arguments:   script              Path to target .js/.vbs file  optional arguments:   -h, --help          exhibit this assistance message as well as move   --debug             Output debug information   --disable_dns       Disable DNS Requests   --disable_com_init  Disable COM Object Id Lookup   --enable_shell      Enable Shell Commands   --disable_net       Disable Network Requests
```Analyze a script alongside the default parameters:  
```
python wshook.py bad.js
```Enable verbose debugging:  
```
python wshook.py --debug bad.js
```Enable musical rhythm out (execute) commands:  
```
python frida-wshook.py --enable_shell bad.vbs
```Disable WSASend:  
```
python frida-wshook.py --disable_net bad.vbs
```Check what ProgIds the script uses:  
```
python frida-wshook.py --disable_com_init bad.vbs
```  
**Hooked Functions**  

*   ole32.dll
    *   [CLSIDFromProgIDEx](https://msdn.microsoft.com/en-us/library/windows/desktop/ms680113(v=vs.85).aspx)
*   Shell32.dll
    *   [ShellExecuteEx](https://msdn.microsoft.com/en-us/library/windows/desktop/bb762154(v=vs.85).aspx)
*   Ws2\_32.dll
    *   [WSASocketW](https://msdn.microsoft.com/en-us/library/windows/desktop/ms742212(v=vs.85).aspx)
    *   [GetAddrInfoExW](https://msdn.microsoft.com/en-us/library/windows/desktop/ms738518(v=vs.85).aspx)
    *   [WSASend](https://msdn.microsoft.com/en-us/library/windows/desktop/ms742203(v=vs.85).aspx)
    *   [WSAStartup](https://msdn.microsoft.com/en-us/library/windows/desktop/ms742213(v=vs.85).aspx)

  
**Known Issues**  

*   Network responses are non captured
*   Disabling Object Lookup tin drive the script to only output the commencement ProgId...Malware QA tin last lacking.
*   WSF files alongside a specific project to target currently isn't supported

  
**TODO**  

*   Change GetAddrInfoExW to exercise .replace instead of .attach
*   Add additional tracing as well as hooks to encompass to a greater extent than APIs
*   Look at bypassing mutual anti-analysis techniques constitute inward scripts (sleeps etc)
*   Update as well as ameliorate network asking hooking (ie: currently it captures requests, but non responses)

  
**Feedback / Help**  
Any questions, comments or requests yous tin discovery us on twitter: [@seanmw](https://twitter.com/herrcore) or [@herrcore](https://twitter.com/herrcore)  
  
  

**[Download Frida-Wshook](https://github.com/OALabs/frida-wshook)**