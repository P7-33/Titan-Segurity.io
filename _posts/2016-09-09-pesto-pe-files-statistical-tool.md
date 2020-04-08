---
title: 'PESTO - PE (files) Statistical Tool'
date: 2019-11-08T00:24:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-7_qXa_M5ZJE/XbJWcGYrl8I/AAAAAAAAQqo/z7huspi99jM6bw2tJkgzfUPCWORNmFqkACNcBGAsYHQ/s1600/PESTO.png)](https://1.bp.blogspot.com/-7_qXa_M5ZJE/XbJWcGYrl8I/AAAAAAAAQqo/z7huspi99jM6bw2tJkgzfUPCWORNmFqkACNcBGAsYHQ/s1600/PESTO.png)

**PESTO - PE (files) Statistical Tool**

  

  
PESTO is a Python script that extracts and saves in a database some PE file security characteristics or flags searching for every PE [binary](https://www.kitploit.com/search/label/Binary "binary") in a whole directory, and saving results in a database.  
It checks for architecture flag in the header, and for the following security flags: ASLR, NO\_SEH, [DEP](https://www.kitploit.com/search/label/DEP "DEP") and CFG. Code is clear enough to modify flags and formats to your own needs.  
More details and flag explanation in here: [https://www.slideshare.net/elevenpaths/anlisis-del-nivel-proteccin-antiexploit-en-windows-10](https://www.slideshare.net/elevenpaths/anlisis-del-nivel-proteccin-antiexploit-en-windows-10 "https://www.slideshare.net/elevenpaths/anlisis-del-nivel-proteccin-antiexploit-en-windows-10")

[](https://www.blogger.com/u/1/null)  
**Functionality**  
The script just needs a path and a tag. The program will go through the path and subdirectories searching for .DLL and .EXE files and extracting the flags in the PE header (thanks to PEfile python library).  
The program requires a tag that will be used as a suffix for logs and database filenames, so different [analysis](https://www.kitploit.com/search/label/Analysis "analysis") can be done in the same directory.  
The information provided by the script is:

*   Percentage of .DLL and .EXE files with i386, AMD64, IA64 or other architecture.
*   Percentage of ASLR, NO\_SEH, DEP and CFG flags enabled or disabled in the headers.
*   After finishing the analysis it will prompt to export results in a SQL or CSV format.

It will create as well a .db file which is a [sqlite](https://www.kitploit.com/search/label/SQLite "sqlite") file with the information collected.  
  
**Related tools**

*   [https://github.com/olliencc/WinBinaryAudit](https://github.com/olliencc/WinBinaryAudit "https://github.com/olliencc/WinBinaryAudit")
*   [https://blog.netspi.com/verifying-aslr-dep-and-safeseh-with-powershell/](https://blog.netspi.com/verifying-aslr-dep-and-safeseh-with-powershell/ "https://blog.netspi.com/verifying-aslr-dep-and-safeseh-with-powershell/")
*   [https://github.com/angelorighi/pescheck/blob/master/pescheck.py](https://github.com/angelorighi/pescheck/blob/master/pescheck.py "https://github.com/angelorighi/pescheck/blob/master/pescheck.py")

  

**[Download PESTO](http://eunsetee.com/idZd "Download PESTO")**

**Regards**

**Kang Asu**