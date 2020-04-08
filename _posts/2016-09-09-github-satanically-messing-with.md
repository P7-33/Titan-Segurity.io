---
title: 'GitHub satanically messing with Markdown – changes 666 to DCLXVI'
date: 2019-11-26T03:04:00+01:00
draft: false
---

This seems to be followed by [github/markup issue 991](https://github.com/github/markup/issues/991), where on ordered sub-list, decimal numerals automatically turns into roman numerals.

> I have found the cause of problem. It is CSS
> 
> > This is the expected way for nested ordered lists to render in HTML.
> 
> This is not expected in HTML. [https://jsfiddle.net/tf5jtv8s](https://jsfiddle.net/tf5jtv8s)
> 
> > We don't make any modifications to the default HTML behavior.
> 
> ```
> ol ol,ul ol{list-style-type:lower-roman} 
> ```
> 
> I don't know CSS but my understanding is that this is the cause of problem. I can get expected result by disabling CSS. (I am from my mobile so I can't use browser inspector)

As mentioned in "[A formal spec for GitHub Flavored Markdown](https://githubengineering.com/a-formal-spec-for-github-markdown/)", GitHub markdown spec [GFM: GitHub Flavored Markdown Spec](https://github.github.com/gfm/) is built on top of the [CommonMark Spec](http://spec.commonmark.org/0.26).

And as [Tommi Kaikkonen](https://stackoverflow.com/users/8132914/tommi-kaikkonen) mentioned in [his answer](https://stackoverflow.com/a/44619303/6309), the ordered list is because of the dot following 666. See [GFM Spec section 5.2](https://github.github.com/gfm/#list-items).

As mentioned in [section 6.1](https://github.github.com/gfm/#backslash-escapes), any ASCII punctuation character may be backslash-escaped, to avoid this issue.  
That means:

```
- 666\. ha. 
```

(as explicitly shown in [ForNeVeR](https://stackoverflow.com/users/2684760/fornever)'s [answer](https://stackoverflow.com/a/44623878/6309))

That is why that `666` number is changed to roman numerals in a GitHub `README` markdown.

* * *

[Mike Lippert](https://stackoverflow.com/users/2184226/mike-lippert) commented:

> the 1st element in that list so it should show as `i` not `dclxvi`.  
> Markdown ordered lists ignore the actual number used and number sequentially, and I haven't seen a way to change that.

However, no: it shows `dclxvi`, because the generated html code is

, which is consistent with [the GFM specs](https://github.github.com/gfm/#list-items):

> If the list item is ordered, then it is also assigned a start number, based on the ordered list marker"

(here, '`666`' is the ordered list marker)

Mike adds:

> > @VonC For anyone else here's another useful excerpt from VonC's doc link:
> 
> "The start number of an ordered list is determined by the list number of its initial list item. The numbers of subsequent list items are disregarded."

* * *

> Also, why is the spacing messed up? I didn't catch that in your answer

You get an ordered list

within an un-ordered list _item_3.  :
    
    ```
     *    
         666.  ha. 
    ```
    
    GitHub CSS rules include:
    
    ```
    .markdown-body ol { padding-left: 2em; } 
    ```
    
    If you put `3em`, you would get  
    [![correct padding](https://i.stack.imgur.com/zmUrx.png)](https://i.stack.imgur.com/zmUrx.png)  
    instead of  
    [![wrong padding](https://i.stack.imgur.com/rKPZY.png)](https://i.stack.imgur.com/rKPZY.png)
    

  
  
from Hacker News https://ift.tt/2QxNGsL