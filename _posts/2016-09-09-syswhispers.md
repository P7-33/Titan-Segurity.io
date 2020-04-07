---
title: 'SysWhispers'
date: 2020-01-14T07:03:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-xanLwA3vWI4/XglohxJPYtI/AAAAAAAARUk/RghSqwDZSVEryymiArh3tPNB7nBIhghtQCNcBGAsYHQ/s640/Malware.jpg)](https://1.bp.blogspot.com/-xanLwA3vWI4/XglohxJPYtI/AAAAAAAARUk/RghSqwDZSVEryymiArh3tPNB7nBIhghtQCNcBGAsYHQ/s1600/Malware.jpg)

**SysWhispers - AV/EDR Evasion Via Direct System Calls**

  

  
SysWhispers helps with [evasion](https://www.kitploit.com/search/label/Evasion "evasion") by generating header/ASM files implants can use to make direct system calls.  
All core [syscalls](https://www.kitploit.com/search/label/Syscalls "syscalls") are supported from Windows XP to 10. Example generated files available in `example-output/`.  
  
**Introduction**  
Various security products place hooks in user-mode APIs which allow them to redirect execution flow to their engines and detect for suspicious behaviour. The functions in `ntdll.dll` that make the syscalls consist of just a few assembly instructions, so re-implementing them in your own implant can bypass the triggering of those security product hooks. This technique was popularized by [@Cn33liz](https://twitter.com/Cneelis "@Cn33liz") and his [blog post](https://outflank.nl/blog/2019/06/19/red-team-tactics-combining-direct-system-calls-and-srdi-to-bypass-av-edr/ "blog post") has more technical details worth reading.  
SysWhispers provides red teamers the ability to generate header/ASM pairs for any system call in the core kernel image (`ntoskrnl.exe`) across any Windows version starting from XP. The [headers](https://www.kitploit.com/search/label/Headers "headers") will also include the necessary type definitions.  
The main implementation difference between this and the [Dumpert](https://github.com/outflanknl/Dumpert "Dumpert") POC is that this doesn't call `RtlGetVersion` to query the OS version, but instead does this in the assembly by querying the PEB directly. The benefit is being able to call one function that supports multiple Windows versions instead of calling multiple functions each supporting one version.  
  
  
**Installation**  

```
> git clone [https://github.com/jthuraisamy/SysWhispers.git](https://github.com/jthuraisamy/SysWhispers.git)  
> cd SysWhispers  
> pip3 install -r .\requirements.txt  
> py .\syswhispers.py --help
```

  
**Usage and Examples**  
  
**Command Lines**  

```
# Export all functions with compatibility for all supported Windows versions (see example-output/).  
py .\syswhispers.py --preset all -o syscalls_all  
  
# Export just the common functions with compatibility for Windows 7, 8, and 10.  
py .\syswhispers.py --preset common -o syscalls_common  
  
# Export NtProtectVirtualMemory and NtWriteVirtualMemory with compatibility for all versions.  
py .\syswhispers.py --functions NtProtectVirtualMemory,NtWriteVirtualMemory -o syscalls_mem  
  
# Export all functions with compatibility for Windows 7, 8, and 10.  
py .\syswhispers.py --versions 7,8,10 -o syscalls_78X
```

  
**Script Output**  
```
PS C:\Projects\SysWhispers> py .\syswhispers.py --preset common --out-file syscom  
  
  ,         ,       ,_ /_   .  ,   ,_    _   ,_   ,  
_/_)__(_/__/_)__/_/_/ / (__/__/_)__/_)__(/__/ (__/_)__  
      _/_                         /  
     (/                          /   @Jackson_T, 2019  
  
SysWhispers: Why call the kernel when you can whisper?  
  
Common functions selected.  
  
Complete! Files written to:  
        syscom.asm  
        syscom.h
```  
**Before-and-After Example of Classic `CreateRemoteThread` DLL Injection**  
```
py .\syswhispers.py -f NtAllocateVirtualMemory,NtWriteVirtualMemory,NtCreateThreadEx -o syscalls
```

```
#include   
  
void InjectDll(const HANDLE hProcess, const char* dllPath)  
{  
    LPVOID lpBaseAddress = VirtualAllocEx(hProcess, NULL, strlen(dllPath), MEM_COMMIT | MEM_RESERVE, PAGE_READWRITE);  
    LPVOID lpStartAddress = GetProcAddress(GetModuleHandle(L"kernel32.dll"), "LoadLibraryA");  
   
    WriteProcessMemory(hProcess, lpBaseAddress, dllPath, strlen(dllPath), nullptr);  
    CreateRemoteThread(hProcess, nullptr, 0, (LPTHREAD_START_ROUTINE)lpStartAddress, lpBaseAddress, 0, nullptr);  
}
```

```
#include   
#include "syscalls.h" // Import the generated header.  
  
void InjectDll(const HANDLE hProcess, const char* dllPath)  
{  
    HANDLE hThread = NULL;  
    LPVOID lpAllocationStart = nullptr;  
    SIZE_T szAllocationSize = strlen(dllPath);  
    LPVOID lpStartAddress = GetProcAddress(GetModuleHandle(L"kernel32.dll"), "LoadLibraryA");  
   
    NtAllocateVirtualMemory(hProcess, &lpAllocationStart, 0, (PULONG)&szAllocationSize, MEM_COMMIT | MEM_RESERVE, PAGE_READWRITE);  
    NtWriteVirtualMemory(hProcess, lpAllocationStart, (PVOID)dllPath, strlen(dllPath), nullptr);  
    NtCreateThreadEx(&hThread, GENERIC_EXECUTE, NULL, hProcess, lpStartAddress, lpAllocationStart, FALSE, 0, 0, 0, nullptr);  
}
```

  
**Common Functions**  
Using the `--preset common` switch will create a header/ASM pair with the following functions:  
  
  
  
Click to expand function list.  
**Importing into Visual Studio**  

1.  Copy the generated H/ASM files into the project folder.
2.  In Visual Studio, go to _Project_ → _Build Customizations..._ and enable MASM.
3.  In the _Solution Explorer_, add the .h and .asm files to the project as header and source files, respectively.
4.  Go to the properties of the ASM file, and set the _Item Type_ to _Microsoft Macro Assembler_.
5.  Ensure that the project platform is set to x64. 32-bit projects are not supported at this time.

  
**Caveats and Limitations**  

*   Only 64-bit Windows is supported at this time.
*   System calls from the graphical subsystem (`win32k.sys`) are not supported.
*   Tested on Visual Studio 2019 (v142) with Windows 10 SDK.

  
**Troubleshooting**  

*   `ModuleNotFoundError` in Python script.
    *   Ensure that the required modules are installed with `pip3 install -r requirements.txt`.
*   Type redefinitions errors: a project may not compile if typedefs in `syscalls.h` have already been defined.
    *   Ensure that only required functions are included (i.e. `--preset all` is rarely necessary).
    *   If a typedef is already defined in another used header, then it could be removed from `syscalls.h`.

  
**Credits**  
This script was developed by [@Jackson\_T](https://twitter.com/Jackson_T "@Jackson_T") but builds upon the work of many others:  

*   [@j00ru](https://twitter.com/j00ru "@j00ru") for maintaining syscall numbers in machine-readable formats.
*   [@FoxHex0ne](https://twitter.com/FoxHex0ne "@FoxHex0ne") for cataloguing many function prototypes and typedefs in a machine-readable format.
*   [@PetrBenes](https://twitter.com/PetrBenes "@PetrBenes"), [NTInternals.net team](https://undocumented.ntinternals.net/ "NTInternals.net team"), and [MSDN](https://docs.microsoft.com/en-us/windows/ "MSDN") for additional prototypes and typedefs.
*   [@Cn33liz](https://twitter.com/Cneelis "@Cn33liz") for the initial [Dumpert](https://github.com/outflanknl/Dumpert "Dumpert") POC implementation.

Special thanks to [@Dcept905](https://twitter.com/Dcept905 "@Dcept905") for testing and suggestions.  
  
**Related Articles and Projects**  

*   [@0x00dtm](https://twitter.com/0x00dtm "@0x00dtm"): [Userland API Monitoring and Code ](https://0x00sec.org/t/userland-api-monitoring-and-code-injection-detection/5565 "Userland API Monitoring and Code ")[Injection](https://www.kitploit.com/search/label/Injection "Injection") Detection
*   [@0x00dtm](https://twitter.com/0x00dtm "@0x00dtm"): [Defeating Userland Hooks (ft. Bitdefender)](https://0x00sec.org/t/defeating-userland-hooks-ft-bitdefender/12496 "Defeating Userland Hooks (ft. Bitdefender)") ([Code](https://github.com/NtRaiseHardError/Antimalware-Research/tree/master/Generic/Userland%20Hooking/AntiHook "Code"))
*   [@Cn33liz](https://twitter.com/Cneelis "@Cn33liz"): [Combining Direct System Calls and sRDI to bypass AV/EDR](https://outflank.nl/blog/2019/06/19/red-team-tactics-combining-direct-system-calls-and-srdi-to-bypass-av-edr/ "Combining Direct System Calls and sRDI to bypass AV/EDR") ([Code](https://github.com/outflanknl/Dumpert "Code"))
*   [@SpecialHoang](https://twitter.com/SpecialHoang "@SpecialHoang"): [Bypass EDR’s memory protection, introduction to hooking](https://medium.com/@fsx30/bypass-edrs-memory-protection-introduction-to-hooking-2efb21acffd6 "Bypass EDR’s memory protection, introduction to hooking") ([Code](https://github.com/hoangprod/AndrewSpecial/tree/master "Code"))
*   [@xpn](https://twitter.com/_xpn_ "@xpn") and [@domchell](https://twitter.com/domchell "@domchell"): [Silencing Cylance: A Case Study in Modern EDRs](https://www.mdsec.co.uk/2019/03/silencing-cylance-a-case-study-in-modern-edrs/ "Silencing Cylance: A Case Study in Modern EDRs")
*   [@mrjefftang](https://twitter.com/mrjefftang "@mrjefftang"): [Universal Unhooking: Blinding Security Software](https://threatvector.cylance.com/en_us/home/universal-unhooking-blinding-security-software.html "Universal Unhooking: Blinding Security Software") ([Code](https://github.com/CylanceVulnResearch/ReflectiveDLLRefresher "Code"))
*   [@spotheplanet](https://twitter.com/spotheplanet "@spotheplanet"): [Full DLL Unhooking with C++](https://ired.team/offensive-security/defense-evasion/how-to-unhook-a-dll-using-c++ "Full DLL Unhooking with C++")
*   [@hasherezade](https://twitter.com/hasherezade "@hasherezade"): [Floki Bot and the stealthy dropper](https://blog.malwarebytes.com/threat-analysis/2016/11/floki-bot-and-the-stealthy-dropper/ "Floki Bot and the stealthy dropper")
*   [@hodg87](https://twitter.com/hodg87 "@hodg87"): [Latest Trickbot Variant has New Tricks Up Its Sleeve](https://www.cyberbit.com/blog/endpoint-security/latest-trickbot-variant-has-new-tricks-up-its-sleeve/ "Latest Trickbot Variant has New Tricks Up Its Sleeve")
*   [@hodg87](https://twitter.com/hodg87 "@hodg87"): [Malware Mitigation when Direct System Calls are Used](https://www.cyberbit.com/blog/endpoint-security/malware-mitigation-when-direct-system-calls-are-used/ "Malware Mitigation when Direct System Calls are Used")

  
  

**[Download SysWhispers](http://triabicia.com/3LLq "Download SysWhispers")**

**Regards**

**Kang Asu**