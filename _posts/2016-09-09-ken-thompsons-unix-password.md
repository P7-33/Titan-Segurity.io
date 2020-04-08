---
title: 'Ken Thompson’s Unix password #VintageComputing #History #Unix'
date: 2019-10-09T16:59:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-36.png)

[Leah Neukirchen](https://twitter.com/LeahNeukirchen)‘s [blog discusses](https://leahneukirchen.org/blog/archive/2019/10/ken-thompson-s-unix-password.html) a Unix password file discovered in 2014 containing the encrypted passwords of all the old timers such as Dennis Ritchie, Ken Thompson, Brian W. Kernighan, Steve Bourne and Bill Joy. What a treasure! Many were cracked as they were weak…

> However, `ken`s password eluded my cracking endeavor. Even an exhaustive search over all lower-case letters and digits took several days (back in 2014) and yielded no result. Since the algorithm was developed by Ken Thompson and Robert Morris, I wondered what’s up there. I also realized, that, compared to other password hashing schemes (such as NTLM), crypt(3) turns out to be quite a bit slower to crack (and perhaps was also less optimized).

The topic [came up again](https://inbox.vuxu.org/tuhs/tqkjt9nn7p9zgkk9cm9d@localhost/T/#m160f0016894ea471ae02ee9de9a872f2c5f8ee93) earlier this month on [The Unix Heritage Society](https://www.tuhs.org/) mailing list, and they [shared their results](https://inbox.vuxu.org/tuhs/87bluxpqy0.fsf@vuxu.org/) and frustration of not being able to break `ken`s password.

Finally, today this secret [was resolved](https://inbox.vuxu.org/tuhs/CACCFpdx_6oeyNkgH_5jgfxbxWbZ6VtOXQNKOsonHPF2=747ZOw@mail.gmail.com/) by Nigel Williams:

> ```
> From: Nigel Williams   
> Subject: Re: [TUHS] Recovered /etc/passwd files  
>   
> ken is done:  
>   
> ZghOT0eRm4U9s:p/q2-q4!  
>   
> took 4+ days on an AMD Radeon Vega64 running hashcat at about 930MH/s  
> during that time (those familiar know the hash-rate fluctuates and  
> slows down towards the end).
> ```

Apparently, this is a chess move in descriptive notation, and the beginning of many common openings. It fits very well to Ken Thompson’s background in computer chess.

Mystery solved.

See [Leah’s post](https://leahneukirchen.org/blog/archive/2019/10/ken-thompson-s-unix-password.html) for additional details.