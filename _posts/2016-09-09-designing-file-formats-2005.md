---
title: 'Designing File Formats (2005)'
date: 2019-10-13T11:04:00+01:00
draft: false
---

Designing File Formats
======================

There are many, many file formats, largely owing to the existence of many, many different kinds of files. They range from simple ASCII text documents to complex databases. There are a few elements that should be part of any structured file, but many designers fail to include them.

The header of a good file format has, at a minimum, the following elements:

*   Identification bytes ("magic number" or ID string)
*   Header checksum
*   Version number
*   Offset to data

This applies equally to data that never actually gets stored in a file, such as data sent over a network to a portable device.

### Identification Bytes

The "magic number" has a long history. It's usually a sequence of 2 to 4 bytes that more-or-less uniquely identify a binary file format. Some attempt must be made to avoid values that are likely to occur naturally, so using a string of ASCII text characters is a poor choice if the file could be mixed with text documents. As storage capacities have increased, short magic numbers have been replaced with slightly longer strings.

Identification bytes are most useful on systems that don't have strong typing, such as a UNIX filesystem. On a Macintosh HFS filesystem it's hard to divorce a file from its file and creator types, but under Windows you can change the type of a file by renaming it.

They remain useful on all systems as a sanity check: it's an assurance that what you are reading from the file matches your expectations of the contents. If the file type information in the filename is lost, perhaps during a network data transfer, you can make a highly educated guess at the file contents. Some would argue that they're unnecessary for "internal use" data in a closed system, but during development it works like an "assert" statement, immediately notifying you if you try to load the wrong kind of file or a file that was severely corrupted.

