---
title: '10 Simple CSS Code Examples You Can Learn in 10 Minutes'
date: 2019-11-16T04:52:00+01:00
draft: false
---

![css-code-in-10-minutes](https://static.makeuseof.com/wp-content/uploads/2017/06/css-code-in-10-minutes.jpg)

Once you’ve started dabbling in HTML, you’ll probably be interested in adding more power to your web pages. CSS is the best way to do that. CSS lets you apply changes across your entire page without relying on inline styling.

[![](https://static.makeuseof.com/wp-content/uploads/2019/08/CSS-Properties-Cheat-Sheet.jpg)](http://makeuseof.tradepub.com/c/pubRD.mpl?sr=oc&_t=oc:&pc=w_makc08&ch=CSSPROPP)

[Download our FREE "Essential CSS3 Properties Cheat Sheet" today!](http://makeuseof.tradepub.com/c/pubRD.mpl?sr=oc&_t=oc:&pc=w_makc08&ch=CSSPROPP)

  

[Download](http://makeuseof.tradepub.com/c/pubRD.mpl?sr=oc&_t=oc:&pc=w_makc08&ch=CSSPROPP)

Here are several simple CSS examples to show you how to make some basic styling changes on your web page.

1\. Basic CSS Code for Easy Paragraph Formatting
------------------------------------------------

Styling with CSS means you don’t have to specify a style every time you create an element. You can just say “all paragraphs should have this particular styling” and you’re good to go.

Let’s say you want every paragraph (

, one of the [HTML tags everyone should know](//www.makeuseof.com/tag/top-11-html-tags-blogger-website-owner/)) to be slightly larger than usual. And dark grey text, instead of black. The CSS code for this is:

```
p {  
  
  font-size: 120%;  
  
  color: dimgray;  
  
}
```

Simple! Now, whenever the browser renders a paragraph, the text will inherit the size (120 percent of normal) and color (“dimgray”).

If you’re curious as to which plain-text colors you can use, check out this [CSS color list](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) from Mozilla.

2\. Change Letter Case
----------------------

Want to create a designation for paragraphs that should be in small caps? A CSS sample for that would be:

```
p.smallcaps {  
  
  font-variant: small-caps;  
  
}
```

To make a paragraph that’s entirely in small caps, we’ll use a slightly different HTML tag. Here’s what it looks like:

```


Your paragraph here.


```

Adding a dot and a class name to an element specifies a sub-type of that element defined by a class. You can do this with text, images, links, and just about anything else.

If you want to change the case of a set of text to a specific case, use these CSS examples:

```
text-transform: uppercase;  
  
text-transform: lowercase;  
  
text-transform: capitalize;
```

The last one capitalizes the first letter of every sentence.

3\. Change Link Colors
----------------------

Style changes aren’t limited to paragraphs. There are four different colors a link can be assigned: its standard color, its visited color, its hover color, and its active color (which it displays while you’re clicking on it). Here’s the CSS code for those:

```
a:link {  
  
color: gray;  
  
}  
  
a:visited {  
  
color: green;  
  
}  
  
a:hover {  
  
color: purple;  
  
}  
  
a:active {  
  
color: teal;  
  
}
```

With links, each “a” is followed by a colon, not a dot.

Each one of those declarations changes the color of a link in a specific context. There’s no need to change the class of a link to get it to change color.

4\. Remove Link Underlines
--------------------------

While underlined text clearly indicates a link, it sometimes looks nicer to scrap that underline. This is accomplished with the “text-decoration” attribute. This CSS examples shows how to remove underlines on links:

```
a {  
  
text-decoration: none;  
  
}
```

Anything with the link (“a”) tag will remain non-underlined. Want to underline it when the user hovers over it? Simply add:

```
a:hover {  
  
text-decoration: underline;  
  
}
```

You could also add this text-decoration to active links to ensure the underline doesn’t disappear when the link is clicked.

5\. Make a Link Button With CSS Code
------------------------------------

Want to attract more attention to your link? A link button is a great way to go about it. This one requires a few more lines, but we’ll go over them each individually:

```
a:link, a:visited, a:hover, a:active {  
  
background-color: green;  
  
color: white;  
  
padding: 10px 25px;  
  
text-align: center;  
  
text-decoration: none;  
  
display: inline-block;  
  
}
```

Including all four link states ensures that the button doesn’t disappear when a user hovers or clicks on it. You can also set different parameters for hover and active links, e.g. changing the button or text color.

The background color is set with background-color, and text color with color. Padding defines the size of box—the text is padded by 10px vertically and 25px horizontally.

Text-align ensures that the text is displayed in the center of the button, instead of off to one side. Text-decoration, as we saw in the last example, removes the underline.

The CSS code “display: inline-block” is a bit more complicated. In short, it lets you set the height and width of the object. It also ensures that it starts a new line when it’s inserted.

6\. Create a Text Box
---------------------

A plain paragraph isn’t very exciting. If you want to highlight an element on your page, you might want to add a border. Here’s how to do that with a string of CSS code:

```
p.important {  
  
border-style: solid;  
  
border-width: 5px;  
  
border-color: purple;  
  
}
```

This one is straightforward. It creates a solid purple border, five pixels wide, around any important-class paragraph. To make a paragraph inherit these properties, just declare it like this:

```


Your important paragraph here.


```

This will work regardless however big the paragraph is.

There are many different border styles you can apply; instead of “solid,” try “dotted” or “double.” Meanwhile, the width can be “thin,” “medium,” or “thick.” CSS code can even define the thickness of each border individually, like this:

```
border-width: 5px 8px 3px 9px;
```

That results in a top border of five pixels, a right border of eight, a bottom of three, and a left border size of nine pixels.

7\. Center-Align Elements
-------------------------

  
For a very common task, centering elements with CSS code is surprisingly unintuitive. Once you’ve done it a few times though, it becomes much easier. You have a couple of different ways to center things.

For a block element (usually an image), use the margin attribute:

```
.center {  
  
display: block;  
  
margin: auto;  
  
}
```

This ensures that the element is displayed as a block and that the margin on each side is set automatically. If you want to center all the images on a given page, you can even add “margin: auto” to the img tag:

```
img {  
  
margin: auto;  
  
}
```

To learn why it works this way, check out the [CSS box model explanation at W3C](https://www.w3schools.com/css/css_boxmodel.asp).

But what if we want to center text with CSS? Use this sample CSS:

```
.centertext {  
  
text-align: center;  
  
}
```

Want to use the “centertext” class to center the text in a paragraph? Simply add that class to the

tag:

```


This text will be centered.


```

8\. CSS Examples for Adjusting Padding
--------------------------------------

The padding of an element specifies how much space should be on each side. For example, if you add 25 pixels of padding to the bottom of an image, the following text will be pushed 25 pixels down. Many elements can have padding, not just images.

Let’s say you want every image to have 20 pixels of padding on the left and right sides, and 40 pixels on the top and bottom. The most basic execution is:

```
img {  
  
padding-top: 40px;  
  
padding-right: 25px;  
  
padding-bottom: 40px;  
  
padding-left: 25px;  
  
}
```

There’s shorthand CSS code we can use to present all of this information in a single line:

```
img {  
  
padding: 40px 25px 40px 25px;  
  
}
```

This sets the top, right, bottom, and left paddings to the right number. Thanks to only two values being used (40 and 25) we can make it even shorter:

```
img {  
  
padding: 40px 25px  
  
}
```

When you use only two values, the first value is set for the top and bottom, while the second will be left and right.

9\. Highlight Table Rows
------------------------

CSS code make tables look much nicer than the default grids. Adding colors, adjusting borders, and making your table responsive to mobile screens are all easy. We’ll look at just one cool effect here: highlighting table rows when you mouse over them.

Here’s the code you’ll need for that:

```
tr:hover {  
  
background-color: #ddd;  
  
}
```

Now whenever you mouse over a table cell, that row will change color. To see some of the other cool things you can do, check out the [W3C page on fancy CSS tables](https://www.w3schools.com/css/tryit.asp?filename=trycss_table_fancy).

10\. Shifting Images Between Transparent and Opaque
---------------------------------------------------

CSS code can help you do cool things with images, too. Here’s a CSS example to display images at less than full opacity, so they appear slightly “whited out”. When you mouse over the images, they’re brought to full opacity:

```
img {  
  
opacity: 0.5;  
  
filter: alpha(opacity=50);  
  
}
```

The “filter” attribute does the same thing as “opacity,” but internet Explorer 8 and earlier don’t recognize the opacity measurement. For older browsers, it’s a good idea to include it.

Now that the images are slightly transparent, we’ll bring them to fully opaque on a mouseover:

```
img:hover {  
  
opacity: 1.0;  
  
filter: alpha(opacity=100);  
  
}
```

10 CSS Examples With Source Code
--------------------------------

With these CSS code examples, you should have a much better idea of how CSS works. [CSS templates](//www.makeuseof.com/tag/css-template-sites-dont-start-scratch/) can help, but understanding the raw elements is vital.

The 10 easy CSS code examples we’ve looked at:

1.  Easy paragraph formatting
2.  Change letter case
3.  Change link colors
4.  Remove link underlines
5.  Make a link buuton
6.  Create a text box
7.  Center-align elements
8.  Adjust padding
9.  Highlight table rows
10.  Make images opaque

Reviewing them again, you’ll notice several patterns that you can apply to future code. And that’s when you know you’ve really started becoming a CSS master. But remembering it can be tough. You might want to bookmark this page for future reference.

For a quick way to remember some of the things you’ve learnt here, be sure to check out our [CSS3 properties cheat sheet](//www.makeuseof.com/tag/essential-css-properties-cheat-sheet/).

Read the full article: [10 Simple CSS Code Examples You Can Learn in 10 Minutes](https://www.makeuseof.com/tag/simple-css-code-examples/)

  
  
from MakeUseOf https://ift.tt/32PUeFM  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)