---
title: 'Book Review: "Black Hat Go"'
date: 2020-02-14T11:31:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-hpkJtjc7zWs/XkJsni-tbiI/AAAAAAAALTM/zZaTqNHdjdcfnbKqwgC6jF7wO-0LzD9XQCLcBGAsYHQ/s640/black_hat_go.jpg)](https://1.bp.blogspot.com/-hpkJtjc7zWs/XkJsni-tbiI/AAAAAAAALTM/zZaTqNHdjdcfnbKqwgC6jF7wO-0LzD9XQCLcBGAsYHQ/s1600/black_hat_go.jpg)

"Black Hat Go: Go Programming For Hackers and Pentesters" by Tom Steele, Chris Patten, and Dan Kottmann is the long awaited Go version of "Black Hat Python". Granted it's not the same authors but it is the same publisher and certainly captures the same feel. I think it was the long release time (2+ years since it's announcement) or that the community has already explored these topics, but this book felt really underwhelming to me. They take a breadth first approach in this book and demonstrate a ton of different computer security techniques in go. The book is kind of a mile wide and an inch deep in the sense that there are a lot of different examples but many of them don't go beyond the basic implementation of these ideas. I read [the book on Kindle](https://www.amazon.com/Black-Hat-Go-Programming-Pentesters-ebook/dp/B073NPY29N) for ~$25 at 368 pages, it was a long read but interesting none the less. I give it 6 out of 10 stars, for being a fairly basic intro to the go programming language and computer security. I recommend it to those looking for an intro to go through example, or those who enjoyed the format of Black Hat Python. The code is annotated in the same style as Black Hay Python, which is a credit to the publisher NoStarch Press, they really know how to produce a great programming book. It's also awesome that they make [all of the code available](https://github.com/blackhat-go/bhg) for free. Like I've always said with these books, just looking through the code is worth your time even if you don't read the book. That said, the following are the chapters of the book to help you understand its contents or navigate the code (which is divided by chapter):  
  
Chapter 1: Go Fundamentals  
Chapter 2: TCP, Scanners, and Proxies  
Chapter 3: HTTP Clients and Remote Interaction with Tools  
Chapter 4: HTTP Servers, Routing, and Middleware  
Chapter 5: Exploiting DNS  
Chapter 6: Interacting with SMB and NTLM  
Chapter 7: Abusing Databases and Filesystems  
Chapter 8: Raw Packet Processing  
Chapter 9: Writing and Porting Exploit Code  
Chapter 10: Go Plugins and Extendable Tools  
Chapter 11: Implementing and Attacking Cryptography  
Chapter 12: Windows System Interaction and Analysis  
Chapter 13: Hiding Data with Steganography  
Chapter 14: Building a Command-and-Control RAT  
  
One of my favorite chapters was Chapter 6 on NTLM and SMB, as they walked through a basic understanding of the protocol and how it negotiates its session. Unfortunately I felt like this chapter was way too short, as they really only show how to authenticate and negotiate a session, something that has already been explored in public domain for awhile now. Another one of my favorite chapters was the Windows internals chapter, which dealt with a wide range of subjects, from remote process injection to windows PE header parsing. If your into topics like PE parsing, I urge you to checkout [binject](https://github.com/Binject/binjection/), where we more completely parse [PEs](https://github.com/Binject/debug/blob/master/pe/write.go), [ELFs](https://github.com/Binject/debug/blob/master/elf/write.go), and [Mach-os](https://github.com/Binject/debug/blob/master/macho/write.go) in go. I wish the book would link out to more complete projects and examples in each of their chapters, as there are so many mature projects in go around the same topics they cover in the book. After speaking to a few people who have read it, several repeated that the golang info, protocol details, or security theory can all be studied in more depth from more authoritative sources. This book is like a broad amalgamation of several individually deep topics, but only offers a brief intro to each of them. I personally waited a long time for this book, a few years since it was first announced. In that time I actually read a number of alternative go programming books (ex: [Security with Go](http://lockboxx.blogspot.com/2018/03/book-review-security-with-go.html)), as well as explored many fully developed projects around these same ideas. Comparing this with similar go books, Black Hat Go doesn't hold up well and doesn't offer anything novel on its own. I also don't like how much of the book contains repetitive code. Multiple chapters set up the same example either showing them incorrectly the first few times or showing slightly different implementations, resulting in a lot of the book being repetitive rehashing of the same examples. As a go fanatic, even if you don't get this book to learn go, I still highly encourage you to pick up this language. The following presentation really has nothing to with the authors, but I liked it as an intro to go, which some people who may have found this post might be looking for:  
  

  
That said, the following presentation is much closer in style to the book Black Hat Go and it's target audience. While it doesn't have any relation to the book,  the examples she demonstrates are extremely similar to the types of examples they use in this book. Further, she has a simpler approach to the language that new people may find easier: