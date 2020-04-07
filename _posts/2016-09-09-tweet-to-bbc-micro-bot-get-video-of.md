---
title: 'Tweet to the BBC Micro Bot, get a video of your code
running! #BBCMicro #VintageComputing @DominicPajak'
date: 2020-02-24T15:14:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/02/ezgif-6-a703885d7f71.gif)

[8bitkick.cc](http://www.8bitkick.cc/) hosts a marvelous BBC Micro Model B emulator named [BBC Micro Bot](http://www.8bitkick.cc/bbc-micro-bot.html). Using it could not be easier: Send a tweet to [@bbcmicrobot](https://twitter.com/bbcmicrobot) and it will run it on a 1980s 8-bit computer emulator!

This bot runs a full emulation of the [BBC Micro Model B](https://computerhistory.org/blog/the-bbc-micro/) – a computer standard in schools in the UK during the 1980s. There is a lot more you can do with it!

> BBC BASIC
> ---------
> 
> The BBC Micro Model B emulator used by the bot is running [BBC BASIC II](https://en.wikipedia.org/wiki/BBC_BASIC) (1982). If you’ve never tried BBC BASIC checking out the examples on the [@bbcmicrobot](https://twitter.com/bbcmicrobot) Twitter account is a good place to start.

The [program graphic above](https://twitter.com/bbcmicrobot/status/1231339415911444481) is by Neil and uses abbreviated (minification) commands. so the actual code looks like:

> ```
> 0a=1305:DIMX(35),Y(35):F.I=0TO35:A=I\*PI/18:X(I)=375\*SINA:Y(I)=300\*COSA:  
> N.:MO.2:V.29,640;512;23,0,8202;0;0;0;:REP.U.FNA(FNA(FNA(1)))   
> 1DEFFNA(N):F.I=0TO11:F.O=0TON:V.18,3,1-(N-1)\*(I   
> MOD7),1049;X(I);Y(I);a;X(I+12);Y(I+12);a;X(I+24);Y(I+24);a;X(I);Y(I);:N.,:=0
> ```

But you can get started by tweeting:

> ```
> 10 MODE 2  
> 20 COLOUR RND(7)  
> 30 PRINT "HELLO WORLD"  
> 40 GOTO 20
> ```

The bot generates a [3 second, 50fps mp4](https://twitter.com/bbcmicrobot/status/1226927329550618625) after 30 seconds of emulated execution time. If you’re curious you might have noticed the [Acornsoft Graphics Extension ROM](https://stardot.org.uk/forums/viewtopic.php?t=16838) is installed on the emulated machine. The bot also has a pretty strict filter for bad words and blocks offenders immediately, because printing rude words in infinite loops looks a lot like spam to Twitter!

Check the bot out by tweeting to [@bbcmicrobot](https://twitter.com/bbcmicrobot) and see the [web page here](http://www.8bitkick.cc/bbc-micro-bot.html).

If you’d like to get up to speed on BBC BASIC, check out:

*   Learn to write games for the BBC Micro with Eben | [blog](https://www.raspberrypi.org/blog/learn-to-write-games-for-the-bbc-micro-with-eben/)
*   BBC Micro User Guide [html](http://central.kaserver5.org/Kasoft/Typeset/BBC/Contents.html) | [PDF](http://bbc.nvg.org/doc/BBCUserGuide-1.00.pdf)
*   8BS.com’s huge collection of [BBC BASIC books](http://8bs.com/othrdnld/manuals/publications.shtml)

![](https://cdn-blog.adafruit.com/uploads/2020/02/untitled-61.jpg)