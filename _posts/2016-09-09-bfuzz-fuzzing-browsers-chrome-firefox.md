---
title: 'Bfuzz - Fuzzing Browsers (Chrome & Firefox)'
date: 2019-09-25T08:46:00+01:00
draft: false
---

[![](https://2.bp.blogspot.com/-DXigdVTItaQ/W9iTcvyomRI/AAAAAAAANFA/WnILAdkT9fEmk3FB1S7670SEtfrozispwCLcBGAs/s640/Bfuzz.png)](https://2.bp.blogspot.com/-DXigdVTItaQ/W9iTcvyomRI/AAAAAAAANFA/WnILAdkT9fEmk3FB1S7670SEtfrozispwCLcBGAs/s1600/Bfuzz.png)

  

BFuzz is an input based fuzzer tool which accept `.html` equally an input, open's upwards your browser amongst a novel representative in addition to top multiple testcases generated past times domato which is acquaint inwards `recurve` folder of BFuzz, to a greater extent than over BFuzz is an [automation](http://www.kitploit.com/search/label/Automation) which performs same chore repeatedly.

  
**Run BFuzz**  
```
warmachine@ftw: /BFuzz$ ./generate.sh warmachine@ftw: /BFuzz$ python BFuzz.py  Enter the browser type:  1: Chrome   2: Firefox >>
```Running `python BFuzz.py` volition enquire for selection weather condition to fuzz Chrome or Firefox, soundless if selected `2` this volition opened upwards [firefox](http://www.kitploit.com/search/label/Firefox) `firefox --new-instance` in addition to randomly opened upwards whatever of the testcase from `recurve` practise the logs on the finally await for `3 seconds` over again it volition opened upwards firefox in addition to the same procedure proceed so on.  
BFuzz is a pocket-size `.py` script which enable's to opened upwards browser run testcase for `12 seconds` so closed await for `3 seconds` in addition to over again follow the same process.  
  
**Domato**  
The testcase's inwards `recurve` are generated past times [domato](https://github.com/googleprojectzero/domato) generator.py contains the primary script. It uses grammar.py equally a library in addition to contains additional helper code for DOM fuzzing.  
grammar.py contains the generation engine that is to a greater extent than oftentimes than non application-agnostic in addition to tin so live on used inwards other (i.e. non-DOM) generation-based fuzzers. As it tin live on used equally a library, its usage is described inwards a dissever department below.  
.txt files comprise grammer definitions. There are iii primary files, html.txt, css.txt in addition to js.txt which comprise HTML, CSS in addition to JavaScript grammars, respectively. These root grammer files may include content from other files.  
  
**Bug showcase**  
Epiphany Web 3.28.1: [CVE-2018-11396](https://bugzilla.gnome.org/show_bug.cgi?id=795740)  
Mozilla Firefox: Stack based [buffer overflow](http://www.kitploit.com/search/label/Buffer%20Overflow) põrnikas ID: 1456083 \[Went DUPLICATE\]  
  
**View inwards action**  
  

  
  

**[Download BFuzz](https://github.com/RootUp/BFuzz)**