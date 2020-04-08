---
title: 'Brutality: A Fuzzer For Any GET Entries '
date: 2019-10-05T14:04:00+01:00
draft: false
---

**Brutalitys' Features**  

*   Multi-threading on demand.
*   Fuzzing, bruteforcing GET params.
*   Find admin panels.
*   Colored output.
*   Hide results by return code, word numbers.
*   Proxy support.
*   Big wordlist.

**Screenshots:**  

[![](https://1.bp.blogspot.com/-HWbx_30J58I/XZiUbWz-ZZI/AAAAAAAAO1g/_qrXy-ha-1YiUxux3jBZ-gZ6kvYvaqqrgCLcBGAsYHQ/s1600/Brutality.png)](https://1.bp.blogspot.com/-HWbx_30J58I/XZiUbWz-ZZI/AAAAAAAAO1g/_qrXy-ha-1YiUxux3jBZ-gZ6kvYvaqqrgCLcBGAsYHQ/s1600/Brutality.png)

[![](https://1.bp.blogspot.com/-nY-M1Q3aPoM/XZiUfVtmO9I/AAAAAAAAO1k/WRKP9E766Qo79OZvtECu2TTxK4rv8B0bQCLcBGAsYHQ/s1600/Brutality%2Bexploitation.png)](https://1.bp.blogspot.com/-nY-M1Q3aPoM/XZiUfVtmO9I/AAAAAAAAO1k/WRKP9E766Qo79OZvtECu2TTxK4rv8B0bQCLcBGAsYHQ/s1600/Brutality%2Bexploitation.png)

  
**Brutality's Installtion**  
  
**How to use Brutality?**  

  
**Examples:**  
   Use default wordlist with 5 threads (-t 5) and hide 404 messages (–e 404) to fuzz the given URL ([http://192.168.1.1/FUZZ](http://192.168.1.1/FUZZ)):  
`python brutality.py -u 'http://192.168.1.1/FUZZ' -t 5 -e 404`  
  
   Use common\_pass.txt wordlist (-f ./wordlist/common\_pass.txt), remove response with 6969 length (-r 6969) and proxy at 127.0.0.1:8080 (-p [http://127.0.0.1:8080](http://127.0.0.1:8080/)) to fuzz the given URL ([http://192.168.1.1/brute.php?username=admin&password=FUZZ&submit=submit#](http://192.168.1.1/brute.php?username=admin&password=FUZZ&submit=submit#)):  
`python brutality.py -u 'http://192.168.1.1/brute.php?username=admin&password=FUZZ&submit=submit#' -f ./wordlist/common_pass.txt -r 6969 -p http://127.0.0.1:8080`  
  
**ToDo List:**  

*   Smooth output.
*   Export file report.
*   Modularization.

  

[**Download Brutality**](https://github.com/ManhNho/brutality)