---
title: 'FockCache'
date: 2020-02-16T01:33:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-SkQM1nfSJwg/XjovATIucOI/AAAAAAAARn8/-xn29HldLKMtzq8Sb6ZGZy9-IhvYOlBTgCNcBGAsYHQ/s640/WKTlr2ffvL6CAISm7oSzSZCLe.png)](https://asciinema.org/a/WKTlr2ffvL6CAISm7oSzSZCLe)

**FockCache - Minimalized Test Cache Poisoning**

  
FockCache - Minimalized Test Cache Poisoning  
  
Detail For Cache [Poisoning](https://www.kitploit.com/search/label/Poisoning "Poisoning") : [https://portswigger.net/research/practical-web-cache-poisoning](https://portswigger.net/research/practical-web-cache-poisoning "https://portswigger.net/research/practical-web-cache-poisoning")  
  
**FockCache**  
FockCache tries to make cache poisoning by trying X-Forwarded-Host and X-Forwarded-Scheme [headers](https://www.kitploit.com/search/label/Headers "headers") on web pages.  
After successful result, it gives you a poisoned URL.  
[](https://www.blogger.com/u/7/null)

  

  
**To be added soon:**  
1 - Page Param Checker  
2 - Recursive Checking  
  
**Installation**  
1 - Install with installer.sh  
`chmod +x installer.sh`  
`./installer.sh`  
2 - Install manual  
`go get [github.com/briandowns/spinner](http://github.com/briandowns/spinner)`  
`go get [github.com/christophwitzko/go-curl](http://github.com/christophwitzko/go-curl)`  
`go run main.go --hostname victim.host`  
or  
`go build FockCache main.go`  
  
**Run**  
`./FockCache --hostname victim.host`  
  

**[Download Fockcache](http://whareotiv.com/oNo "Download Fockcache")**

**Regards**

**Kang Asu**