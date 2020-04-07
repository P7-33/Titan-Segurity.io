---
title: 'Variable Fonts: The Future of Web Type (2016)'
date: 2019-12-28T04:13:00+01:00
draft: false
---

![Variable fonts animation by CJ Dunn using Dunbar](https://typographica.org/wp-content/uploads/2016/09/Dunbar_variable_fonts_animation_for_typographica.gif)  
I love typography, but I love the web even more. So when [news broke of OpenType 1.8](https://medium.com/@tiro/https-medium-com-tiro-introducing-opentype-variable-fonts-12ba6cd2369) and the type community [erupted](http://twitter.com/bianca_berning/status/775991553013772288) [with](http://twitter.com/timbrown/status/776052168835072000) [excitement](http://twitter.com/roxanegataud/status/777209352025407488), I immediately tried to figure out what variable fonts would mean for web developers.

Quick wins
----------

John Hudson neatly summarized the most obvious advantage of variable fonts[1](https://typographica.org/on-typography/variable-fonts/#notes) in the first line of [his introduction to the new OpenType variable font spec](http://typedrawers.com/discussion/1763/otvar-introducing-opentype-variable-fonts/p1):

> A single font that behaves like multiple fonts

What’s so great about that? Well, two of the biggest gripes developers have with webfonts are, first, that you need to download a separate file for each width or style; and, second, that those files can be pretty big. Variable fonts solve both issues by basically sticking everything into a single, highly optimized file.

_One_ network request for _one_ file for _all_ weights and styles of a typeface — that’s a pretty big deal. After all, slow downloads lead to [FOUT and FOIT](https://css-tricks.com/fout-foit-foft/); variable fonts represent a significant step in minimizing those annoyances.

In terms of the performance improvements variable fonts have to offer, the example given in the presentation of OpenType 1.8 speaks for itself. Five weights of the Segoe UI font add up to 657 KB in five separate font files. Combined into a single variable font, one 199-KB file will produce the same variety of weights — and potentially many more. That’s a seventy percent reduction in file size alone!

Two new web technologies already being used in the wild will compound variable fonts’ benefits. The first, [HTTP/2](https://www.smashingmagazine.com/2016/02/getting-ready-for-http2/), will reduce network overhead and render communication between browser and server a lot more efficient, making requesting multiple files instead of one pretty much a non-issue. The second, [WOFF2](http://www.w3.org/TR/WOFF2/), already supported by most major browsers, will compress font files down to incredibly small sizes, further boosting performance.

With bandwidth and performance issues curtailed, what else can we expect from variable fonts?

### Fewer downloads, more typography

We’ll be able to use a much wider range of widths and styles with impunity. Where previously we had to refrain from using lots of different weights to avoid long download times and performance hiccups, soon we’ll be able to all but disregard such technical details in our decision-making. Creativity, not technical limitations, will guide font choice.

### Good fallbacks, great new features

Speaking of technical limitations, here’s the question all web developers dread: What about older browsers? What happens when a browser without support encounters a variable font? Luckily, the folks who worked on the spec thought of this and built in a basic fallback mechanism: a variable font will work like a regular ol’ font, using the master design for all variations appearing in a web page.

And modern browsers? What tools will we use to manipulate variable fonts? Since the new format has only just been announced, the CSS spec understandably hasn’t had time to be drafted yet. As [John Hudson remarked](http://typedrawers.com/discussion/comment/22875/#Comment_22875):

> Members of the Font Variations and W3C CSS working groups are in contact, and variable fonts are on the agenda for this month’s W3C TPAC meeting. Topics will include not only mechanisms to explicitly specify instances in CSS, but also enable conditional dynamic (responsive) web typography with variable fonts.

### Responsive typography

[Responsive web design](http://alistapart.com/article/responsive-web-design) had a huge impact on how we build websites for the modern web, and variable fonts have the potential to do the same for [responsive typography](http://alistapart.com/blog/post/variable-fonts-for-responsive-design).

Type will have the power to shrink, grow, and gain or lose weight _seamlessly_. No need to download a new font for every variation — if the type designer even created the one you’re looking for. In other words, variable fonts can programmatically generate the exact variation you need, and will be able to respond on the fly to factors that influence readability — things like viewport size, viewing distance, contrast, ambient light, and user preferences.

![Continuous variation of weights and widths across multiple axes. Illustration by CJ Dunn using Dunbar](https://typographica.org/wp-content/uploads/2016/09/Dunbar_variable_fonts_weight_width_axes.png)

Continuous variation of weights and widths across multiple axes. All illustrations by [CJ Dunn](http://cjtype.com/dunbar/variablefonts/) using [Dunbar](http://fontsinuse.com/typefaces/42187/dunbar).

![Fonts can have other axes related to typeface design, such as x-height.](https://typographica.org/wp-content/uploads/2016/09/Dunbar_variable_fonts_xheight_axis.png)

Beyond weight and width, font makers can build other axes into OpenType 1.8 fonts, such as design parameters like x-height, further optimizing type for specific sizes or expressions.

This is one of the most interesting aspects of variable fonts; its impact on responsive design can’t be anything less than huge. Exciting times ahead!

### Smoother FOUT

Tim Brown made [an interesting observation](https://twitter.com/nicewebtype/status/776088007111835652): when operating systems eventually ship with variable fonts, they’ll become great fallback fonts in your `font-family` font stack. You’ll easily be able to tweak the system font to match your webfont’s width, x-height, and other measurements, thereby producing an incredibly smooth [FOUT](https://css-tricks.com/fout-foit-foft/) — the transition to a webfont after it has downloaded, which can cause a disruptive reshuffle of content if the webfont and fallback fonts’ metrics differ.[2](https://typographica.org/on-typography/variable-fonts/#notes)

Combine this with [CSS `font-display`](https://css-tricks.com/font-display-masses/), and fonts will never cause invisible content (FOIT) or layout shifting (FOUT) again.

Variable viability
------------------

So variable fonts seem like a good idea on paper. But, to echo [a question raised by Matthew Butterick](http://practicaltypography.com/the-scorpion-express.html), will the benefits really offset the potential costs? By the time support for variable fonts lands — and since the W3C has just started drafting the spec, that could take years — we’ll have HTTP/2, WOFF2, and [perhaps support for TrueType Collections](https://twitter.com/jenskutilek/status/777115719695732736): literally a way to wrap multiple fonts into one file. These three technologies already exist; when combined, they could rival variable fonts in compression results.

Unless you’re using a lot of weights on your site, or using a font with a very large character set (e.g., a CJK font), why go for a brand-new format with only very basic backward compatibility? Maybe the key doesn’t lie so much in compression benefits, but in responsive type. As with so many new developments in tech, only time, user testing, and experimentation will tell.

Type, the web, and the future
-----------------------------

The introduction of variable fonts is a milestone in digital type history, which was rooted in metal type for a frustratingly long time — at least in the eyes of a computer-nerd type lover like myself. Type has finally adapted to the flexible nature of our screens and the technology that fills them with content.

Developers will discover new strategies in the form of design tools and CSS rules, which will open up all kinds of new ways to experiment, adapt, and create.

My hope is that the single-weight WOFF file you use today will soon become what table layout is to web design — a technique that once worked, but that has been surpassed by a superior technique to create, consume, and enjoy content on the web.

### Notes

1.  The term “variable fonts” was first introduced by Nick Sherman in [A List Apart](http://alistapart.com/blog/post/variable-fonts-for-responsive-design).[⤴](https://typographica.org/on-typography/variable-fonts/#1 "Return to text.")
2.  Print designers familiar with Adobe’s [PDF substitution fonts](https://helpx.adobe.com/acrobat/using/pdf-fonts.html) ([AdobeSansMM and AdobeSerifMM](https://twitter.com/FontsInUse/status/778762502276382720)) will understand this concept.[⤴](https://typographica.org/on-typography/variable-fonts/#2 "Return to text.")

_A big thank-you to [Robin Rendle](https://robinrendle.com/), [John Hudson](http://tiro.com), [Bram Stein](https://www.bramstein.com/), [Hidde de Vries](https://hiddedevries.nl/en/), [Stephen Coles](http://stephencoles.org/), and [Caren Litherland](http://twitter.com/litherland) for their feedback._

**[Roel Nieskens](https://pixelambacht.nl)** is a front-end developer, font hacker, designer, video geek, and thoroughbred computer nerd working at Kabisa in Weert, The Netherlands.

  
  
from Hacker News https://ift.tt/2yLlTIS