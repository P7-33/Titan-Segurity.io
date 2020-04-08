---
title: 'Blobrunner - Apace Debug Shellcode Extracted During Malware Analysis'
date: 2019-09-25T07:10:00+01:00
draft: false
---

[![](https://2.bp.blogspot.com/-fEwFCsTrs4M/W9hrORvXtEI/AAAAAAAANEI/XSYYAbtTaJceOIyF0j2WbMd6WBVFA_etgCLcBGAs/s640/BlobRunner_1_br.png)](https://2.bp.blogspot.com/-fEwFCsTrs4M/W9hrORvXtEI/AAAAAAAANEI/XSYYAbtTaJceOIyF0j2WbMd6WBVFA_etgCLcBGAs/s1600/BlobRunner_1_br.png)

  

BlobRunner is a uncomplicated tool to speedily debug shellcode extracted during [malware](http://www.kitploit.com/search/label/Malware) analysis.

BlobRunner allocates retentivity for the target file in addition to jumps to the base of operations (or offset) of the allocated memory. This allows an analyst to speedily debug into extracted artifacts amongst minimal overhead in addition to effort.

  

To role BlobRunner, you lot tin download the compiled executable from the [releases](https://github.com/OALabs/BlobRunner/releases) page or fix your ain using the steps below.

  
**Building**  
Building the executable is conduct forrad in addition to relatively painless.  
**Requirements**  

*   Download in addition to install Microsoft Visual C++ Build Tools or Visual Studio

**Build Steps**  

*   Open Visual Studio Command Prompt
*   Navigate to the directory where BlobRunner is checked out
*   Build the executable past times running:

```
cl blobrunner.c
```  
**Building BlobRunner x64**  
Building the x64 version is most the same equally above, but only uses the x64 tooling.  

*   Open x64 Visual Studio Command Prompt
*   Navigate to the directory where BlobRunner is checked out
*   Build the executable past times running:

```
 cl /Feblobrunner64.exe /Foblobrunner64.out blobrunner.c
```  
**Usage**  
To debug:  

*   Open BlobRunner inwards your favorite debugger.
*   Pass the shellcode file equally the offset parameter.
*   Add a breakpoint earlier the bound into the shellcode
*   Step into the shellcode

```
BlobRunner.exe shellcode.bin
```Debug into file at a specific offset.  
```
BlobRunner.exe shellcode.bin --offset 0x0100
```Debug into file in addition to don't recess earlier the jump. **Warning:** Ensure you lot convey a breakpoint laid earlier the jump.  
```
BlobRunner.exe shellcode.bin --nopause
```  
**Debugging x64 Shellcode**  
Inline assembly [isn't supported](https://msdn.microsoft.com/en-us/library/wbk4z78b.aspx) past times the x64 compiler, in addition to thence to back upwards debugging into x64 shellcode the loader creates a suspended thread which allows you lot to house a breakpoint at the thread entry, earlier the thread is resumed.  
  
**Remote [Debugging](http://www.kitploit.com/search/label/Debugging) Shell Blobs (IDAPro)**  
The procedure is most identical to debugging shellcode locally - amongst the exception that the you lot withdraw to re-create the shellcode file to the [remote](http://www.kitploit.com/search/label/Remote) system. If the file is copied to the same path you lot are running _win32\_remote.exe_ from, you lot exactly withdraw to role the file mention for the parameter. Otherwise, you lot volition withdraw to specify the path to the shellcode file on the remote system.  
  
**Shellcode Samples**  
You tin speedily generate shellcode samples using the [Metasploit](http://www.kitploit.com/search/label/Metasploit) tool [msfvenom](https://github.com/rapid7/metasploit-framework/wiki/How-to-use-msfvenom).  
Generating a uncomplicated [Windows](http://www.kitploit.com/search/label/Windows) exec payload.  
```
msfvenom -a x86 --platform windows -p windows/exec cmd=calc.exe -o test2.bin
```  
**Feedback / Help**  

*   Any questions, comments or requests you lot tin detect us on twitter: @seanmw or @herrcore
*   Pull requests welcome!

  
  

**[Download BlobRunner](https://github.com/OALabs/BlobRunner)**