---
title: 'The Digital Equipment Corporation (DEC) Logo – ancient digitalization
found #DEC #Logo @nedbat'
date: 2019-10-28T14:13:00+01:00
draft: false
---

![Ned Batchelder](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-97.png)

A wonderful article by [NedBatchelder](https://nedbatchelder.com/) on digitally creating the PostScript code for the Digital Equipment Corporation (DEC) logo and later finding it in some older HP document archives and sharing it.

_Ed: As the article is 12 years, old and I hope Ned’s website never disappears, I’m going to quote the [entire article](https://nedbatchelder.com/blog/200712/ancient_history_the_digital_logo.html) as a means of preserving it. The following is Ned’s voice telling the narrative. I highly suggest you check out all the great info on [his site](https://nedbatchelder.com/) and [Twitter feed](https://twitter.com/nedbat). We highly suggest [sponsoring Ned on GitHub](https://nedbatchelder.com/blog/201910/sponsor_me_on_github.html)._

**Sunday 16 December 2007**

My first corporate job was with Digital Equipment Corporation. I worked in the printer group, on PostScript technologies. It was common then to simulate the [Digital logo](http://vt100.net/dec/logo) by scaling Helvetica and superimposing it in white onto colored rectangles.

But I knew that was inaccurate, and it gave a bad hacked-up impression. So I took it upon myself to create a genuine Digital logo in PostScript. My association with the logo was strong enough that I still get requests every few months for the logo. I am now an HP employee, so I have contact with even more ex-DECcies interested in the logo (HP bought Compaq which bought Digital, you see).

When the latest request came in, I decided to make a serious attempt at resurrecting the logo.

I don’t have the PostScript file for the logo any more, but it was often included in PostScript files generated from the in-house document creation tool (VAX Document). HP still maintains an archive of papers from the Digital days, so I figured a little archaeology there would yield a logo fossil.

A Google search for the [term VMS in PostScript files on hp.com](http://www.google.com/search?q=vms%20filetype%3Aps%20site%3Ahp.com) provided a direct hit: the first result (a paper entitled [How the RDB/VMS Data Sharing System Became Fast](http://gatekeeper.hpl.hp.com/archive/pub/Compaq/CRL/research-reports/92.4.ps)) _(Ed: This link no longer works)_ had the Digital logo font in it. Digging deeper, it turns out I was really lucky: very few of the papers on the site had the logo.

The logo I made was actually a font (Type 3, meaning the characters were defined with PostScript code). Back in 1987 I went to the graphic design group and got the largest photographic master of the logo they had. I scanned them, then used an early version of Adobe Illustrator to create the curves.

Here’s the historical summary I included in the font file:

> The logo was designed in 1957 by Elliot Hendrickson, who was then working as an independent designer. He was contracted by DEC to do a brochure, and DEC wanted a logo to accompany it. The logo up to then had been the letters DEC in blocks the shape of the plug-in cards that DEC had been producing. Elliot re-worked the logo, incorporating letters which were hand-drawn for the purpose by Arthur Hover(?). The logo has been maintained since then in conventional technology, i.e. film masters. There was at least one reworking of the logo at some point.
> 
> The masters I received had a number of interesting features. The boxes were not all the same width, and there seemed to be no logic to which boxes were wider. The ‘g’ was the narrowest, and the ‘i’ and ‘l’ were second widest. Also, the two ‘i’s were not exactly the same shape. On ten-inch masters, (one box to an 8”×11” sheet), the boxes were not rectangles, but were very slightly tapered in weird ways. I assume that the tapering is the result of too many reproductions, but the difference in widths may have been deliberate at some time. Elliot reports that when he drew it, all boxes were the same width. I have made all of the boxes the same width, since that seems to have been the original intent, since the differences were almost negligible anyway, and since there was no logic to the differences.

The font I retrieved from the research report had none of the commentary, but here is the code ([declogo17.ps](https://nedbatchelder.com/files/declogo17.ps)):

> ```
> 11 dict begin  
>   
> /FontInfo 3 dict def  
> FontInfo begin  
>     /Notice (The Digital logo is a registered trademark of Digital Equipment Corporation.) def  
>     /FullName (Digital Logo) def  
>     /version (1.7, 24-Apr-1989) def  
>     end  
>   
> /FontName /DEC\_Logo def  
> /FontType 3 def                         % This is a user-defined font  
> /FontMatrix matrix def                  % Use an identity transform  
> /FontBBox \[ 0 0 3.383 1 \] def           % Logo itself is biggest  
> /GapWidth .070 def                      % The width of the gap between boxes  
> /LogoWidth 3.383 def                    % The width of the logo  
>   
> /Encoding 256 array def  
> 0 1 255 { Encoding exch /.notdef put } for  
>   
> Encoding  
> dup (d) 0 get /DEC-logo put             % (d) gives logo  
> dup (t) 0 get /smalltrademark put       % (t) gives small trademark  
>     (T) 0 get /largetrademark put       % (T) gives large trademark  
>   
> /Work 15 dict def                       % for doing work in font.  
>   
> /BuildChar {  
>     exch begin                          % Use the font dictionary  
>         Work begin  
>             Encoding exch get           % Look up the character name  
>             load                        % Pull out the procedure  
>             exec                        % Run it.  
>             end                         % Work  
>         end                             % fontdict  
>     } def  
>   
> Work begin  
>   
> /.notdef {} def  
>   
> /words {  
>     0           %   
>     moveto      % !  
>     curveto     % "  
>     closepath   % #  
>     lineto      % $  
>     boxw        % %  
>     boxstep     % &  
>     translate   % '  
> } bind cvlit def  
> ( mr vy! mt rQ h\[ kF aw kE" Zw kG T@ q\] T@ ~I" T@ AKA Zv AQi ai AQk" h\[ AQi m  
> t AJX mr ADw"# nI AZ\[! nI Avp$ |C Avp$ |C ^h$ mk ^h$ mk bl$ l\` a\` gc \\\\U \_F   
> \\\\U" VR \\\\T Fa cj Fa ~I" Fa ATf RS A\`M \`S A\`M" e\_ A\`M je A^W nI AZ\["#% !% B\\\\  
> P$  B\\\\P$  $#& '% !% B\\\\P$  B\\\\P$  $# ZK ^h! ZK A\]p$ hO A\]p$ hO ^h$# ZK AfV!  
>  ZK Au~$ hO Au~$ hO AfV$#& ' l\[ AE~! l\[ AKe fG AQX \`Q AQX" \[O AQX S\] ANK S\]   
> ?t" S\] pa \]A nR \`L nR" f\_ nR l\[ rg l\[ yS"#  B\\\\P!% B\\\\P$% $  $# ld AWi! kG A  
> Yn fV A^\\\\ \_b A^\\\\" T} A^\[ FM AXT FM }s" FN hy V{ ax \]r ax" eL aw jl fK lL g  
> s" lL aN$ lL \\\\W gM Wg ^w Wg" Wk Wh V{ \\\\O V{ ^a" HO ^a$ HO WN L| Ld \]~ Lc"   
> mN Lc rP RX t\[ Td" vP VZ x? \[^ x? \_a" x? A\]p$ le A\]p$#& '% !% B\\\\P$  B\\\\P$   
> $# ZK ^h! ZK A\]p$ hO A\]p$ hO ^h$# ZK AfV! ZK Au~$ hO Au~$ hO AfV$#& ' dX Aue  
> ! Wa Aue$ Wa A^w$ Pr A^w$ Pr ATT$ Wa ATT$ Wa ld$ Wa d? \[Z \_B fP \_C" kU \_C kH  
>  \_A ob \_r" ob lz$ lj lZ kq lM jW lP" gj lU dX mR dX rF" dX ATS$ nd ATS$ nd A  
> ^w$ dX A^w$#% !  $  B\\\\P$% B\\\\P$#& '  !  B\\\\P$% B\\\\P$% $# J{ AIx! V~ AIx$ V~  
>  APR ZR ASi \`f ASi" jj ASj jU AOK jT AId" dF AGI dk AGM \[L AEC" OI ABQ Gq }G  
>  Gp ph" Gq d\[ P\] \]z ZP \]{" dD \]z fF aE jJ cr" jJ ^z$ yb ^z$ uz dp vw ey vu j  
> R" vv mn vu AOX vu AOX" vv AVC sX AZH qG A\[\_" k\] A^w d^ A\_Q \`f A\_R" Ru A\_P J  
> z AXU J{ AIx"# jT }j! jT uI$ jT qP ee in \\\\R im" Wp il UN mC UM qZ" UN ur X{  
>  yI \\\\D yq" \_U z\[ fv |V jT }j"#& '% !% B\\\\P$  B\\\\P$  $# ZK ^h! ZK Awb$ hO Aw  
> b$ hO ^h$#)  
> /pathstring exch def  
>   
> /round-to-pixels {  
>     0 transform  
>     round exch round exch  
>     itransform  
>     pop  
>     } def  
>   
> /DEC-logo {  
>     3.383 0 0 0 3.383 1 setcachedevice  
>     .0001 .0001 scale  
>   
>     /boxw 4250 round-to-pixels def  
>     /boxstep 4950 round-to-pixels def  
>   
>     pathstring  
>     {  
>         dup 62 gt  
>         {   63 and exch 6 bitshift add }  
>         {   dup 32 ge  
>             {   32 sub words exch get exec }  
>             {   pop }  
>             ifelse  
>             }  
>         ifelse  
>         }  
>     forall  
>   
>     fill  
>     } def  
>   
>   
> /trademark {  
>     /s exch .380 div def  
>     /w s .725 mul .070 add def  
>     /u 1 .673 s mul sub def  
>     w 0 0 u w 1 setcachedevice  
>     /Symbol findfont s scalefont setfont  
>     .070 u moveto                               % Superscript it  
>     (\\344) show  
>     } def  
>   
>   
> /smalltrademark { .15 trademark } def  
> /largetrademark { .25 trademark } def  
>   
> end                                             % Work dictionary  
>   
> FontName                                        % Get the name  
> currentdict                                     % Get the font dict  
> end                                             % Close up the dict  
> definefont pop                                  % Define the font
> ```

I don’t remember encoding the path in that tricky way: the printed copy I have of the code was much lengthier. _Updated:_ Alert reader Peter Weaver sent along a copy he found of the earlier version: [declogo11.ps](https://nedbatchelder.com/files/declogo11.ps). _(Ed: at end of article)_

To draw with the font, I added this code:

> ```
> /DEC\_Logo findfont 100 scalefont setfont  
> 72 72 moveto  
> (d) show  
> showpage  
> 
> ```

With that PostScript file, I could create a [PDF file](https://nedbatchelder.com/files/declogo.pdf), an [Illustrator file](https://nedbatchelder.com/files/declogo.ai) (back to home!) then .PNGs:

[![](https://cdn-blog.adafruit.com/uploads/2019/10/declogo_large.png)](https://nedbatchelder.com/pix/declogo_large.png)

Hopefully, these will satisfy the needs for Digital logo fans. If you need anything more, let me know!

[The original article is here, long may it live and educate.](https://nedbatchelder.com/blog/200712/ancient_history_the_digital_logo.html)

DecLogo11.ps:

> ```
> % See http://nedbatchelder.com/blog/200712/ancient\_history\_the\_digital\_logo.html  
> %!PS-Adobe-2.0  
> %%Title: PostScript Digital Logo Font, v1.1  
> %%Creator: Ned Batchelder  
> %%CreationDate: 9-Nov-87  
> %%DocumentFonts: Symbol  
> %%DocumentSuppliedFonts: DigitalLogo  
> %%EndComments  
> %  
> %      DIGITAL INTERNAL USE ONLY  
> %  
> % INTRODUCTION:  
> % This rendition of the Digital logo was prepared by Ned Batchelder using  
> % Adobe Illustrator and hand manipulation of the resulting PostScript code.  
> % Photographic masters of the logo were obtained from David Comberg in the  
> % Graphic Design Group. Additional consultation was provided by Elliot  
> % Hendrickson, one of the original designers of the logo.  
> %  
> % USE:  
> % This file defines a new PostScript font, called /DigitalLogo. It consists  
> % of three characters. (d) is the entire Digital logo, (t) is a small  
> % trademark symbol, and (T) is a large trademark symbol. The font is designed  
> % so that the argument to scalefont is the height of the logo. There is no  
> % extra white space around the logo at all. The trademarks are designed to be  
> % shown right after the logo, and they align themselves. The only correct  
> % strings to show with this font are (d), (dt), and (dT). There is an entry  
> % (named GapWidth) in the font dictionary which gives the unscaled width of  
> % the gap between the blocks. This distance is given because it is used as a  
> % unit to determine how much space to leave around the logo.  
> %  
> % HISTORY:  
> % The logo was designed in 1957 by Elliot Hendrickson, who was then working  
> % as an independent designer. He was contracted by DEC to do a brochure, and  
> % DEC wanted a logo to accompany it. The logo up to then had been the letters  
> % DEC in blocks the shape of the plug-in cards that DEC had been producing.  
> % Elliot re-worked the logo, incorporating letters which were hand-drawn for  
> % the purpose by Arthur Hover(?). The logo has been maintained since then in  
> % conventional technology, ie, film masters. There was at least one reworking  
> % of the logo at some point.  
> %  
> % The masters I received had a number of interesting features. The boxes were  
> % not all the same width, and there seemed to be no logic to which boxes were  
> % wider. The 'g' was the narrowest, and the 'i' and 'l' were second widest.  
> % Also, the two 'i's were not exactly the same shape. On ten-inch masters,  
> % (one box to an 8½x11 sheet), the boxes were not rectangles, but were very  
> % slightly tapered in wierd ways. I assume that the tapering is the result of  
> % too many reproductions, but the difference in widths may have been  
> % deliberate at some time. Elliot reports that when he drew it, all boxes  
> % were the same width. I have retained the different widths in my version,  
> % since the experts I had at hand did not seem to think I should make them  
> % uniform.  
> %  
> % Please feel free to use this logo, but keep in mind the following:  
> %  
> % 1. This code is for INTERNAL USE ONLY.  
> % 2. I am not entirely happy with the final shapes of the letters, and am  
> % hoping to improve them. Please allow for future updates to this code.  
> % 3. Only use this logo within the guidelines of the Corporate Identity  
> % program. If you use this font precisely as is, you can't get in much  
> % trouble. Don't take the shapes and do strange things with them.  
> % In particular, the Identity states that the logo is a one-color logo: The  
> % letters are actually holes in the blocks, through which the background can  
> % be seen. Do not modify this code so that the letters are always white.  
> %  
> % Edit history:  
> %  
> % 21-Sep-87 nmb     Created as a standalone file with demo.  
> %  6-Nov-87 nmb     Converted to font form.  
> %  9-Nov-87 nmb     Removed // uses for compatibility with LW Classics  
> %  
>   
> %%BeginFont: DigitalLogo  
> 10 dict begin  
>   
> /FontInfo 3 dict def  
> FontInfo begin  
>     /Notice  
> (The Digital logo is a registered trademark of Digital Equipment Corporation.)  
>     def  
>     /FullName (Digital logo) def  
>     /version (1.1) def  
>     end  
>   
> /FontType 3 def                         % This is a user-defined font  
> /FontMatrix matrix def                  % Use an identity transform  
> /FontBBox \[ 0 0 3.383 1 \] def           % Logo itself is biggest  
> /GapWidth .070 def                      % The width of the gap between boxes  
>   
> /Encoding 256 array def  
> 0 1 255 { Encoding exch /.notdef put } bind for  
>   
> Encoding  
> dup (d) 0 get /DEC-logo put             % (d) gives logo  
> dup (t) 0 get /smalltrademark put       % (t) gives small trademark  
>     (T) 0 get /largetrademark put       % (T) gives large trademark  
>   
> /Work 15 dict def                       % for doing work in font.  
>   
> /BuildChar {  
>     exch begin                          % Use the font dictionary  
>         Work begin  
>             Encoding exch get           % Look up the character name  
>             load                        % Pull out the procedure  
>             exec                        % Run it.  
>             end                         % Work  
>         end                             % fontdict  
>     } bind def  
>   
> Work begin  
>   
> /.notdef {} def  
>   
> %  
> % - \`DEC-logo' -  
> %  
> % Images a DEC logo with the lower left corner at the current origin, with a  
> % height of one unit, in the current color.  
> %  
>   
> /m /moveto load def  
> /l /lineto load def  
> /c /curveto load def  
>   
> /DEC-logo {  
>     3.383 0 0 0 3.383 1 setcachedevice  
>     {   % D  
>         % d counter  
>         .2930 .3513 m  
>         .2932 .3217 .2587 .2758 .2167 .2757 c  
>         .1719 .2759 .1280 .3165 .1280 .3977 c  
>         .1280 .4801 .1718 .5225 .2153 .5227 c  
>         .2587 .5225 .2932 .4760 .2930 .4407 c  
>         closepath  
>         % d outside  
>         .2953 .5787 m  
>         .2953 .7600 l  
>         .3843 .7600 l  
>         .3843 .1960 l  
>         .2923 .1960 l  
>         .2923 .2220 l  
>         .2848 .2144 .2531 .1813 .1990 .1813 c  
>         .1426 .1812 .0417 .2282 .0417 .3977 c  
>         .0417 .5414 .1171 .6157 .2067 .6157 c  
>         .2399 .6157 .2725 .6039 .2953 .5787 c  
>         closepath  
>         % d box  
>         .432 0.0 m  
>         .432 1.0 l  
>         .000 1.0 l  
>         .000 0.0 l  
>         closepath  
>         } exec  
>     {   % I  
>         % i box  
>         .927 0.0 m  
>         .927 1.0 l  
>         .502 1.0 l  
>         .502 0.0 l  
>         closepath  
>         % i body  
>         .6695 .196 m  
>         .6695 .600 l  
>         .7595 .600 l  
>         .7595 .196 l  
>         closepath  
>         % i dot  
>         .6695 .655 m  
>         .6695 .755 l  
>         .7595 .755 l  
>         .7595 .655 l  
>         closepath  
>         } exec  
>     {   % G  
>         % g counter  
>         1.2813 .4478 m  
>         1.2813 .4837 1.2409 .5208 1.2035 .5208 c  
>         1.1713 .5208 1.1215 .5003 1.1215 .4084 c  
>         1.1215 .3105 1.1827 .2962 1.2030 .2962 c  
>         1.2433 .2962 1.2813 .3239 1.2813 .3667 c  
>         closepath  
>         % g box  
>         0.997 1.0 m  
>         1.415 1.0 l  
>         1.415 0.0 l  
>         0.997 0.0 l  
>         closepath  
>         % g outside  
>         1.2822 .5609 m  
>         1.2729 .5742 1.2424 .6044 1.1988 .6044 c  
>         1.1311 .6043 1.0367 .5652 1.0367 .3955 c  
>         1.0368 .2617 1.1437 .2168 1.1876 .2168 c  
>         1.2350 .2167 1.2702 .2443 1.2798 .2547 c  
>         1.2798 .2126 l  
>         1.2798 .1815 1.2479 .1511 1.1945 .1511 c  
>         1.1485 .1512 1.1437 .1807 1.1437 .1953 c  
>         1.0497 .1953 l  
>         1.0497 .1486 1.0798 .0804 1.1888 .0803 c  
>         1.2864 .0803 1.3186 .1176 1.3325 .1316 c  
>         1.3442 .1434 1.3617 .1758 1.3617 .2017 c  
>         1.3617 .6 l  
>         1.2823 .6 l  
>         closepath  
>         } exec  
>     {   % I  
>         % i box  
>         1.910 0.0 m  
>         1.910 1.0 l  
>         1.485 1.0 l  
>         1.485 0.0 l  
>         closepath  
>         % i body  
>         1.6525 .196 m  
>         1.6525 .6 l  
>         1.7425 .6 l  
>         1.7425 .196 l  
>         closepath  
>         % i dot  
>         1.6525 .655 m  
>         1.6525 .755 l  
>         1.7425 .755 l  
>         1.7425 .655 l  
>         closepath  
>         } exec  
>     {   % T  
>         % t  
>         2.2128 .7525 m  
>         2.1305 .7525 l  
>         2.1305 .6071 l  
>         2.0874 .6071 l  
>         2.0874 .5396 l  
>         2.1305 .5396 l  
>         2.1305 .2852 l  
>         2.1305 .2367 2.1554 .1986 2.2248 .1987 c  
>         2.2573 .1987 2.2560 .1985 2.2842 .2034 c  
>         2.2842 .2874 l  
>         2.2658 .2842 2.2601 .2829 2.2511 .2832 c  
>         2.2338 .2837 2.2128 .2898 2.2128 .3206 c  
>         2.2128 .5395 l  
>         2.2780 .5395 l  
>         2.2780 .6071 l  
>         2.2128 .6071 l  
>         closepath  
>         % t box  
>         2.404 0.0 m  
>         1.980 0.0 l  
>         1.980 1.0 l  
>         2.404 1.0 l  
>         closepath  
>         } exec  
>     {   % A  
>         % a box  
>         2.474 0.0 m  
>         2.474 1.0 l  
>         2.888 1.0 l  
>         2.888 0.0 l  
>         closepath  
>         % a outside  
>         2.5439 .4728 m  
>         2.6210 .4728 l  
>         2.6210 .5138 2.6422 .5353 2.6826 .5353 c  
>         2.7470 .5354 2.7449 .5067 2.7448 .4708 c  
>         2.7050 .4553 2.7087 .4557 2.6480 .4419 c  
>         2.5709 .4241 2.5237 .3911 2.5236 .3112 c  
>         2.5237 .2331 2.5793 .1914 2.6420 .1915 c  
>         2.7048 .1914 2.7178 .2117 2.7438 .2290 c  
>         2.7438 .1978 l  
>         2.8422 .1978 l  
>         2.8190 .2352 2.8251 .2425 2.8249 .2706 c  
>         2.8250 .2926 2.8249 .5080 2.8249 .5080 c  
>         2.8250 .5507 2.8028 .5768 2.7883 .5855 c  
>         2.7521 .6071 2.7074 .6097 2.6826 .6098 c  
>         2.5945 .6096 2.5438 .5653 2.5439 .4728 c  
>         closepath  
>         % a counter  
>         2.7448 .3946 m  
>         2.7448 .3401 l  
>         2.7448 .3152 2.7145 .2670 2.6550 .2669 c  
>         2.6260 .2668 2.6098 .2883 2.6097 .3162 c  
>         2.6098 .3442 2.6335 .3657 2.6536 .3697 c  
>         2.6745 .3739 2.7226 .3862 2.7448 .3946 c  
>         closepath  
>         } exec  
>     {   % L  
>         % l box  
>         3.383 0.0 m  
>         3.383 1.0 l  
>         2.958 1.0 l  
>         2.958 0.0 l  
>         closepath  
>         % l  
>         3.1255 .196 m  
>         3.1255 .765 l  
>         3.2155 .765 l  
>         3.2155 .196 l  
>         closepath  
>         } exec  
>     fill  
>     } bind def  
>   
> %  
> % % pct \`trademark' --  
> %  
> % Borrow the sans-serif trademark symbol from /Symbol. AFM file says:  
> % C 228 ; WX 786 ; N trademarksans ; B 5 293 725 673 ;  
> % We scale it down to pct percent of the height of the logo and superscript  
> % it some, and voila!  
> %  
>   
> /trademark {  
>     /s exch .380 div def  
>     /w s .725 mul .070 add def  
>     /u 1 .673 s mul sub def  
>     w 0 0 u w 1 setcachedevice  
>     /Symbol findfont s scalefont setfont  
>     .070 u m                                    % Superscript it  
>     (\\344) show  
>     } bind def  
>   
> %  
> % These are two different trademarks (just different sizes).  
> %  
>   
> /smalltrademark { .15 trademark } def  
> /largetrademark { .25 trademark } def  
>   
> end                                             % Work dictionary  
>   
> currentdict                                     % Get the font dict  
> end                                             % Close it up  
> /DigitalLogo exch definefont pop                % Define the font.  
>   
> %%EndFont
> ```