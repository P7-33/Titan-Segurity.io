---
title: 'AtomShields Cli'
date: 2019-11-09T00:25:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-ZpWxea7xaQs/XbJYeAg5bCI/AAAAAAAAQqw/HjbUOx2wH8Mkxfz7MZceW001V8aZvPLKgCNcBGAsYHQ/s640/AtomShields-cli.png)](https://asciinema.org/a/l87EfxU2e3eNpwQ9F8Sbhpk3q)

**AtomShields Cli - Security Testing Framework For Repositories And Source Code**

  

  
AtomShields Cli is a Command-Line Interface to use the software [AtomShields](https://github.com/ElevenPaths/AtomShields "AtomShields")  
  
**Installation**

```
pip install atomshieldscli
```

  
**Basic usage**

```
ascli --target --name 
```

The allowed _action_ values are:

*   **install**: To install a [checker](https://www.kitploit.com/search/label/Checker "checker") or a report, depending the context setted.
*   **uninstall**: To uninstall a checker or a report, depending the context setted.
*   **run**: To run the scan.
*   **show**: To show a checker list or a report list, depending the context setted.
*   **help**: Show the help

The allowed _context_ values are:

*   **checkers**: Operate with checkers
*   **reports**: Operate with reports

The _target_ option set the path to scan, or the [plugin](https://www.kitploit.com/search/label/Plugin "plugin") (checker/report) to install/uninstall.

[](https://www.blogger.com/u/1/null)  
**Show all checkers**

```
ascli show checkers
```

  
  
**Show all reports**

```
ascli show reports
```

  
  
**Install checker**

```
ascli install checkers --target path/to/file.py
```

  
  
**Install report**

```
ascli install reports --target path/to/file.py
```

  
  
**Uninstall checker**

```
ascli uninstall checkers --target path/to/file.py
```

or

```
ascli uninstall checkers --target checker_name
```

  
  
**Uninstall report**

```
ascli uninstall reports --target path/to/file.py
```

or

```
ascli uninstall reports --target checker_name
```

  
  
**Run the scan**

```
ascli run --target path/to/file.py --name repo_name
```

  

**[Download AtomShields-cli](http://eunsetee.com/idb9 "Download AtomShields-cli")**

**  
Regards**

**Kang Asu**