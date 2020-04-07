---
title: 'Examples of the ps command within Linux'
date: 2020-01-01T10:26:00+01:00
draft: false
---

Below are some examples of the ps command within Linux.  
  
ps -eH --forest | less  
  
This will list all processes (-e select all processes) and (-H hierarchy), as well as --forest includes ASCII lines.  
  

[![](https://1.bp.blogspot.com/-WtjOdrIXFLg/Xf-BKuIcRgI/AAAAAAAAGQU/qe-QSwV1_20Cry57i5SUJI8f_PFr1tQRACLcBGAsYHQ/s320/ps_1.png)](https://1.bp.blogspot.com/-WtjOdrIXFLg/Xf-BKuIcRgI/AAAAAAAAGQU/qe-QSwV1_20Cry57i5SUJI8f_PFr1tQRACLcBGAsYHQ/s1600/ps_1.png)

  
The -f switch is for full-format and will include more columns.  
  
ps -ef | less  
  

[![](https://1.bp.blogspot.com/-fWp-Elf_Xic/Xf-ByeF_PjI/AAAAAAAAGQc/Zo8TQPWc9fkMtFJ3L6zyeLSc-TlNi55ygCLcBGAsYHQ/s320/ps_2.png)](https://1.bp.blogspot.com/-fWp-Elf_Xic/Xf-ByeF_PjI/AAAAAAAAGQc/Zo8TQPWc9fkMtFJ3L6zyeLSc-TlNi55ygCLcBGAsYHQ/s1600/ps_2.png)

  
The -u switch returns data for a particular user.  
  
ps -u username | less  
  
The -sort switch allows the information to be sorted by columns.  
  
ps -e -o pcpu,args --sort -pcpu| less  
  

[![](https://1.bp.blogspot.com/-wxGAtIygfOw/Xf-C86Y-PpI/AAAAAAAAGQo/UvjmcuCY6H4Z0t9z0PLn3QFHQq0DKU3QwCLcBGAsYHQ/s320/ps_3.png)](https://1.bp.blogspot.com/-wxGAtIygfOw/Xf-C86Y-PpI/AAAAAAAAGQo/UvjmcuCY6H4Z0t9z0PLn3QFHQq0DKU3QwCLcBGAsYHQ/s1600/ps_3.png)

  
Pipe through the head command to see the ten most CPU intensive processes.  
  
ps -e -o pcpu,args --sort -pcpu | head -10