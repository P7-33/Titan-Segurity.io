---
title: 'Userrecon-Py v2.0'
date: 2019-10-25T06:15:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-fIEPHw_7Tjk/Xaanuq_BKQI/AAAAAAAABvo/HoemJ5r2Nn8RwV_dkc6ZebvzQkFpyPU9wCLcBGAsYHQ/s320/userrecon-py.png)](https://1.bp.blogspot.com/-fIEPHw_7Tjk/Xaanuq_BKQI/AAAAAAAABvo/HoemJ5r2Nn8RwV_dkc6ZebvzQkFpyPU9wCLcBGAsYHQ/s1600/userrecon-py.png)

**Userrecon-Py v2.0 - Username Recognition On Various Websites**

Username [recognition](https://www.kitploit.com/search/label/Recognition "recognition") on various websites.

  
**Installation**  
  
**With `pip3`**

```
# Linux  
sudo -H pip3 install git+[https://github.com/decoxviii/userrecon-py.git](https://github.com/decoxviii/userrecon-py.git) --upgrade  
userrecon-py --help
```

  
**Build from source**

```
# Linux  
git clone [https://github.com/decoxviii/userrecon-py.git](https://github.com/decoxviii/userrecon-py.git) ; cd userrecon-py  
sudo -H pip3 install -r requirements.txt  
python3 setup.py build  
sudo python3 setup.py install
```

  
**Usage**  
Start by printing the available actions by running `userrecon-py --help`. Then you can perform the following tests:

```
# print all results.  
userrecon-py target decoxviii --all -o test  
  
  
# print positive results.  
userrecon-py target decoxviii --positive -o test  
  
  
# print negative results.  
userrecon-py target decoxviii --negative  -o test
```

**decoxviii**  
**[MIT](https://github.com/decoxviii/userrecon-py/blob/master/LICENSE "MIT")**  
  

**[Download Userrecon-Py](http://eunsetee.com/VubQ "Download Userrecon-Py")**

**  
Regards**

**Kang Asu**