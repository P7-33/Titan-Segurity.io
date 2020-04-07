---
title: 'Wormhole: direct two network devices with Python #Python @biglesp'
date: 2020-01-07T14:59:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2020/01/Untitled-18.png)

[Les Pounder posts](https://bigl.es/tooling-tuesday-magic-wormhole/) the question: Have you ever needed to send a file to someone who is in the same room? Enter: Wormhole.

> [This is a tool written in Python to send files over a local network by creating a direct link between two devices, a wormhole!](https://magic-wormhole.readthedocs.io/en/latest/welcome.html)
> 
> It is a tool to send files direct from two devices in the same room / location where the sender and recipient can speak to one another.
> 
> Let’s take a typical scenario, where I have some files that I need to transfer to a friends laptop. I reach in my pocket but my USB drives are at home, and yes so are my friends!! So how do I send the files quickly? Well I use Magic Wormhole!

To use it, you install on Linux, mac, or Windows via the Python installer. To use:

> I’m sat at my laptop and I want to send a file `Th3-M4nd410r14n.mp4` to my friends computer. So I open a terminal and type.
> 
> ```
> wormhole send Th3-M4nd410r14n.mp4  
> 
> ```
> 
> This will then trigger the following text.
> 
> ```
> Sending 657 Bytes file named 'Th3-M4nd410r14n.mp4'  
> On the other computer, please run: wormhole receive  
> Wormhole code is: 75-disbelief-cobra
> ```

[See the blog post](https://bigl.es/tooling-tuesday-magic-wormhole/) for more information.