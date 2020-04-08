---
title: 'ThreadBoat'
date: 2019-10-10T21:54:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-H1r8lU96_1M/XZkDJrMefQI/AAAAAAAABt0/KyyzH_FgNSsQM4eFz5bn-e5-6TaUql0xQCLcBGAsYHQ/s320/ThreadBoat_1.gif)](https://1.bp.blogspot.com/-H1r8lU96_1M/XZkDJrMefQI/AAAAAAAABt0/KyyzH_FgNSsQM4eFz5bn-e5-6TaUql0xQCLcBGAsYHQ/s1600/ThreadBoat_1.gif)

**ThreadBoat - Program Uses Thread Execution Hijacking To Inject Native Shellcode Into A Standard Win32 Application**

Program uses Thread [Hijacking](https://www.kitploit.com/search/label/Hijacking "Hijacking") to Inject Native Shellcode into a Standard [Win32](https://www.kitploit.com/search/label/Win32 "Win32") Application.  
  
With Thread Hijacking, it allows the hijacker.exe program to suspend a thread within the target.exe program allowing us to write shellcode to a thread.  
[](https://www.blogger.com/u/1/null)

  

  
**Usage**

```
int main()  
{  
 System sys;  
 Interceptor incp;  
 Exception exp;  
  
 sys.returnVersionState();  
 if (sys.returnPrivilegeEscalationState())  
 {  
  std::cout << "Token Privileges Adjusted\n";  
 }  
   
 if (DWORD m_procId = incp.FindWin32ProcessId((PCHAR)m_win32ProcessName))  
 {  
  incp.ExecuteWin32Shellcode(m_procId);  
 }  
  
 system("PAUSE");  
 return 0;  
}
```

  
**Environment**

*   Windows Vista+
*   Visual C++

  
**Libs**

*    Winapi  
    *   user32.dll
    *   kernel32.dll
*    ntdll.dll

  

**[Download ThreadBoat](http://eunsetee.com/Nuuc "Download ThreadBoat")**

**Regards**

**Kang Asu**