The all-time coolest identification string goes to the [PNG graphics file format](http://libpng.org/pub/png/spec/iso/index-object.html#5PNG-file-signature), which looks like this:

```
 (decimal) 137 80 78 71 13 10 26 10 (hexadecimal) 89 50 4e 47 0d 0a 1a 0a (ASCII C notation) \\211 P N G \\r \\n \\032 \\n
```

The first byte is non-ASCII to avoid confusion with text files. The next three make it obvious to human eyes that this is a PNG file. The \\r\\n sequence allows a quick test for conversions from CRLF to CR or LF, and the \\n at the end tests for conversions from LF to CR or CRLF. The second-to-last byte is a Ctrl-Z, used on some systems as an end-of-file marker in text files. Not only does it detect improper text handling, it also stops you from getting a screen full of garbage if you "type" the file under MS-DOS.

ASCII file formats can benefit from ID strings, because applications that read them can tell immediately whether they have the right kind of file. When receiving a data stream over a network, the ID string can serve to identify the nature of the incoming data.

### Header Checksum

This could be anything from a single-byte checksum to a 32-bit CRC to a 128-bit MD5 hash. The checksum immediately follows the magic number, and is applied to everything that follows the checksum and precedes the start of data (as identified by the "offset to data" field). It lets you know with a high degree of certainty that what you are reading from the file's header matches what was written.

Many developers view internal checksums as unnecessary, and they have a valid point. TCP/IP networks are very reliable, and if you can't trust the data on your hard drive then you have some serious issues. However, there are still valid reasons for checking your headers.

For one, storage is less stable than you might think. I received numerous questions in the early days of CD recording about recorders that worked well for audio CDs, text files, and JPEG images, but failed when storing ZIP archives. What they didn't realize is that only the ZIP archives had CRCs in them. All of the data being written was damaged, usually by a flaky SCSI or IDE cable, but the errors were so rare that they weren't noticeable in many types of files. You may not notice that your text file has become a "tixt" file or that your vacation picture has a few extra spots, but a 32-bit CRC is rarely fooled by errors.

Another common way to damage files is with ASCII-mode FTP transfers, which do end-of-line conversions (e.g. LF to CRLF). Having bytes altered or shuffled around can cause all sorts of interesting problems. With a header checksum, you can immediately detect any damage to the header. If you trust the code creating the file, you can assume the header is valid, and reduce the amount of error checking your code has to perform.

There is a school of thought that says the header checksum should actually be the \*last\* bit of data written to the header, e.g. it's always found at (OffsetToData-4). This allows the CRC to cover the entire header (including the magic number, though testing that again is redundant), but more importantly it allows the header to be written as a stream over a network. You can compute the CRC as you write the header bytes out, and don't have to seek back to fill it in. Generally speaking, file headers are small and don't require this type of treatment, but it's something to keep in mind.

### Version Number

This should be the most obviously necessary field. Applications and file formats evolve over time, and it's important to be able to determine whether the contents of a file are readable or not. There are two basic approaches, "serial" and "major/minor".

The serial approach uses a single value, often stored in one byte. The number starts at 0 or 1 and increments. The application can recognize and handle what it recognizes as the "current" version, as well as some set of prior versions, but rejects anything newer than what it understands.

The major/minor approach uses two values. The major version works like the "serial" version. Anything older can (usually) be handled, anything newer is rejected. The minor version starts at 0 for each major version, and goes up when new fields are added. Older fields are left untouched, and are filled out even when obsolete. This approach is useful for backward compatibility: older applications can read the newer files, because the fields expected by an application written for a given minor version are guaranteed to exist. If the file's minor version is lower, the application knows how to parse the file. If the file's minor version is greater, the application knows that all of the fields it is aware of are present, and it can just ignore the newer fields. If a major file redesign is necessary, updating the major number prevents older applications from trying to parse newer files.

File version numbers should not be tied to application version numbers, and do not need to be hairy things like "1.3.5d1". One or two steadily increasing values are sufficient.

It is possible to avoid explicit version numbering if you provide for it in other ways. For example, the PNG format uses named "chunks". If the data format needs to change, the chunk type name is altered. The overall file structure does not change, and the version number is effectively embedded in the chunk name (or perhaps even within the chunk itself). This approach only works if you're sure that the overall file format never needs to change.

Some file formats will include a "minimum application version" number. This sounds a bit like putting the cart before the horse: the application is best equipped to decide whether or not it can handle a given file format. File format versions should be stored in applications, not the other way around. The justification for this sort of versioning is backward compatibility, because it allows the file format designer to tell applications whether or not they're able to read the file. This is better handled with the major/minor versioning scheme described above.

### Offset to Data

The benefits of this field aren't immediately obvious unless you consider backward compatibility. An older application can read newer data files so long as it knows how to find the fields it cares about and skip the ones it doesn't. The offset to data tells the application how to skip the unrecognized header fields.

The offset should always be measured from the start of the file. This makes arithmetic trivial for accesses in a real file (seek with SEEK\_SET) or a memory buffer (add to the buffer pointer after casting to a char\*).

You may be tempted to use this field as a version number. For example, Windows uses sizeof() to determine versions for many types of structures, e.g. bitmaps. Resist this temptation. It locks you into a situation where your files must always grow larger. It's reasonable for Windows API structures, which must retain binary compatibility across multiple versions, but unless you insist on full backward binary compatibility, forever and always, this is a bad decision to make at design time.

This field isn't necessary in an ASCII file format, which will have some sort of explicit "data starts here" after a variable-length header.

### Other Fields

Some formats have complex structures. They might have multiple data fields each of which deserves an offset, or have linked lists of objects. Whether these fields go into the file header or into some sort of "block header" is up to you as the file format designer.

One field you should seriously consider adding is a length field. For a file on disk, the length of the data is implied by the length of the file. However, having an embedded length will let you detect if the file was inadvertently truncated (perhaps while being downloaded from the web), and is very important if your data is ever streamed over a network.

Other Considerations
--------------------

### Struct Slurping

It is tempting to read and write files directly from C structs. This is usually done in the name of efficiency or code minimization.

Resist the temptation. Historically, this has been a horrible idea, because structure padding and organization can vary across platforms, compilers, and even different versions of one compiler. Standardized approaches to C compilers and explicit "pragmas" have mostly done away with these issues, but your best bet for compatibility is to write fields individually.

Use the standard libc buffered I/O functions (fopen, fread, fwrite, getc, putc) or buffered C++ iostreams. It may "feel" slow to call getc or putc on every byte, but remember that these are fairly small macros that operate on a buffer of data. Reading data into a buffer and parsing it yourself will not gain you much in the way of efficiency, and may seriously impact the clarity of your code.

One common mistake to avoid when coding in C/C++ is writing statements like this:

> `unsigned short val = getc(infp) | getc(infp) << 8;`

The trouble with this is that not all compilers evaluate arguments in the same order, so you don't know if the first getc() call on the line will execute first or second. (I suspect ANSI C has defined this, but I wouldn't rely on it being implemented correctly.) It's trivially easy to break this into two consecutive statements, and the compiled code will probably be identical.

Don't forget to check feof() and ferror() (or equivalents) after doing a series of getc() or putc() calls.

### Little-Endian or Big-Endian

