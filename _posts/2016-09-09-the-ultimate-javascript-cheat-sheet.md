---
title: 'The Ultimate JavaScript Cheat Sheet'
date: 2020-01-26T01:34:00+01:00
draft: false
---

![Code displayed on a laptop screen](https://static.makeuseof.com/wp-content/uploads/2019/10/code-on-a-laptop-screen.jpeg)

If you want to build dynamic webpages, you’ll have to supplement your HTML and CSS knowledge with [an understanding of JavaScript](//www.makeuseof.com/tag/what-is-javascript/). This scripting language is considered an essential in modern web development.

You can build all kinds of interesting interactive apps and websites with JavaScript, but there’s much to learn on the way. With that in mind, we have created the following JavaScript cheat sheet for you.

The cheat sheet can serve as a quick refresher on JavaScript elements any time you need one. It’s handy for newbies and experts alike.

**FREE DOWNLOAD:** This cheat sheet is available as a **downloadable PDF** from our distribution partner, TradePub. You will have to complete a short form to access it for the first time only. Download [The Ultimate JavaScript Cheat Sheet](https://makeuseof.tradepub.com/c/pubRD.mpl?secure=1&sr=pp&_t=pp:&qf=w_makc19&ch=).

The Ultimate JavaScript Cheat Sheet
-----------------------------------

Shortcut

Action

**JavaScript Arrays**

concat()

Join several arrays into one

copyWithin()

Copy array elements within the array, to and from specified positions

indexOf()

Return the primitive value of the specified object

includes()

Check if an array contains the specified element

join()

Combine elements of an array into a single string and return the string

entries()

Return a key/value pair Array Iteration Object

every()

Check if every element in an array passes a test

fill()

Fill the elements in an array with a static value

filter()

Create a new array with every element in an array that pass a test

find()

Return the value of the first element in an array that pass a test

forEach()

Call a function for each array element

from()

Create an array from an object

lastIndexOf()

Give the last position at which a given element appears in an array

pop()

Remove the last element of an array

push()

Add a new element at the end

reverse()

Sort elements in descending order

reduce()

Reduce the values of an array to a single value (going left-to-right)

reduceRight()

Reduce the values of an array to a single value (going right-to-left)

shift()

Remove the first element of an array

slice()

Pull a copy of a portion of an array into a new array object

sort()

Sort elements alphabetically

splice()

Add elements in a specified way and position

unshift()

Add a new element to the beginning

**JavaScript Boolean Methods**

toString()

Convert a Boolean value to a string, and return the result

valueOf()

Return the first position at which a given element appears in an array

toSource()

Return a string representing the source code of the object

**JavaScript Arithmetic Operators**

+

Addition

\-

Subtraction

\*

Multiplication

/

Division

(...)

Grouping operator (operations within brackets are executed earlier than those outside)

%

Modulus (remainder)

++

Increment numbers

\--

Decrement numbers

\==

Equal to

\===

Equal value and equal type

!=

Not equal

!==

Not equal value or not equal type

\>

Greater than

<

Lesser than

\>=

Greater than or equal to

<=

Lesser than or equal to

?

Ternary operator

**Logical Operators**

&&

Logical AND

||

Logical OR

!

Logical NOT

**Bitwise Operators**

&

AND statement

|

OR statement

~

NOT

^

XOR

<<

Left shift

\>>

Right shift

\>>>

Zero fill right shift

**Functions**

alert()

Output data in an alert box in the browser window

confirm()

Open up a yes/no dialog and return true/false depending on user click

console.log()

Write information to the browser console (good for debugging purposes)

document.write()

Write directly to the HTML document

prompt()

Create a dialog for user input

**Global Functions**

decodeURI()

Decode a Uniform Resource Identifier (URI) created by encodeURI or similar

decodeURIComponent()

Decode a URI component

encodeURI()

Encode a URI into UTF-8

encodeURIComponent()

Same but for URI components

eval()

Evaluate JavaScript code represented as a string

isFinite()

Determine whether a passed value is a finite number

isNaN()

Determine whether a value is an illegal number

Number()

Convert an object's value to a number

parseFloat()

Parse a string and return a floating point number

parseInt()

Parse a string and return an integer

**JavaScript Loops**

for

The most common way to create a loop in JavaScript

while

Set up conditions under which a loop executes

do while

Similar to the while loop, however, it executes at least once and performs a check at the end to see if the condition is met to execute again

break

Stop and exit the cycle if certain conditions are mets

continue

Skip parts of the cycle if certain conditions are met

**Escape Characters**

\\'

Single quote

\\"

Double quote

\\\\

Backslash

\\b

Backspace

\\f

Form feed

\\n

New line

\\r

Carriage return

\\t

Horizontal tabulator

\\v

Vertical tabulator

**JavaScript String Methods**

charAt()

Return a character at a specified position inside a string

charCodeAt()

Give the unicode of character at that position

concat()

Concatenate (join) two or more strings into one

fromCharCode()

Return a string created from the specified sequence of UTF-16 code units

indexOf()

Provide the position of the first occurrence of specified text within a string

lastIndexOf()

Same as indexOf() but with the last occurrence, searching backwards

match()

Retrieve the matches of a string against a search pattern

replace()

Find and replace specified text in a string

search()

Execute a search for a matching text and return its position

slice()

Extract a section of a string and return it as a new string

split()

Split a string object into an array of strings at a specified position

startsWith()

Check whether a string begins with specified characters

substr()

Similar to slice() but extracts a substring depended on a specified number of characters

substring()

Similar to slice() but can’t accept negative indices

toLowerCase()

Convert strings to lower case

toUpperCase()

Convert strings to upper case

valueOf()

Return the primitive value (that has no properties or methods) of a string object

**REGULAR EXPRESSION SYNTAX**  
  
**Pattern Modifiers**

e

Evaluate replacement

i

Perform case-insensitive matching

g

Perform global matching

m

Perform multiple line matching

s

Treat strings as single line

x

Allow comments and whitespace in pattern

U

Ungreedy pattern

**Brackets**

\[abc\]

Find any of the characters in the brackets

\[^abc\]

Find any character not in the brackets

\[0-9\]

Find digit specified in the brackets

\[A-z\]

Find any character from uppercase A to lowercase z

(a|b|c)

Find any of the alternatives separated with |

**Metacharacters**

.

Find a single character, except newline or line terminator

\\w

Word character

\\W

Non-word character

\\d

A digit

\\D

A non-digit character

\\s

Whitespace character

\\S

Non-whitespace character

\\b

Find a match at the beginning/end of a word

\\B

Find a match not at the beginning/end of a word

\\u0000

NUL character

\\n

A new line character

\\f

Form feed character

\\r

Carriage return character

\\t

Tab character

\\v

Vertical tab character

\\xxx

Character specified by an octal number xxx

\\xdd

Latin character specified by a hexadecimal number dd

\\udddd

Unicode character specified by a hexadecimal number dddd

**Quantifiers**

n+

Match any string that contains at least one n

n\*

Any string that contains zero or more occurrences of n

n?

Any string that contains zero or one occurrences of n

n{X}

Any string that contains a sequence of X n’s

n{X,Y}

Strings that contains a sequence of X to Y n’s

n{X,}

Matches any string that contains a sequence of at least X n’s

n$

Any string with n at the end of it

^n

String with n at the beginning of it

?=n

Any string that is followed by a specific string n

?!n

String that is not followed by a specific string n

**Number Properties**

MAX\_VALUE

Maximum numeric value representable in JavaScript

MIN\_VALUE

Smallest positive numeric value representable in JavaScript

NaN

The “Not-a-Number” value

NEGATIVE\_INFINITY

Negative Infinity value

POSITIVE\_INFINITY

Positive Infinity value

**Number Methods**

toExponential()

Return a string with a rounded number written as exponential notation

toFixed()

Return string of a number with a specified number of decimals

toPrecision()

Return string of a number written with a specified length

toString()

Return a number as a string

valueOf()

Return a number as a number

**Math Properties**

E

Euler’s number

LN2

Natural logarithm of 2

LN10

Natural logarithm of 10

LOG2E

Base 2 logarithm of E

LOG10E

Base 10 logarithm of E

PI

The number PI

SQRT1\_2

Square root of 1/2

SQRT2

Square root of 2

**Math Methods**

abs(x)

Return the absolute (positive) value of x

acos(x)

Arccosine of x, in radians

asin(x)

Arcsine of x, in radians

atan(x)

Arctangent of x as a numeric value

atan2(y,x)

Arctangent of the quotient of its arguments

ceil(x)

Value of x rounded up to its nearest integer

cos(x)

Cosine of x (x is in radians)

exp(x)

Value of Ex

floor(x)

Value of x rounded down to its nearest integer

log(x)

Natural logarithm (base E) of x

max(x,y,z,...,n)

Number with highest value

min(x,y,z,...,n)

Number with lowest value

pow(x,y)

X to the power of y

random()

Random number between 0 and 1

round(x)

Value of x rounded to its nearest integer

sin(x)

Sine of x (x is in radians)

sqrt(x)

Square root of x

tan(x)

Tangent of an angle

**Dates**

Date()

Create a new date object with the current date and time

Date(2017, 5, 21, 3, 23, 10, 0)

Create a custom date object. The numbers represent year, month, day, hour, minutes, seconds, milliseconds. You can omit anything you want except for year and month.

Date(“2017-06-23”)

Date declaration as a string

getDate()

Get the day of the month as a number (1-31)

getDay()

Get the weekday as a number (0-6)

getFullYear()

Get the year as a four digit number (yyyy)

getHours()

Get the hour (0-23)

getMilliseconds()

Get the millisecond (0-999)

getMinutes()

Get the minute (0-59)

getMonth()

Get the month as a number (0-11)

getSeconds()

Get the second (0-59)

getTime()

Get the time (milliseconds since January 1, 1970)

getUTCDate()

Day (date) of the month in the specified date according to universal time (also available for day, month, fullyear, hours, minutes etc.)

parse

Parse a string representation of a date, and return the number of milliseconds since January 1, 1970

setDate()

Set the day as a number (1-31)

setFullYear()

Set the year (optionally month and day)

setHours()

Set the hour (0-23)

setMilliseconds()

Set the milliseconds (0-999)

setMinutes()

Set the minutes (0-59)

setMonth()

Set the month (0-11)

setSeconds()

Set the seconds (0-59)

setTime()

Set the time (milliseconds since January 1, 1970)

setUTCDate()

Set the day of the month for a specified date according to universal time (also available for day, month, fullyear, hours, minutes etc.)

**DOM MODE **  
  
**Node Properties**

attributes

Live collection of all attributes registered to an element

baseURI

Absolute base URL of an HTML element

childNodes

Collection of an element’s child nodes

firstChild

First child node of an element

lastChild

Last child node of an element

nextSibling

Next node at the same node tree level

nodeName

Name of a node

nodeType

Type of a node

nodeValue

Value of a node

ownerDocument

Top-level document object for current node

parentNode

Parent node of an element

previousSibling

Node immediately preceding the current one

textContent

Textual content of a node and its descendants

**Node Methods**

appendChild()

Add a new child node to an element as the last child node

cloneNode()

Clone HTML element

compareDocumentPosition()

Compare the document position of two elements

getFeature()

Return an object which implements the APIs of a specified feature

hasAttributes()

Return true if an element has any attributes, else return false

hasChildNodes()

Return true if an element has any child nodes, else return false

insertBefore()

Insert a new child node before a specified, existing child node

isDefaultNamespace()

Return true if a specified namespaceURI is the default, else return false

isEqualNode()

Check if two elements are equal

isSameNode()

Check if two elements are the same node

isSupported()

Return true if a specified feature is supported on the element

lookupNamespaceURI()

Return the namespaceURI associated with a given node

lookupPrefix()

Return a DOMString containing the prefix for a given namespaceURI, if present

normalize()

Join adjacent text nodes and remove empty text nodes in an element

removeChild()

Remove a child node from an element

replaceChild()

Replace a child node in an element

**Element Methods**

getAttribute()

Return the specified attribute value of an element node

getAttributeNS()

Return string value of the attribute with the specified namespace and name

getAttributeNode()

Get the the specified attribute node

getAttributeNodeNS()

Return the attribute node for the attribute with the given namespace and name

getElementsByTagName()

Provide a collection of all child elements with the specified tag name

getElementsByTagNameNS()

Return a live HTML collection of elements with a certain tag name belonging to the given namespace

hasAttribute()

Return true if an element has any attributes, else return false

hasAttributeNS()

Provide a true/false value indicating whether the current element in a given namespace has the specified attribute

removeAttribute()

Remove a specified attribute from an element

removeAttributeNS()

Remove the specified attribute from an element within a certain namespace

removeAttributeNode()

Take away a specified attribute node and return the removed node

setAttribute()

Set or change the specified attribute to a specified value

setAttributeNS()

Add a new attribute or change the value of an attribute with the given namespace and name

setAttributeNode()

Set or change the specified attribute node

setAttributeNodeNS()

Add a new namespaced attribute node to an element

**Browser Window Properties**

closed

Check whether a window has been closed or not and return true or false

defaultStatus

Set or return the default text in the statusbar of a window

document

Return the document object for the window

frames

Return all iframe elements in the current window

history

Provide the History object for the window

innerHeight

Inner height of a window’s content area

innerWidth

Inner width of the content area

length

Return the number of iframe elements in the window

location

Return the location object for the window

name

Set or return the name of a window

navigator

Return the Navigator object for the window

opener

Return a reference to the window that created the window

outerHeight

Outer height of a window, including toolbars/scrollbars

outerWidth

Outer width of a window, including toolbars/scrollbars

pageXOffset

Number of pixels by which the document has been scrolled horizontally

pageYOffset

Number of pixels by which the document has been scrolled vertically

parent

Parent window of the current window

screen

Return the Screen object for the window

screenLeft

Horizontal coordinate of the window (relative to screen)

screenTop

Vertical coordinate of the window

screenX

Same as screenLeft but needed for some browsers

screenY

Same as screenTop but needed for some browsers

self

Return the current window

status

Set or return the text in the statusbar of a window

top

Return the topmost browser window

**Browser Window Methods**

alert()

Display an alert box with a message and an OK button

blur()

Remove focus from the current window

clearInterval()

Clear a timer set with setInterval()

clearTimeout()

Clear a timer set with setTimeout()

close()

Close the current window

confirm()

Display a dialog box with a message and OK and Cancel buttons

focus()

Set focus to the current window

moveBy()

Move a window relative to its current position

moveTo()

Move a window to a specified position

open()

Open a new browser window

print()

Print the content of the current window

prompt()

Display a dialog box that prompts the visitor for input

resizeBy()

Resize the window by the specified number of pixels

resizeTo()

Resize the window to a specified width and height

scrollBy()

Scroll the document by a specified number of pixels

scrollTo()

Scroll the document to specified coordinates

setInterval()

Call a function or evaluate an expression at specified intervals

setTimeout()

Call a function or evaluate an expression after a specified interval

stop()

Stop the window from loading

**Screen Properties**

availHeight

Return the height of the screen (excluding the Windows Taskbar)

availWidth

Return the width of the screen (excluding the Windows Taskbar)

colorDepth

Return the bit depth of the color palette for displaying images

height

The total height of the screen

pixelDepth

The color resolution of the screen in bits per pixel

width

The total width of the screen

**JAVASCRIPT EVENTS**  
  
**JavaScript Mouse Events**

onclick

When user clicks on an element

oncontextmenu

When user right-clicks on an element to open a context menu

ondblclick

When user double-clicks on an element

onmousedown

When user presses a mouse button over an element

onmouseenter

When user moves pointer onto an element

onmouseleave

When user moves pointer away from an element

onmousemove

When user moves pointer while it is over an element

onmouseover

When user moves pointer onto an element or one of its children

onmouseout

When user moves pointer away from an element or one of its children

onmouseup

When user releases a mouse button while over an element

**JavaScript Keyboard Events**

onkeydown

When user is pressing a key down

onkeypress

When user starts pressing a key

onkeyup

When user releases a key

**JavaScript Frame Events**

onabort

When loading of media is aborted

onbeforeunload

Before the document is about to be unloaded

onerror

When an error occurs while loading an external file

onhashchange

When the anchor part of a URL has changed

onload

When an object has loaded

onpagehide

When user navigates away from a webpage

onpageshow

When user navigates to a webpage

onresize

When user resizes document view

onscroll

When user is scrolling an element’s scrollbar

onunload

When a page has unloaded

**JavaScript Form Events**

onblur

When an element loses focus

onchange

When the content of a form element changes (for **input**, **select**, and **textarea**)

onfocus

When an element gets focus

onfocusin

When an element is about to get focus

onfocusout

When an element is about to lose focus

oninput

User input on an element

oninvalid

When an element is invalid

onreset

When a form is reset

onsearch

When a user types something in a search field (for **input="search"**)

onselect

When user selects some text (for **input** and **textarea**)

onsubmit

When a form is submitted

**JavaScript Drag Events**

ondrag

When user drags an element

ondragend

When user has finished dragging the element

ondragenter

When the dragged element enters a drop target

ondragleave

When the dragged element leaves the drop target

ondragover

When the dragged element is on top of the drop target

ondragstart

When user starts to drag an element

ondrop

Dragged element is dropped on the drop target

**JavaScript Clipboard Events**

oncopy

When user copies content of an element

oncut

When user cuts an element’s content

onpaste

When user pastes content in an element

**JavaScript Media Events**

onabort

When media loading is aborted

oncanplay

When browser can start playing media (e.g. a file has buffered enough)

oncanplaythrough

When browser can play through media without stopping

ondurationchange

When duration of media changes

onended

When media has reached its end

onerror

When an error occurs while loading an external file

onloadeddata

When media data is loaded

onloadedmetadata

When metadata (like dimensions and duration) is loaded

onloadstart

When browser starts looking for specified media

onpause

When media is paused either by user or automatically

onplay

When media has been started or is no longer paused

onplaying

When media is playing after having been paused or stopped for buffering

onprogress

When browser is in the process of downloading media

onratechange

When playing speed of media changes

onseeked

When user has finished moving/skipping to a new position in media

onseeking

When user starts moving/skipping

onstalled

When browser is trying to load unavailable media

onsuspend

When browser is intentionally not loading media

ontimeupdate

The playing position has changed (e.g. because of fast forward)

onvolumechange

When media volume has changed (including mute)

onwaiting

When media has paused but is expected to resume (for example, buffering)

**Animation**

animationend

When CSS animation is complete

animationiteration

When CSS animation is repeated

animationstart

When CSS animation has started

**Miscellaneous**

transitionend

When CSS transition is complete

onmessage

When a message is received through the event source

onoffline

When browser starts to work offline

ononline

When browser starts to work online

onpopstate

When the window’s history changes

onshow

When a **menu** element is shown as a context menu

onstorage

When a Web Storage area is updated

ontoggle

When user opens or closes the **details** element

onwheel

When mouse wheel rolls up or down over an element

ontouchcancel

When screen touch is interrupted

ontouchend

When user’s finger goes off touch screen

ontouchmove

When user drags a finger across the screen

Explore JavaScript Further
--------------------------

We consider [JavaScript one of the top programming languages to master](//www.makeuseof.com/tag/top-programming-language-learn-future/) for the future. And we recommend diving into advanced concepts like [JavaScript array methods](//www.makeuseof.com/tag/javascript-array-methods/) once you have a grasp of the basics of JavaScript.

Image Credit: [Oskar Yildiz](https://unsplash.com/@oskaryil) on [Unsplash](https://unsplash.com/photos/cOkpTiJMGzA)

Read the full article: [The Ultimate JavaScript Cheat Sheet](https://www.makeuseof.com/tag/ultimate-javascript-cheat-sheet/)

  
  
from MakeUseOf https://ift.tt/38BrWSD  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)