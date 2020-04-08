---
title: 'Functrace'
date: 2019-12-13T23:20:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-POQVcR6-_kk/Xema1klnlDI/AAAAAAAARCQ/yOemClc_jbAmBgoc_vVno13Bxuuz32MHgCNcBGAsYHQ/s640/functrace_1_functrace.gif)](https://1.bp.blogspot.com/-POQVcR6-_kk/Xema1klnlDI/AAAAAAAARCQ/yOemClc_jbAmBgoc_vVno13Bxuuz32MHgCNcBGAsYHQ/s1600/functrace_1_functrace.gif)

**Functrace - A Function Tracer**

  
_functrace_ is a tool that helps to analyze a [binary](https://www.kitploit.com/search/label/Binary "binary") file with dynamic [instrumentation](https://www.kitploit.com/search/label/Instrumentation "instrumentation") using _DynamoRIO_ ([http://dynamorio.org/](http://dynamorio.org/ "http://dynamorio.org/")).  
These are some implemented features (based on DynamoRIO):

*   disassemble all the executed code
*   disassemble a specific function (dump if these are addresses)
*   get arguments of a specific function (dump if these are addresses)
*   get return value of a specific function (dump if this is an address)
*   monitors application signals
*   generate a report file
*   _ghidra_([https://ghidra-sre.org/](https://ghidra-sre.org/ "https://ghidra-sre.org/")) coverage script (based on the functrace report file)

  
  
**Setup**

```
$ wget [https://github.com/DynamoRIO/dynamorio/releases/download/release_7_0_0_rc1/DynamoRIO-Linux-7.0.0-RC1.tar.gz](https://github.com/DynamoRIO/dynamorio/releases/download/release_7_0_0_rc1/DynamoRIO-Linux-7.0.0-RC1.tar.gz)  
$ tar xvzf DynamoRIO-Linux-7.0.0-RC1.tar.gz
```

OR

```
$ wget [https://github.com/DynamoRIO/dynamorio/releases/download/cronbuild-7.91.18047/DynamoRIO-x86_64-Linux-7.91.18047-0.tar.gz](https://github.com/DynamoRIO/dynamorio/releases/download/cronbuild-7.91.18047/DynamoRIO-x86_64-Linux-7.91.18047-0.tar.gz)  
$ tar xvzf DynamoRIO-x86_64-Linux-7.91.18047-0.tar.gz
```

You can also clone and compile directly DynamoRIO

```
$ git clone [https://github.com/invictus1306/functrace](https://github.com/invictus1306/functrace)  
$ mkdir -p functrace/build  
$ cd functrace/build  
$ cmake .. -DDynamoRIO_DIR=/full_DR_path/cmake/  
$ make -j4
```

  
**Using functrace**

```
$ drrun -c libfunctrace.so -report_file report -- target_program [args]
```

  
**Options**  
The following _\[functrace\]_([https://github.com/invictus1306/functrace](https://github.com/invictus1306/functrace "https://github.com/invictus1306/functrace")) options are supported:

```
-disassembly                    -> disassemble all the functions   
-disas_func function_name       -> disassemble only the function function_name   
-wrap_function function_name    -> wrap the function function_name      
-wrap_function_args num_args    -> number of arguments of the wrapped function  
-cbr                            -> remove the bb from the cache (in case of conditional jump)  
-report_file file_name          -> report file name (required)  
-verbose                        -> verbose
```

  
**Simple usage**  
  
**Option _\-verbose_**

```
$ drrun -c libfunctrace.so -report_file report -verbose -- target_program [args]
```

  
**Option _\-disassemby_**

```
$ drrun -c libfunctrace.so -report_file report -disassembly -- target_program [args]
```

  
**Option _\-disas\_func_**

```
$ drrun -c libfunctrace.so -report_file report -disas_func name_function -- target_program [args]
```

  
**Option _\-wrap\_function_ and _\-wrap\_function\_args_**

```
$ drrun -c libfunctrace.so -report_file report -wrap_function name_function -wrap_function_args num_args -- target_program [args]
```

  
**Option _\-cbr_**

```
$ drrun -c libfunctrace.so -report_file report -cbr -- target_program [args]
```

  
**CVE-2018-4013 - [Vulnerability](https://www.kitploit.com/search/label/Vulnerability "Vulnerability") Analysis**  
A vulnerability on the [LIVE555 RTSP](http://www.live555.com/ "LIVE555 RTSP") server library. This is the [description](https://www.cvedetails.com/cve/CVE-2018-4013/ "description").  

[![](https://1.bp.blogspot.com/-2QpEKOpz_80/XemaprPlIHI/AAAAAAAARCM/XHdTNVdw2VYReykk8n1pMBQsahTYeKUCwCNcBGAsYHQ/s640/functrace_2_CVE-2018-4013.gif)](https://1.bp.blogspot.com/-2QpEKOpz_80/XemaprPlIHI/AAAAAAAARCM/XHdTNVdw2VYReykk8n1pMBQsahTYeKUCwCNcBGAsYHQ/s1600/functrace_2_CVE-2018-4013.gif)

  
**Working enviroment**  
Tested on Ubuntu 16.04.5 LTS 64 bit  
  
**Future features**

*   Ghidra plugin
*   Visual setup interface
*   Store and compare different coverage analysis
*   Run DR directy from ghidra
*   Add more functionality to functrace
*   Support for Android

  

**[Download Functrace](http://locinealy.com/iK2 "Download Functrace")**

**Regards**

**Kang Asu**