The best piece of advice here is to use the format that matches up with the most likely consumer of data. If you're writing a file that will be used predominantly on 80x86 machines, use little-endian ordering for all values. When reading data, you have a choice of assuming that you're running on a little-endian machine or writing portable code. In the former case you can just grab data 2 or 4 bytes at a time and stuff it into integers, in the latter you need to read it a byte at a time and order it appropriately. If you read everything through small functions ("Read16LE" to read a 16-bit little-endian value), you can encapsulate your (non-)portability issues.

If you're more concerned with portability, use an ASCII format instead. Output your values with printf/cout, and input them with scanf/cin. It's usually a good idea to add additional format error checking with this approach though, because users will often edit text files by hand. If you want to be trendy, use XML.

### Checksums on File Data

Putting a CRC on the file data is valuable for the same reasons as putting it on the file header. The best place for a CRC is actually at the end of a chunk of data. This allows you to write the data in a stream, without having to seek back to write the CRC. Very important when streaming data over a network.

A similar argument was made for checksums in file headers, but file headers are (usually) much smaller than the data contained in the file.

### End-of-File Marker

File truncation can occur when files are sent over a network or a disk has bad blocks. Your program can detect truncation by:

*   Having a full file CRC. Best for reliability, worst for performance.
*   Having a full file length in the header. Read until the length is satisfied, not until EOF. If you're not reading the entire file all at once, then seek to (length-1) and try to read one byte.
*   Add an explicit end marker. Seek to the end of the file and read it. The file length can come from the header or from the filesystem (fseek with SEEK\_END).

If you're memory-mapping a large file directly into multiple process address spaces, and don't want the performance overhead of a full-file CRC check, an end marker is a trivial way to make sure you've got the whole thing.

### Documentation

If you create a binary file format, document what every byte means. For example:

```
All values little-endian +00 2B Magic number (0xd5aa) +02 1B Version number (currently 1) +03 1B (pad byte) +04 4B CRC-32 +08 4B Length of data +0c 2B Offset to start of data +xx \[data\]
```

ASCII file formats can be self-documenting if you include comments in the format specification. Create a default config file with lots of comments and keep that in your source tree.

Examples
--------

The [PNG format](http://libpng.org/pub/png/spec/iso/index-object.html#5DataRep) is pretty neat. The identification string is followed by a series of "chunks", each of which is headed by the chunk type and chunk length (so unrecognized chunks can be skipped), and followed by a 32-bit CRC. Instead of changing a version when data formats change, the chunk type is altered. This allows adding chunks that older applications can ignore. This is similar in concept to the "Apple Preferred Format", used on the Apple IIgs (and elsewhere?) for image formats.

A quick look at HTTP (HyperText Transfer Protocol, used to send documents between a web server and your browser) shows that it has a version (part of the request rather than the response), an offset to data (expressed as the first occurrence of two consecutive newlines), but no identification bytes (unnecessary since it's a direct response to a request) or checksum (probably unnecessary). It does have a file length (content-length field), which is vital for servers that return multiple items on one connection.

XML has an identification string and version number, e.g. "". As is typical of structured ASCII files, the data immediately follows the end of the header tag. This is a fairly dynamic format, so no checksum is included.

The [ZIP archive format](http://www.pkware.com/company/standards/appnote/) has a magic number, two versions (the app version that created the archive and the version needed to extract it), a CRC-32, length, and offset to the start of the first file header. The "central directory" is continued at the end of the file, which causes a fairly obvious failure if the file is truncated.

True story: once upon a time I had a substantial collection of data (about 15MB) that was memory-mapped into multiple processes. The data was accessed directly as C-style arrays -- portability wasn't a concern -- but reliability was very important. My file had a version number and a CRC, and the various applications would print helpful messages into an error log if, say, the version number was off. We were in the process of setting up a new installation in Japan, and I was asked to help troubleshoot their installation from my side of the Pacific. I logged in and started flipping through the logs. I found a long stream of "incorrect version" messages. As I continued to look farther, the "incorrect version" messages were replaced with "bad CRC" messages. Apparently some enterprising engineer over in Japan had binary-edited the file to increment the version number. This would have resulted in unpredictable (but most likely \*very bad\*) things happening. The moral of the story is that CRCs can do more than check for accidental errors.

* * *

Copyright © 2005 by [Andy McFadden](http://www.fadden.com/). All Rights Reserved.

  
  
from Hacker News https://ift.tt/33q365t