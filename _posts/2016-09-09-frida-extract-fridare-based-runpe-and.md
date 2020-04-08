---
title: 'Frida-Extract - Frida.Re Based Runpe (And Mapviewofsection) Extraction
Tool'
date: 2019-09-25T08:26:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-BVZ4PM2lz0I/W9aGCWAMdTI/AAAAAAAANDY/Hh_TSayIqlwYd8eIAfufy7bQkHPQ2HLigCLcBGAs/s640/frida.png)](https://1.bp.blogspot.com/-BVZ4PM2lz0I/W9aGCWAMdTI/AAAAAAAANDY/Hh_TSayIqlwYd8eIAfufy7bQkHPQ2HLigCLcBGAs/s1600/frida.png)

  

FridaExtract is a [Frida.re](http://www.frida.re/) based [RunPE](http://www.adlice.com/runpe-hide-code-behind-legit-process/) extraction tool. RunPE type [injection](http://www.kitploit.com/search/label/Injection) is a mutual technique used past times [malware](http://www.kitploit.com/search/label/Malware) to enshroud code inside to a greater extent than or less other process. It also happens to hold upwards the in conclusion phase inward a lot of [packers](http://www.kitploit.com/search/label/Packers) : )

NOTE: Frida directly also supports extraction of injected PE files using the "MapViewOfSection" technique best [described here](http://blog.w4kfu.com/tag/duqu).

Using FridaExtract yous tin automatically extract together with reconstruct a PE file that has been injected using the RunPE method... together with bypass these packers!

  

**Why Frida?**

There are tons of great tools that already extract RunPE injected code, FridaExtract is **not** amend than these. But it is easier to install, easier to build (lol), easier to run, together with easier to hack. No compilers, no build environments, only a uncomplicated "pip install" together with you're upwards together with running.

The code is specifically commented together with organized to human activity every bit a template for yous to build your ain Frida projects. This is to a greater extent than of a proof of concept that demonstrates how to setup hooks inward a [Windows](http://www.kitploit.com/search/label/Windows) environment. Please copy-paste-hack this whatsoever means yous like!

  

**Getting Started**

**Warning:** FridaExtract solely industrial plant nether Windows 32bit. There are currently to a greater extent than or less mystery bugs amongst wow64 therefore nosotros recommend sticking to Windows7 32bit or Windows Server 2008 32bit.

*   First commencement a VM (see alert above) if yous are going to hold upwards unpacking malware.
*   Install [Python 2.7](https://www.python.org/downloads/)
*   Remember to [set your python together with pip paths](http://docs.python-guide.org/en/latest/starting/install/win/) ; )
*   Install Frida past times typing `pip install frida` inward cmd
*   Clone this repository together with yous are attain to extract!

  

**Extracting PE Files**

FridaExtract is solely able to extract RunPE injected PE files therefore it is fairly limited. If yous are using a VM that is slow to snapshot-run-revert together with therefore yous tin only attempt FridaExtract blindly on every malware sample together with run across what comes out but nosotros don't recommend it. Instead, FridaExtract is proficient compliment to a [sandbox](http://www.kitploit.com/search/label/Sandbox) (we <3 [malwr](https://malwr.com/)). First run the sample inward a sandbox together with Federal Reserve notation the API calls.

For RunPE technique if yous run across the next API calls together with therefore FridaExtract may hold upwards the tool for you:

*   CreateProcess
*   WriteVirtualMemory (to remote process)
*   ResumeThread (in remote process)

For the MapViewOfSection technique if yous run across the next API calls together with therefore FridaExtract may hold upwards the tool for you:

*   CreateProcess
*   NtCreateSection
*   NtUnmapViewOfSection (remote process)
*   NtMapViewOfSection (remote process)

  
**Examples**  
By default FridaExtract volition attempt to automatically extract the injected PE file, reconstruct it, together with dump it to a file called `dump.bin`.  
```
python FridaExtract.py bad.exe
```  
**Dump To File**  
Influenza A virus subtype H5N1 dump file tin hold upwards specified using the `--out_file` command.  
```
python FridaExtract.py bad.exe --out_file extracted.exe
```  
**Pass Arguments**  
If the packed PE file yous are attempting to extract requires arguments yous tin top them using the `--args` command. Multiple arguments tin hold upwards passed every bit comma separated.  
```
python FridaExtract.py bad.exe --args password
```  
**Dump Raw**  
FridaExtract volition automatically attempt to reconstruct the dumped retentiveness into a PE file. If this isn't working together with yous only desire a raw dump of all retentiveness written to the subprocess yous tin purpose the `--raw` command. Instead of writing the reconstructed PE to the dump file the raw retentiveness segments volition hold upwards written inward companionship of address.  
```
python FridaExtract.py bad.exe --raw
```  
**Verbose**  
FridaExtract uses hooks on the next APIs to extract the injected PE file:  

*   ExitProcess
*   NtWriteVirtualMemory
*   NtCreateThread
*   NtResumeThread
*   NtDelayExecution
*   CreateProcessInternalW
*   NtMapViewOfSection
*   NtUnmapViewOfSection
*   NtCreateSection

To describe these APIs together with impress the results purpose the `-v` or `--verbose` command.  
```
python FridaExtract.py bad.exe --verbose
```  
**Caveats**  
Frida uses userland hooks that tin easily hold upwards bypassed. If yous involve a to a greater extent than robust DBI tool attempt PIN! Influenza A virus subtype H5N1 great event of using PIN to extract RunPE is provided past times [here](http://jbremer.org/malware-unpacking-level-pintool/).  
Frida injects a javascript runtime into the procedure yous are analyzing, it is **not** stealthy. For a decent overview of how Frida may hold upwards detected past times malware [check this out](https://crackinglandia.wordpress.com/2015/11/10/anti-instrumentation-techniques-i-know-youre-there-frida/).  
  
**Acknowledgments**  

*   Huge thank yous to @oleavr for helping me amongst my endless questions well-nigh Frida
*   Hat tip to @skier\_t for his awesome PE rebuilding script together with therefore much more!

  
**Feedback / Help**  

*   Any questions, comments, requests hitting us upwards on twitter: @herrcore or @seanmw
*   Anything Frida specific break us lurking on IRC: #frida at irc.freenode.net
*   Pull requests welcome!

  
  

**[Download Frida-Extract](https://github.com/OALabs/frida-extract)**