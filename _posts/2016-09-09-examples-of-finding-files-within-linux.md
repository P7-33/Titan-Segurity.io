---
title: 'Examples of finding files within Linux'
date: 2019-10-01T10:06:00+01:00
draft: false
---

Below are some examples of how to find files within Linux.  The **which** command returns the path of a command.  
  
which ping  
/bin/ping  
  
The **locate** command returns any file which contains the text.  To focus on a particular path, use the grep command as well.  The switch "-i" will specify locate to ignore case-sensitivity.  
  
locate chrome | grep /home/sam  
  
The **find** command is similar; it has several parameters such as:  
  
\-iname - file name  
\-mtime - modified time  
\-perm - permissions  
  
The example below looks for all files in the home directory that have been created or modified in the past seven days:  
  
find ~/ -mtime -7  
  
[https://distrowatch.com/weekly.php?issue=20190812](https://distrowatch.com/weekly.php?issue=20190812)