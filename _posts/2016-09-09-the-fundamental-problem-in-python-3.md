---
title: 'The Fundamental Problem in Python 3'
date: 2019-12-20T07:46:00+01:00
draft: false
---

![](https://s0.wp.com/i/blank.jpg "The Fundamental Problem in Python 3 | The Changelog")  

> “In the beginning the Universe was created. This has made a lot of people very angry and been widely regarded as a bad move.”
> 
> – _Douglas Adams_

This expands on my recent post [The Incredible Disaster of Python 3](https://changelog.complete.org/archives/10053-the-incredible-disaster-of-python-3). I seem to have annoyed the Internet…

Back in the mists of time, Unix was invented. Today the descendants of Unix, whether literal or in spirit, power the majority of the world’s cell phones, most of the most popular sites on the Internet, etc. And among this very popular architecture, there lies something that has made people very angry at times: on a Unix filesystem, 254 bytes are valid in filenames. The two that are not are 0x00 and the slash character. Otherwise, they are valid in virtually any combination (the special entries “.” and “..” being the exception).

This property has led to a whole host of bugs, particularly in shell scripts. A filename with a leading dash might look like a parameter to a tool. Filenames can contain newline characters, space characters, control characters, and so forth; running ls in a directory with maliciously-named files could certainly scramble one’s terminal. These bugs continue to persist, though modern shells offer techniques that — while optional — can be used to avoid most of these classes of bugs.

It should be noted here that not every valid stream of bytes constitutes a stream of bytes that can be decoded as UTF-8. This is a departure from earlier encoding schemes such as iso-8859-1 and cp437; you might get gibberish, but “garbage in, garbage out” was a thing and if your channel was 8-bit clean, your gibberish would survive unmodified.

Unicode brings many advantages, and has rightly become the predominant standard for text encoding. But the previous paragraph highlights one of the challenges, and this challenge, along with some others, are at the heart of the problem with Python 3. That is because, at a fundamental level, **Python 3’s notion of a filename is based on a fiction.** Not only that, but it tries to introduce strongly-typed strings into what is fundamentally a weakly-typed, dynamic language.

**A quick diversion: The Rust Perspective**

The Unicode problem is a problematic one, and it may be impossible to deal with it with complete elegance. Many approaches exist; here I will describe Rust’s string-related types, of which there are three for our purposes:

*   The **String** (and related **&str**) is used for textual data and contains bytes that are guaranteed to be valid UTF-8 at all times
*   The **Vec** (and related **\[u8\]**) is a representation of pure binary bytes, of which all 256 possible characters are valid in any combination, whether or not it forms valid UTF-8
*   And the **Path**, which represents a path name on the system.

The Path uses the underlying operating system’s appropriate data type (here I acknowledge that Windows is very different from POSIX in this regard, though I don’t go into that here). Compile-time errors are generated when these types are mixed without proper safe conversion.

**The Python Fiction**

Python, in contrast, has only two types; roughly analogous to the String and the Vec in Rust. Critically, most of the Python standard library treats a filename as a String – that is, a sequence of valid Unicode code points, which is a **subset** of the valid POSIX filenames.

Do you see what we just did here? We’ve set up another shell-like situation in which filenames that are valid on the system create unexpected behaviors in a language. Only this time, it’s not \\n, it’s things like \\xF7.

From a POSIX standpoint, the correct action would have been to use the bytes type for filenames; this would mandate proper encode/decode calls by the user, but it would have been quite clear. It should be noted that some of the most core calls in Python, such as open(), do accept both bytes and strings, but this behavior is by no means consistent in the standard library, and some parts of the library that process filenames (for instance, listdir in its most common usage) return strings.

**The Plot Thickens**

At some point, it was clearly realized that this behavior was leading to a lot of trouble on POSIX systems. Having a listdir() function be unable (in its common usage; see below) to handle certain filenames was clearly not going to work. So Python introduced its _surrogate escape_. When using surrogate escapes, when attempting to decode a binary byte that is not valid in UTF-8, it is replaced with a multibyte UTF-8 sequence from Unicode code space that is otherwise rarely used. Then, when converted back to a binary sequence, this Unicode code point is converted to the same original byte. However, this is not a systemwide default and in many cases must be specifically requested.

And now you see this is both an ugly kludge and a violation of the promise of what a string is supposed to be in Python 3, since this doesn’t represent a valid Unicode character at all, but rather a token for the notion that “there was a byte here that we couldn’t convert to Unicode.” Now you have a string that the system thinks is Unicode, that looks like Unicode, that you can process as Unicode — substituting, searching, appending, etc — but which is actually at least partially representing things that should rightly be unrepresentable in Unicode.

And, of course, surrogate escapes are not universally used by even the Python standard library either. So we are back to the problem we had in Python 2: what the heck is a string, anyway? It might be all valid Unicode, it might have surrogate escapes in it, it might have been decoded from the wrong locale (because life isn’t perfect), and so forth.

**Unicode Realities**

The article [pragmatic Unicode](https://nedbatchelder.com/text/unipain.html) highlights these facts:

1.  Computers are built on bytes
2.  The world needs more than 256 symbols
3.  You cannot infer the encoding of bytes — you must be told, or have to guess
4.  Sometimes you are told wrong

I have no reason to quibble with this. How, then, does that stack up with this code from Python? (From zipfile.py, distributed as part of Python)

```
  
 if flags & 0x800:  
 # UTF-8 file names extension  
 filename = filename.decode('utf-8')  
 else:  
 # Historical ZIP filename encoding  
 filename = filename.decode('cp437')  
 
```

There is a reason that Python [can’t extract a simple ZIP file properly](https://bugs.python.org/issue38861). The snippet above violated the third rule by inferring a cp437 encoding when it shouldn’t. But it’s worse; the combination of factors leads extracall() to essentially convert a single byte from CP437 to a multibyte Unicode code point on extraction, rather than simply faithfully reproducing the bytestream that was the filename. Oh, and it doesn’t use surrogate escapes. Good luck with that one.

**It gets even worse**

Let’s dissect Python’s disastrous [documentation on Unicode filenames](https://docs.python.org/3.8/howto/unicode.html#unicode-filenames).

First, we begin with the premise that [there is no filename encoding](http://lucumr.pocoo.org/2014/5/12/everything-about-unicode/) in POSIX. Filenames are just blobs of bytes. There is no filename encoding!

What about $LANG and friends? They give hints about the environment, languages for interfaces, and terminal encoding. They can often be the best HINT as to how we should render characters and interpret filenames. But they do not subvert the fundamental truth, which is that POSIX filenames do not have to conform to UTF-8.

So, back to the Python documentation. Here are the problems with it:

*   It says that there will be a filesystem encoding if you set LANG or LC\_CTYPE, falling back to UTF-8 if not specified. As we have already established, UTF-8 can’t handle POSIX filenames.
*   It gets worse: “The os.listdir() function returns filenames, which raises an issue: should it return the Unicode version of filenames, or should it return bytes containing the encoded versions? os.listdir() can do both”. So we are somewhat tacitly admitting here that str was a poor choice for filenames, but now we try to have it every which way. This is going to end badly.
*   And then there’s this gem: “Note that on most occasions, you should can just stick with using Unicode with these APIs. The bytes APIs should only be used on systems where undecodable file names can be present; that’s pretty much only Unix systems now.” Translation: **Our default advice is to pretend the problem doesn’t exist, and will cause your programs to be broken or crash on POSIX.**

**Am I just living in the past?**

This was the most common objection raised to my prior post. “Get over it, the world’s moved on.” Sorry, no. I laid out the case for proper handling of this in my previous post. But let’s assume that your filesystems are all new, with shiny UTF-8 characters. It’s STILL a problem. Why? Because it is likely that an errant or malicious non-UTF-8 sequence will cause a lot of programs to crash or malfunction.

We know how this story goes. All the shell scripts that do the wrong thing when “; rm” is in a filename, for instance. Now, Python is not a shell interpreter, but if you have a program that crashes on a valid filename, you have — at LEAST — a vector for denial of service. Depending on the circumstances, it could turn into more.

**Conclusion**

*   Some Python 3 code is going to crash or be unable to process certain valid POSIX filenames.
*   Some Python 3 code might use surrogate escapes to handle them.
*   Some Python 3 code — part of Python itself even — just assumes it’s all from cp437 (DOS) and converts it that way.
*   Some people recommend using latin-1 instead of surrogate escapes – even official Python documentation covers this.

The fact is: A Python string is the WRONG data type for a POSIX filename, and so numerous, incompatible kludges have been devised to work around this problem. There is no consensus on which kludge to use, or even whether or not to use one, even within Python itself, let alone the wider community. We are going to continue having these problems as long as Python continues to use a String as the fundamental type of a filename.

Doing the right thing in Python 3 is [extremely hard](http://lucumr.pocoo.org/2014/5/12/everything-about-unicode/), not obvious, and rarely taught. This is a recipe for a generation of buggy code. Easy things should be easy; hard things should be possible. Opening a file correctly should be easy. Sadly I fear we are in for many years of filename bugs in Python, because this would be hard to fix now.

**Resources**

(For even more fun, consider command line parameters and environment variables! I’m annoyed enough with filenames to leave those alone for now.)

  
  
from Hacker News https://ift.tt/2DcSDzm