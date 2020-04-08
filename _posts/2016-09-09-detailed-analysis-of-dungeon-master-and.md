---
title: 'Detailed Analysis of Dungeon Master and Chaos Strikes Back Atari ST Floppy Disks'
date: 2019-09-27T05:07:00+01:00
draft: false
---

### Overview

This document provides a detailed description of the floppy disk used by Dungeon Master and Chaos Strikes Back for Atari ST. All versions of Dungeon Master and Chaos Strikes Back for Atari ST were studied:

*   Dungeon Master version 1.0 English (1987-12-08)
*   Dungeon Master version 1.0 English (1987-12-11)
*   Dungeon Master version 1.1 English
*   Dungeon Master version 1.2 English
*   Dungeon Master version 1.2 German
*   Dungeon Master version 1.3 French
*   Chaos Strikes Back version 2.0 English (Game Disk)
*   Chaos Strikes Back version 2.1 English (Game Disk)

The first part of the document contains general information explaining how data is stored on a floppy disk and how it is read. This technical information is required in order to fully understand the second part of the document that describes the contents of the game's floppy disk and particularly the sectors used by the copy protection scheme.

### Technical background

#### Some definitions

**Floppy disk**: A data storage media in the shape of a disk whose surface is coated with a magnetic material on both sides. You can think of this coating as a huge number of tiny magnets that can be oriented as desired. Each magnet creates a small magnetic field and has a north pole and a south pole. Identical poles repel themselves while different poles attract themselves.  
[![Floppy Disk](http://dmweb.free.fr/files/thumbnails/TechDoc-FloppyDiskThumbnail.png "Floppy Disk")](http://dmweb.free.fr/files/TechDoc-FloppyDisk.png "Floppy Disk")  
**Floppy disk drive**: The electromechanical device used to read and write data on floppy disks. Its main components include a motor to rotate the disk, a head to read/write data to disks and a second step by step motor to move the head across the disk.  
[![Floppy Disk Drive](http://dmweb.free.fr/files/thumbnails/TechDoc-FloppyDiskDriveThumbnail.jpg "Floppy Disk Drive")](http://dmweb.free.fr/files/TechDoc-FloppyDiskDrive.jpg "Floppy Disk Drive")  
**Floppy disk controller (FDC)**: An electronic chip connected to the floppy disk drive and designed to manage it. In a computer, programs can only talk with the FDC and never directly with the floppy disk drive.

#### Organizing data on the disk

The physical surface of a floppy disk is homogeneous. However, this surface is logically divided into smaller parts to make it easier to read and write small amounts of data at a time. First, the surface is divided into tracks. A track is a circular area on the floppy disk. On figure 1, the orange area represents a track. Tracks are numbered starting at 0 and the first track is on the outer edge of the surface. The innermost track depicted in green represents the last track.  
Each track is divided into smaller parts called sectors. On figure 1, the red area represents a sector on track 0, the first track. The yellow area represents another sector. While the actual length of these two sectors are very different (the outermost being much longer), every sector contains the same amount of data. Because the drive rotates the floppy disk at a constant angular speed, the drive's head will spend the same amount of time above all sectors, no matter which track they are part of.  
**Figure 1**  
[![Floppy Disk Structure](http://dmweb.free.fr/files/thumbnails/TechDoc-FloppyDiskStructureThumbnail.png "Floppy Disk Structure")](http://dmweb.free.fr/files/TechDoc-FloppyDiskStructure.png "Floppy Disk Structure")

A sector is the smallest area that can be read or written: if you want to read a single byte of data from the floppy disk, you need to read the whole sector and then extract the byte you want from this sector data. Similarly, if you want to write a single byte of data to the floppy disk, you must first read the content of the sector where the byte will be written, modify the byte you want in memory and then write back the whole sector.

When the drive starts to write data to the floppy disk, there is some imprecision to where exactly it will start. In order to avoid any overlap while writing a particular sector, there are areas called 'gaps' between each sector and also between the beginning and end of a track. These gaps provide some tolerance for the start and end locations of sectors. Gaps do not contain any useful user data.

#### Storing binary data using magnetic states

Floppy disks are designed to record digital data, which are series of bits of information ('0' and '1' values). For that purpose, only two different magnetic states are required (contrary to analog recording like on audio tapes).  
The floppy disk surface is virtually divided into small areas. When all the magnets in an area are oriented in the same way, their individual magnetic fields combine themselves to produce a stronger and significant magnetic field, also called a 'magnetic flux'. Information is stored on the disk by creating series of areas where all magnets are oriented in the same way, thus creating two types of magnetized areas: 'north poles areas' or 'south poles areas'. Binary data is stored using these two states, but they do not directly map to bit values (zeros and ones). In fact, each bit is stored using two adjacent magnetized areas, forming what is called a 'bit cell':

*   Two areas with different magnetizations (a north pole and a south pole, in any order) represent a '1' bit. Such a bit cell is said to contain a 'flux reversal'.
*   Two areas with identical magnetization (two north poles or two south poles) represent a '0' bit. Such a bit cell does not contain a 'flux reversal'.

This scheme is necessary because when reading information from the floppy disk, the drive is not able to detect the magnetization of an area as a north pole or a south pole. It can only detect flux reversals.  
As a result, data on a track is stored as regions of opposite magnetization, which is illustrated on figure 1 by the small zoomed portion of a sector.

Changing the orientation of the magnets (in order to write information to the disk) or detecting flux reversals (in order to read information from the disk) relies on the physical phenomenon named 'electromagnetic induction' that has two aspects:

*   A changing magnetic field will create an electric current in a nearby electric circuit. Note that a constant magnetic field will not create any current. This is why only flux reversals can be detected and not the absolute magnetization of the surface.
*   The flow of electicity in an electric circuit produces a magnetic field.

These two aspects are used in the head of a floppy disk drive. The head contains a small coil and is the part of the disk drive that is the closest to the disk surface (without touching it) and allows reading and writing.

#### Reading and writing data

In order to write data to the disk, the computer sends binary data that is converted to a current in the head coil. This current is reversed when a '1' bit is sent and remains the same when a '0' bit is sent. The current in the coil produces a magnetic field whose direction depends on the way the current is flowing in the head. The magnets on the disk surface will then change their orientation to align with the magnetic field produced by the head coil. By using the appropriate electrical signal, it is thus possible to create areas on the disk oriented in one way or the other. The shape of the writing current in the head is represented on figure 2.

In order to read data from the disk, the head is not powered. While moving above the disk surface, the flux reversals on the media will induce electric pulses in the head coil. The presence of an electric pulse is translated to a '1' bit and the absence of pulse is translated to a '0' bit. The shape of the reading current in the head is represented on figure 2.  
Detecting a '1' bit is fairly easy as a pulse is generated, but detecting a '0' bit requires some timing: the floppy disk controller has to wait for some time before concluding that no flux reversal occured when one could have occured. Also, if there was a large number of consecutive '0' bits written on the disk, it would be difficult for the FDC to accurately count these bits. This is why the FDC requires an accurate synchronization with the data flow coming from the head of the floppy drive. This requirement is achieved by two things described in the following sections: an encoding scheme for data written to the disk and a system inside the FDC so that it automatically synchronizes its clock with the electrical pulses it receives while reading from the floppy disk drive.

#### Encoding data

Floppy disks on Atari ST use an encoding named 'Modified Frequency Modulation' (MFM). This simple encoding is used to prevent long series of '0' bits from being written to the floppy disk. In MFM encoding, the stream of data bits that you want to write to the floppy disk is modified by inserting an additional bit, called a clock bit, between each pair of data bits. The value of a clock bit depends on the values of the two data bits around it: if both data bits are '0', then the clock bit is set to '1'. Otherwise, the clock bit is set to '0'.  
This encoding ensures that there are no sequences of more than three consecutive '0' bits.  
Figure 2 illustrates the MFM encoding of two data bytes of value $68 by highlighting the data bits and clock bits with different colors.

Note: this MFM encoding is also used on other computers like on PC. There are also other encodings like FM or GCR.

**Figure 2**  
[![Bit Cells](http://dmweb.free.fr/files/thumbnails/TechDoc-BitCellsThumbnail.png "Bit Cells")](http://dmweb.free.fr/files/TechDoc-BitCells.png "Bit Cells")

#### Synchronizing the FDC

The FDC needs a clock so that it knows the rate at which it should output data bits interpreted from the electrical signal it receives from the floppy disk drive. For this purpose, it uses an 'inspection window' which is a time frame during which the FDC waits for an electrical pulse (a flux reversal) to occur.

The _size_ of a bit cell is the amount of time it takes for the drive's head to move across a bit cell on the disk. On Atari ST, the floppy disk rotates under the head at a constant angular speed of about 300rpm (rotations per minute) but there can be small speed differences from drive to drive (a more or less 1% tolerance).  
For MFM disks on Atari ST, the bit cell size is standard at 2µs (microseconds), but the small possible variations of disk rotation speed means that the bit cell size can appear shorter or longer when read by the FDC.

Note: In this document, a _bit cell_ refers to an area on the disk surface that either contains a flux reversal or does not contain one. Using this definition, an MFM bit cell is 2µs wide. In some other documents, the term _bit cell_ may be used to refer to a bit of useful user data, each of which is stored on the disk as the data bit itself and the additional clock bit. With this alternate definition, an MFM bit cell is 4µs wide because it contains both a data bit and a clock bit.

The FDC contains a part called a 'Phase-Locked Loop' (PLL) which is responsible for automatically adjusting the inspection window to the input signal. When pulses are found, the PLL automatically adjusts the size and position of the inspection window so that pulses occur right in the middle of the inspection window.  
In a perfect case, the inspection window would be exactly 2µs (microseconds) and each pulse would occur exactly in the middle of the inspection window.  
When adjusted, the FDC monitors the electrictal signal for a 2µs time frame. If a pulse occurs during this time frame, the FDC interprets it as a '1' bit and outputs it. If no pulse occurs during this time frame, the FDC interprets it as a '0' bit and outputs it.  
The result is a raw sequence of bits. The next step is to separate the data bits from the clock bits.

#### Separating data bits and clock bits

This task is performed by a part of the FDC called the 'data separator' and is achieved by searching for a very specific bit pattern in the raw sequence of bits. This pattern is called a 'synchronization mark' as it indicates to the data separator where to start its job. This mark is written using a special command of the FDC. It cannot appear in normal user data because the mark violates the MFM encoding rule: it contains a '0' clock bit inserted between two '0' data bits (note that it does not violates the rule of the 3 maximum consecutive '0' bits). This mark is called A1 because it is similar to the encoding of the hexadecimal value $A1. The mark is also noted $4489 as it is the exact value written to disk when including data bits and clock bits.

```
Binary representation of $A1 byte: 1 0 1 0 0 0 0 1 MFM encoded representation of $A1: 100010010101001 The synchronization mark value is: 100010010**_0_**01001 (which is $4489 in hexadecimal)
```

The MFM encoded representation is the value written to the disk when writing $A1 as part of normal data.  
The synchronization mark value is written to the disk when using the appropriate special FDC command. When reading this bit sequence, the FDC will know it is a synchronization mark because one bit (the one in bold) is a '0' instead of the '1' it would be for normal MFM encoded data.  
Once the synchronization mark has been found, it is easy for the FDC to tell which bits are the clock bits and which ones are the data bits.

#### Track layout

The track layout defines the logical structure of a track. Each track contains an 'index mark' to indicate the beginning of the track. This index mark is preceded by a gap and synchronization marks. Gaps are locations where no useful data is written. This data is used to help the PLL synchronization process and also to avoid any overlap between sectors when overwriting a single sector (because there is an imprecision about where the writing will start exactly).  
Following this index mark are the sectors in the track. Each sector contains a header field and a data field. The sector header field is preceded by a gap and synchronization marks. It contains the following information about the sector:

*   the track number
*   the side number (0 or 1 for the two possible sides of the floppy disk)
*   the sector number (sector numbering starts at 1, unlike track numbering that starts at 0)
*   the size of the sector. The possible sizes are 128 bytes, 256 bytes, 512 bytes and 1024 bytes. 512 bytes is the standard sector size on Atari ST.
*   a CRC (Cyclic Redundancy Check) value used to detect errors in the sector header field.

The sector data field is also preceded by a gap and synchronization marks. It contains the following information:

*   the 512 bytes of user data
*   a CRC value used to detect errors in the sector data field.

#### Floppy disk formats

There are many possible floppy disk formats that use varying numbers of tracks, sectors per track and sector sizes. The format of a floppy disk is defined when the disk is formated. When a floppy disk is formated, each track is written at once (not sector by sector), thus defining the number of sectors and their size, the size of gaps, etc. This operation is called low-level formating. High-level formating means installing a file system on the floppy disk. Usually low and high level formating are performed together.

A standard Atari ST floppy disk has two sides, 80 tracks per side (numbered 0 to 79), 9 sectors per track (numbered 1 to 9) and 512 bytes per sector. The resulting storage capacity is 2 sides x 80 tracks x 9 sectors per track x 512 bytes per sector = 737280 Bytes = 720 KB. It is possible to store 10 or even 11 sectors per track by reducing the size of gaps.

### Detailed structure of the games' floppy disk

#### General layout

All versions of Dungeon Master and Chaos Strikes Back for Atari ST use the same floppy disk format. The format is similar to the standard floppy disk format but with 10 sectors per track instead of 9 in order to store more data on the floppy disk. However, they use only one side of the floppy disk (single sided certified floppy disks were cheaper back at that time, and the first generation of Atari ST had only a single sided disk drive). The resulting storage capacity is: 1 side x 80 tracks x 10 sectors per track x 512 bytes per sector = 409600 Bytes = 400 KB.  
This storage capacity is fully used by the game as all sectors contain data. It would have not been possible to store all the game data on a single side of a standard Atari ST floppy disk that could only contain 360 KB.  
While non standard, this format should not be considered a part of the game's copy protection scheme because there is no technical difficulty in copying such a disk format.  
Track 0 contains a standard Atari ST boot sector and file system as well as two special sectors used by the copy protection scheme. The last two sectors in track 0 and all sectors in other tracks are used to store the game's files. These last sectors will not be described further in this document as they are completely standard and just contain the game's program and data files.

#### Track 0, Sector 1: Boot sector

This sector is identical in all versions of Dungeon Master and Chaos Strikes Back for Atari ST.  
When the computer starts, the BIOS performs some hardware initialization, then it tries to boot from the floppy disk.  
For that purpose, it will load in memory the first sector of the first track (sector 1 of track 0).  
The Atari ST BIOS ensures that the floppy disk is bootable. This check is performed by computing a checksum on the 512 bytes of the boot sector data. This checksum algorithm adds the 256 words in the boot sector. If the result is $1234 then the BIOS assumes that the sector is bootable.  
The sector is then executed starting at offset 0.

The floppy disk contains a standard Atari ST boot sector including the default loader code. The boot sector contains:

*   A branch instruction to the beginning of the Loader code.
*   Data describing the floppy disk format.
*   The Loader configuration: instructs the loader code to load and execute the file named SWOOSH.IMG.
*   The Loader code.
*   Padding $00 bytes until the end of the sector.
*   A last word which value is computed so that the checksum of the sector is $1234.

The loader is configured to load in memory the file named SWOOSH.IMG and then run this program.  
The code in the boot sector will load in memory the appropriate sectors containing the File Allocation Table (FAT) and the root directory listing. It will use this data to search for the SWOOSH.IMG file. The file is then loaded in memory at address $40000. The program is then executed starting at address $40000.

Here is an hexadecimal dump of the data in this sector:

```
Offset(h) 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 00000000 60 38 4C 6F 61 64 65 72 00 00 00 00 02 02 01 00 \`8Loader........ 00000010 02 10 00 24 03 F8 02 00 0A 00 01 00 00 00 00 00 ...$.ø.......... 00000020 00 00 00 00 00 00 00 04 00 00 00 00 00 00 53 57 ..............SW 00000030 4F 4F 53 48 20 20 49 4D 47 00 70 07 32 3C 07 77 OOSH IMG.p.2<.w 00000040 48 E7 C0 00 3F 3C 00 25 4E 4E 54 8F 4C DF 00 03 HçÀ.?<.%NNT.Lß.. 00000050 20 7C FF FF 82 40 30 81 04 41 01 11 51 C8 FF E2 |ÿÿ‚@0..A..QÈÿâ 00000060 20 7C FF FF 82 40 70 0F 42 58 51 C8 FF FC 33 FA |ÿÿ‚@p.BXQÈÿü3ú 00000070 FF AE 00 00 04 82 3F 39 00 00 04 46 3F 3C 00 07 ÿ®...‚?9...F?<.. 00000080 4E 4D 58 4F 4A 80 67 00 00 F6 2A 40 41 FA FF 9C NMXOJ€g..ö\*@Aúÿœ 00000090 4A 90 66 06 20 B9 00 00 04 32 30 2D 00 08 E1 48 J.f. ¹...20-..áH 000000A0 D0 80 38 40 D9 FA FF 84 30 3A FF 76 67 10 3C 3A Ð€8@Ùúÿ„0:ÿvg.<: 000000B0 FF 72 38 3A FF 70 26 7A FF 6E 60 00 00 B4 3C 2D ÿr8:ÿp&zÿn\`..´<- 000000C0 00 0A 38 2D 00 08 D8 6D 00 06 26 7A FF 5E 61 00 ..8-..Øm..&zÿ^a. 000000D0 00 B0 66 00 00 AA 20 4C 30 2D 00 06 E1 48 E3 48 .°f..ª L0-..áHãH 000000E0 41 F0 00 00 43 FA FF 48 90 FC 00 20 B1 CC 6D 00 Að..CúÿH.ü. ±Ìm. 000000F0 00 8E 70 0A 12 30 00 00 B2 31 00 00 66 EA 51 C8 .Žp..0..²1..fêQÈ 00000100 FF F4 7E 00 1E 28 00 1B E1 4F 1E 28 00 1A 2C 7A ÿô~..(..áO.(..,z 00000110 FF 1A 26 7A FF 12 42 84 0C 47 0F F0 6C 52 36 07 ÿ.&zÿ.B„.G.ðlR6. 00000120 55 43 C6 ED 00 02 D6 6D 00 0C 0C 44 00 40 6C 08 UCÆí..Öm...D.@l. 00000130 4A 44 67 0E B6 45 67 10 61 46 66 42 E1 8C E3 8C JDg.¶Eg.aFfBáŒãŒ 00000140 D7 C4 3C 03 3A 03 42 84 D8 6D 00 02 DA 6D 00 02 ×Ä<.:.B„Øm..Úm.. 00000150 34 07 E2 4A D4 47 12 36 20 01 E1 49 12 36 20 00 4.âJÔG.6 .áI.6 . 00000160 08 07 00 00 67 02 E8 49 02 41 0F FF 3E 01 60 A8 ....g.èI.A.ÿ>.\`¨ 00000170 4A 44 67 04 61 0A 66 06 2F 3A FE AC 4E 75 60 FE JDg.a.f./:þ¬Nu\`þ 00000180 3F 39 00 00 04 46 3F 06 3F 04 2F 0B 42 67 3F 3C ?9...F?.?./.Bg?< 00000190 00 04 4E 4D DE FC 00 0E 4A 40 4E 75 00 00 00 00 ..NMÞü..J@Nu.... 000001A0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................ 000001B0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................ 000001C0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................ 000001D0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................ 000001E0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 ................ 000001F0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 24 7D ..............$}
```

Detailed content of the boot sector:

Offset

Size

Values

Notes

000

2

60 38

BRA.S instruction to branch to the loader code at offset $3A ($38 bytes forward).

002

6

4C 6F 61 64 65 72 ('Loader' string)

008

3

00 00 00

Volume serial number.

00B

2

00 02 (512)

Number of bytes per sector (Little endian word).

00D

1

02 (2)

Number of sectors per cluster.

00E

2

01 00 (1)

Number of reserved sectors (Little endian word).

010

1

02 (2)

Number of File Allocation Tables (FAT).

011

2

10 00 (16)

Number of entries in the root directory (Little endian word). Each entry is 32 bytes so 16 entries occupy exactly a sector (512 bytes).

013

2

24 03 (804)

Number of sectors on media. This number of sectors is incorrect and should be 800 (80 tracks of 10 sectors).

015

1

F8

Media descriptor.

016

2

02 00 (2)

Number of sectors per FAT (Little endian word).

018

2

0A 00 (10)

Number of sectors per track (Little endian word).

01A

2

01 00 (1)

Number of sides on media (Little endian word).

01C

2

00 00 (0)

Number of hidden sectors (Little endian word).

01E

2

00 00 (0)

A word value that is copied to the system variable named '\_cmdload' (Big endian word).

020

2

00 00 (0)

Load mode (Big endian word). 0 instructs the loader to load a file by its name and using the filesystem. Other values instruct the loader to load a sequence of sectors without refering to the filesystem.

022

2

00 00 (0)

First sector to read (Big endian word). Only used when Load mode is not 0.

024

2

00 00 (0)

Number of sectors to read (Big endian word). Only used when Load mode is not 0.

026

4

00 04 00 00

Load address (Big endian double word). Memory address where the file or sectors will be loaded.

02A

4

00 00 00 00

FAT address (Big endian double word). Memory address where the FAT and root directory data will be loaded. The value $00000000 will automatically select an appropriate address.

02E

11

53 57 4F 4F 53 48 20 20 49 4D 47 'SWOOSH  IMG' string.

File name and extension (8.3 name without the '.'). Only used when Load mode is 0.

039

1

00

Reserved.

03A

n

\-

Boot code (padded with 00 bytes at the end to fill the whole sector).

1FE

2

24 7D

Word value computed so that the checksum of the boot sector is $1234.

#### Track 0, Sectors 2 to 6: File system

The floppy disk is formatted using the FAT12 file system that is used on standard Atari ST floppy disks. The same file system is used on IBM PC floppy disks.  
FAT file systems manage disk space in logical chunks called 'clusters'. A cluster is a set of one or more sectors.  
Each file on the disk is stored in one or more clusters. A cluster is only affected to one file at a time which means that there can be unused (wasted) space at the end of a cluster.  
There is a directory structure that contains an entry for each file. Such an entry stores the file name, the size, the date and time of last modification and the ID of the first cluster used by the file. The other clusters used by the file can be determined by parsing the FAT which is a table with an entry for each cluster on the disk. Each entry in this table contains either the ID of the next cluster of the file, or a special value marking the last cluster of the file.  
For robustness, the FAT is duplicated on two separate locations on the disk to ensure that files can be read even if one sector used to store the FAT itself becomes unreadable.  
On the Dungeon Master and Chaos Strikes Back for Atari ST floppy disks:  
Sectors 2 and 3 store the first FAT  
Sectors 4 and 5 store the second FAT (an exact copy of the first FAT)  
Sector 6 stores the root directory. There can be 16 entries (16 files) in the root directory.

Here is a list of the files that can be found on all versions of the games:

File name

Clusters used

Size and Date/Time

DM 1.0 EN  
(1987-12-08)

DM 1.0 EN  
(1987-12-11)

DM 1.1 EN

DM 1.2 EN

DM 1.2 GE

DM 1.3 FR

CSB 2.0 EN

CSB 2.1 EN

BOOTER

002

1024

1024

1024

1024

1024

1024

1024

1024

08-12-87  
12:34 pm

11-12-87  
11:52 am

07-01-88  
08:53 pm

31-12-99  
04:54 pm

31-12-99  
04:56 pm

20-11-85  
12:04 am

31-12-99  
04:54 pm

31-12-99  
04:54 pm

SWOOSH.IMG

003-005

3016

3016

3016

3016

3016

3016

3016

3016

08-12-87  
12:34 pm

11-12-87  
11:52 am

07-01-88  
08:54 pm

31-12-99  
04:54 pm

31-12-99  
04:56 pm

20-11-85  
12:04 am

31-12-99  
04:54 pm

31-12-99  
04:54 pm

START.PRG

006

770

770

770

770

770

770

770

770

08-12-87  
12:34 pm

11-12-87  
11:52 am

07-01-88  
08:54 pm

31-12-99  
04:55 pm

31-12-99  
04:56 pm

20-11-85  
12:04 am

31-12-99  
04:55 pm

31-12-99  
04:55 pm

GRAPHICS.DAT

007-272

271911

271918

271917

271918

272288

271995

272069

272069

08-12-87  
12:34 am

11-12-87  
02:51 pm

07-01-88  
09:01 pm

18-02-88  
12:18 am

01-03-88  
11:36 am

20-05-88  
06:03 pm

15-11-89  
12:00 am

15-11-89  
12:00 am

START.PAK

273-365 (DM)  
273-368 (CSB)  
372 (CSB 2.1)

95180

95226

95012

95148

95202

95208

97712

98516

08-12-87  
09:19 pm

11-12-87  
03:10 pm

08-01-88  
04:30 pm

24-02-88  
05:06 pm

24-02-88  
04:05 pm

20-05-88  
06:04 pm

15-11-89  
03:59 am

08-01-90  
01:25 pm

DUNGEON.DAT

366-398 (DM)  
369-371 (CSB)

33286

33314

33442

33442

33792

33774

2098

2098

08-12-87  
06:23 am

11-12-87  
02:10 pm

07-01-88  
08:47 pm

01-03-88  
11:04 am

01-03-88  
11:37 am

20-05-88  
06:05 pm

22-04-87  
04:17 am

22-04-87  
04:17 am

Notes:

*   These floppy disks were produced in 1987-1988, yet some files have their dates set to 31-12-99 or 20-11-85!
*   On the floppy disk of Dungeon Master for Atari ST version 1.0 English (1987-12-08), the root directory contains an additional entry for a deleted file (a previous version of the START.PAK file):  
    Name: <$E5>TART.PAK (the first character in the name being replaced by the hexadecimal value $E5 means that the file was deleted)  
    Size: 0 (all the clusters are used by other files)  
    Date/Time: 08-12-87 09:19 pm
*   The SWOOSH.IMG file is identical on all the floppy disks listed in the table above, as well as on the Chaos Strikes Back Utility Disk.
*   The START.PRG file is identical on all the floppy disks listed in the table above, but different from the one found on the Chaos Strikes Back Utility Disk.

#### Track 0, Sector 7: Serial number and protection with fuzzy bits

##### Serial number

On all the floppy disks that have been studied in the making of this document, there are three bytes that are different in each version, making each copy of the games really _unique_. These unique bytes probably form a serial number (because they are preceded by the ASCII string 'Seri') and were probably included during disk duplication when the games were manufactured in the hope that a pirated copy could be more easily identified and located. These three bytes are located at offsets $0D, $0E and $11. The bytes at offsets $0F and $10 may be part of the serial number, but their values are always 00 00 in the disks that were studied. The first 4 bytes may form a little endian 32 bit integer. Here are the values that were found (offsets $0D to $11):

```
9A 03 00 00 B4 Dungeon Master version 1.0 English (1987-12-08) 8F 09 00 00 AB Dungeon Master version 1.0 English (1987-12-11) 61 03 00 00 4F Dungeon Master version 1.1 English 81 04 00 00 48 Dungeon Master version 1.2 English 75 00 00 00 58 Dungeon Master version 1.2 English CA 08 00 00 EF Dungeon Master version 1.2 English 24 12 00 00 1B Dungeon Master version 1.2 German F7 09 00 00 D3 Dungeon Master version 1.3 French AF 01 00 00 83 Dungeon Master version 1.3 French 3E 0E 00 00 1D Dungeon Master version 1.3 French 9A 03 00 00 B4 Chaos Strikes Back version 2.0 English C9 04 00 00 E0 Chaos Strikes Back version 2.0 English 87 02 00 00 A8 Chaos Strikes Back version 2.0 English 35 00 00 00 18 Chaos Strikes Back version 2.1 English CB 03 00 00 E5 Chaos Strikes Back version 2.1 English
```

##### Fuzzy bits

This sector is most interesting because it contains 'fuzzy bits'. A fuzzy bit is a bit whose value seems to be random: if you read the same bit of data several times, the value will sometimes be '0' and it will sometimes be '1'. There are several ways to create fuzzy bits on a floppy disk and they all require the use of special hardware. The floppy disk controller in the Atari ST cannot create them. This is the reason why they are useful as a copy protection mechanism: if you try to copy a sector containing fuzzy bits on a regular Atari ST, the written data will not contain fuzzy bits anymore and will only reflect the bits as they were read when the copy was made. The program can check whether the floppy disk is an original by reading this sector several times and comparing the results. If the value of some bits is different across multiple read operations, then the disk is an original. But if all read operations produce the same result, then the disk is a copy.  
Using this method, it is fairly easy to write a program to detect fuzzy bits. However with the standard FDC in the Atari ST it is not possible to analyse how these fuzzy bits are produced: it is only possible to detect the symptom (bits with random values) but not what causes them.

In order to find out how this works, DrCoolZic performed a very detailed analysis of track 0 on the floppy disk. This was done on an Atari ST equipped with a 'Discovery Cartridge' which is a hardware add-on containing a much more advanced floppy disk controller than the built-in one.

1.  Using the Discovery Cartridge, he made a complete recording of the lowest possible level of information coming from the floppy disk: all the flux reversals on track 0 including the accurate timing between each pair of flux reversals. This high precision record represents the output signal coming out from the floppy disk drive when reading the track. This signal enters the floppy disk controller where the electronics tries to extract meaningful information (the stream of data bits) from the signal.
2.  The recording was transfered to a PC where it was processed by an 'Analyze' program written by DrCoolZic. This program reproduces in software the behavior of the standard Atari ST floppy disk controller with high precision, including the PLL synchronization process.
3.  A first analysis of the sector's content shows that there are no MFM timing violations: consecutive flux reversals are always separated by at least one 0 bit and at most three 0 bits.
4.  A closer analysis of timings shows that some bit cells on the floppy disk do not have normal sizes. This is what causes the fuzzy bits.

The MFM encoding ensures that between two bit cells containing flux reversals (two '1' bits) there are at least one and at most three bit cells without flux reversals ('0' bits). With the standard MFM bit cell being 2µs, it means that two consecutive flux reversals can be spaced only by 4µs, 6µs or 8µs. These three possible patterns are represented on figure 2.  
Or course, depending on the drive speed and other factors, there can be slight variations on these values. The role of the PLL in the FDC is to constantly adapt the inspection window to these variations. The size of the window is adjusted based on the frequency of the flux reversals encountered in the input signal. The position of the window (also called the phase) is adjusted so that flux reversals occur in the middle of the inspection window. Only a few flux reversals are needed for the PLL to be fully synchronized.

Here is a graphic representation of track 0 of the Chaos Strikes Back version 2.1 for Atari ST game disk:  
**Figure 3**  
[![Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0_Screenshot.png](http://dmweb.free.fr/files/thumbnails/Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0_ScreenshotThumbnail.png "Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0_Screenshot.png")](http://dmweb.free.fr/files/Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0_Screenshot.png "Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0_Screenshot.png")

It was generated by [Aufit](http://info-coach.fr/atari/software/pc-projects/Aufit.php) from track data captured with [Kryoflux](http://www.kryoflux.com/). Each point on this graphic represents a flux transition. The X axis represents the time in milliseconds when the flux transition occurred, starting at 0 at the beginning of the track reading. As the floppy disk rotates at about 300 rotations per minute = 5 rotations per second, reading a full track takes approximately 200ms. The Y axis represents the time since the previous flux transition occurred, in microseconds. You can see that most flux transitions occur around 4µs, 6µs or 8µs after the previous one, just as required by the MFM encoding. This is true for all sectors except sector 7 which contains a lot of flux transitions with abnormal timings between 4µs and 6µs. Here is a graphic representing only sector 7 and only the area between 4µs and 6µs:  
**Figure 4**  
[![Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0.Sector.7_Screenshot.png](http://dmweb.free.fr/files/thumbnails/Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0.Sector.7_ScreenshotThumbnail.png "Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0.Sector.7_Screenshot.png")](http://dmweb.free.fr/files/Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0.Sector.7_Screenshot.png "Game_Chaos.Strikes.Back_UK_Version.2.1.Track.0.Sector.7_Screenshot.png")

When the PLL is synchronized, if a flux reversal is not correctly placed and occurs at the very border of the inspection window (1µs sooner or later than the 'perfect' expected timing), then the PLL gets confused and outputs a random value:

*   If the flux reversal is detected right before the end of the inspection window, then the output bit will be '1'. The next bit will be '0' because there cannot be two consecutive '1' bits.
*   If the flux reversal is not detected before the end of the inspection window, then the output bit will be '0'. The flux reversal will be detected at the very beginning of the next inspection window, so that the next output bit will be '1'.

Note that the misplaced flux reversal is never missed: the FDC just cannot reliably determine which bit cell it is part of, hence the random result.

In order to create this fuzzy bit effect, one way is to put flux reversals right on the edge of the PLL's inspection window. For example instead of the standard timings of 4µs or 6µs between two flux reversals, an uncertain flux reversal could be written exactly 5µs after the previous flux reversal. The PLL compensates for variations in the disk rotation speed (it may be different from one drive to another or from one rotation to the next), however smaller instantaneous variations can occur during one rotation of the disk. These small variations are responsible for the appearance of the fuzzy bits: the uncertain flux reversals will not always be detected in the same bit cell.  
In order to maximize the probability of having fuzzy bits detected, the copy protection relies on the very special timing pattern as seen on figure 4. The pattern used in Dungeon Master and Chaos Strikes Back has timings between transition pairs that are slowly increasing from 4µs to 5.5µs and decreasing from 6µs to 4.5µs in small 0.1µs increments so that there will always be some ambiguous transitions right on the edge of inspection windows. Note that the total time for two consecutive transitions is always around 10µs, just as it would have been if normal timings were used (with pairs of 4µs and 6µs transitions).

Here is the sector data as it was most probably defined when being written by the disk duplicator (this is only a guess, but it is validated by the fact that the CRC value for this sector data matches the one found on the original disk in the sector header field):

```
Offset(h) 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 00000000 07 50 41 43 45 2F 46 42 09 53 65 72 69 CA 08 00 .PACE/FB.SeriÊ.. 00000010 00 EF E9 01 68 68 68 68 68 68 68 68 68 68 68 68 .ïé.hhhhhhhhhhhh 00000020 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000030 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000040 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000050 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000060 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000070 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000080 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000090 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000A0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000B0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000C0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000D0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000E0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000F0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000100 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000110 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000120 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000130 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000140 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000150 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000160 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000170 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000180 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 00000190 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000001A0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000001B0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000001C0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000001D0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000001E0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000001F0 68 68 68 68 68 68 68 68 68 68 68 68 68 AC 46 42 hhhhhhhhhhhhh¬FB
```

Note that the duplicator needed additional information about the exact timings to use to record this sector, instead of using the standard timings. The use of carefully chosen custom timings while writing this sector is the real cause of the fuzzy bits. Look at the sector data as it is read from the floppy disk (this is only one example: each read operation would return a slightly different result because of the fuzzy bits producing random values):

```
Offset(h) 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 00000000 07 50 41 43 45 2f 46 42 09 53 65 72 69 ca 08 00 .PACE/FB.Seri... 00000010 00 ef e9 01 68 68 68 68 68 68 68 68 68 68 e8 e8 ....hhhhhhhhhh.. 00000020 e8 e8 e8 e8 e8 e8 e8 e8 e8 68 68 68 68 68 68 68 .........hhhhhhh 00000030 68 68 68 68 68 68 68 68 68 68 68 68 e8 e8 e8 e8 hhhhhhhhhhhh.... 00000040 e8 e8 e8 e8 e8 e8 e8 68 68 68 68 68 68 68 68 68 .......hhhhhhhhh 00000050 68 68 68 68 68 68 68 68 68 68 e8 e8 68 e8 e8 e8 hhhhhhhhhh..h... 00000060 e8 e8 e8 e8 e8 e8 68 68 68 68 68 68 68 68 68 68 ......hhhhhhhhhh 00000070 68 68 68 68 68 68 68 68 e8 e8 68 e8 e8 e8 e8 e8 hhhhhhhh..h..... 00000080 e8 68 e8 e8 e8 68 68 68 68 68 68 68 68 68 68 68 .h...hhhhhhhhhhh 00000090 68 68 68 68 68 68 e8 e8 68 e8 e8 e8 e8 e8 e8 e8 hhhhhh..h....... 000000A0 e8 68 68 e8 68 68 68 68 68 68 68 68 68 68 68 68 .hh.hhhhhhhhhhhh 000000B0 68 68 68 68 68 68 e8 e8 e8 e8 e8 e8 e8 e8 e8 68 hhhhhh.........h 000000C0 68 e8 68 68 68 68 68 68 68 68 68 68 68 68 68 68 h.hhhhhhhhhhhhhh 000000D0 68 e8 68 68 e8 e8 e8 e8 e8 e8 e8 e8 e8 e8 68 68 h.hh..........hh 000000E0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 hhhhhhhhhhhhhhhh 000000F0 e8 e8 e8 e8 e8 e8 e8 e8 e8 e8 68 68 e8 68 68 68 ..........hh.hhh 00000100 68 68 68 68 68 68 68 68 68 68 68 68 68 e8 e8 e8 hhhhhhhhhhhhh... 00000110 68 e8 e8 e8 e8 e8 e8 e8 68 68 e8 68 68 68 68 68 h.......hh.hhhhh 00000120 68 68 68 68 68 68 68 68 68 68 68 68 e8 e8 e8 68 hhhhhhhhhhhh...h 00000130 e8 e8 e8 e8 e8 e8 e8 e8 68 68 68 68 68 68 68 68 ........hhhhhhhh 00000140 68 68 68 68 68 68 68 68 68 68 68 e8 e8 68 e8 e8 hhhhhhhhhhh..h.. 00000150 e8 e8 e8 e8 e8 e8 68 68 68 68 68 68 68 68 68 68 ......hhhhhhhhhh 00000160 68 68 68 68 68 68 68 e8 68 68 e8 e8 e8 e8 e8 e8 hhhhhhh.hh...... 00000170 e8 e8 68 68 e8 68 68 68 68 68 68 68 68 68 68 68 ..hh.hhhhhhhhhhh 00000180 68 68 68 68 68 e8 68 68 e8 e8 e8 e8 e8 e8 e8 e8 hhhhh.hh........ 00000190 68 68 e8 68 68 68 68 68 68 68 68 68 68 68 68 68 hh.hhhhhhhhhhhhh 000001A0 68 68 68 68 68 68 e8 e8 e8 e8 e8 e8 e8 e8 68 68 hhhhhh........hh 000001B0 e8 e8 68 68 68 68 68 68 68 68 68 68 68 68 68 68 ..hhhhhhhhhhhhhh 000001C0 68 e8 e8 68 68 e8 e8 e8 e8 e8 e8 e8 68 68 e8 68 h..hh.......hh.h 000001D0 68 68 68 68 68 68 68 68 68 68 68 68 68 68 68 e8 hhhhhhhhhhhhhhh. 000001E0 e8 68 e8 e8 e8 e8 e8 e8 e8 e8 e8 e8 e8 68 68 68 .h...........hhh 000001F0 68 68 68 68 68 68 68 68 68 68 68 68 68 ac 46 42 hhhhhhhhhhhhh.FB
```

As you can see, many 68h bytes have been transformed to E8h bytes. Here is what happens at binary level:  
Two consecutive 68h bytes, along with their MFM representation:

```
 0 1 1 0 1 0 0 0 0 1 1 0 1 0 0 0 MFM 001010001001010**_1 0_**010100010010101
```

When the fuzzy bit effect takes place, the clock bit between the two bytes of data and the first data bit of the second byte are swapped:

```
 0 1 1 0 1 0 0 0 1 1 1 0 1 0 0 0 MFM 001010001001010**_0 1_**010100010010101
```

The hexadecimal value of the second byte then becomes E8h.

This sector with fuzzy bits is also found on the Chaos Strikes Back for Atari ST Utility Disk.  
The game disks of all Amiga versions of Dungeon Master and Chaos Strikes Back (except Dungeon Master version 3.6) also contain this sector in a dedicated track using an Atari ST format. Other sectors in this track are not used. All other tracks use the regular Amiga format. The Amiga versions of the Chaos Strikes Back Utility Disk do not contain this sector.

#### Track 0, Sector 247: Protection with a non standard sector number

This sector is identical in all versions of Dungeon Master and Chaos Strikes Back for Atari ST.  
In the sector header field of the eighth sector of track 0, the sector number specified is 247 ($F7) instead of the expected value 8.  
Having a sector number which is not in line with other sectors is not a problem by itself. This sector can be read as any other sector as long as you give the FDC the correct sector number to read, which is 247. This may cause trouble to many programs because they will try to read sectors numbered from 1 to 10 and they will fail in reading sector number 8 because there is no such sector on the track. It is also quite easy to write a sector with pretty much any number while formating the track (writing the whole track at once). However, $F7 (and a few other values) is a sector number that cannot be written by the standard floppy disk controller in the Atari ST computer. This value is interpreted as a special command by the FDC when it formats the track and thus this value cannot be written to the disk in a sector header field. It means that a disk copy made on a standard Atari ST cannot have this value correctly copied. Only special equipment can be used to write this value in the sector header. This provides a copy protection mechanism as it cannot be reproduced on a standard Atari ST computer.

There is nothing special with the contents of this sector data field. The protection relies only on the special sector number in the header field.  
Here is an hexadecimal dump of the data in this sector:

```
Offset(h) 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 00000000 43 6F 70 79 72 69 67 68 74 20 28 63 29 20 31 39 Copyright (c) 19 00000010 38 37 2C 20 53 6F 66 74 77 61 72 65 20 48 65 61 87, Software Hea 00000020 76 65 6E 2C 20 49 6E 63 2E 00 FF FF FF FF FF FF ven, Inc..ÿÿÿÿÿÿ 00000030 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000040 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000050 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000060 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000070 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000080 44 75 6E 67 65 6F 6E 4D 61 73 74 65 72 00 FF FF DungeonMaster.ÿÿ 00000090 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000000A0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000000B0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000000C0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000000D0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000000E0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000000F0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000100 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000110 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000120 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000130 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000140 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000150 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000160 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000170 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000180 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 00000190 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000001A0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000001B0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000001C0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000001D0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000001E0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF FF ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ 000001F0 FF FF FF FF FF FF FF FF FF FF FF FF FF FF 9C 9C ÿÿÿÿÿÿÿÿÿÿÿÿÿÿœœ
```

### Description of the boot process

1.  The Atari ST BIOS loads the boot sector from the floppy disk to memory.
2.  After checking that the boot sector is executable (by computing a checksum), the boot sector code is executed.
3.  The boot sector code loads the SWOOSH.IMG file in memory and starts execution of this program.
4.  SWOOSH.IMG displays the FTL logo (using a palette animation technique to simulate the logo animation) and plays the associated sound effect by using the Programmable Sound Generator (PSG). It then makes a BIOS call to run START.PRG with the 'AUTO' command line parameter. The program will not start without this parameter, this is another simple protection.
5.  START.PRG is a small program that reads the compressed main program from the START.PAK file and uncompresses it to memory. The main program, which follows the standard Atari ST .PRG format, is then executed from memory.

### References

 [![Atari-Copy-Protection-V1.4.pdf](http://dmweb.free.fr/sites/all/modules/dmwebmodule/IconPDF.png) Atari-Copy-Protection-V1.4.pdf](http://dmweb.free.fr/files/Atari-Copy-Protection-V1.4.pdf "Atari-Copy-Protection-V1.4.pdf")

This document by DrCoolZic describes all the copy protection schemes that were used on Atari ST. Its content about Dungeon Master was the basis for this web page. It also describes the custom tools written by the author to analyze the copy protections.

 [![TechDoc-DM-AtariST-FloppyDiskAnalysis.zip](http://dmweb.free.fr/sites/all/modules/dmwebmodule/IconArchive.png) TechDoc-DM-AtariST-FloppyDiskAnalysis.zip](http://dmweb.free.fr/files/TechDoc-DM-AtariST-FloppyDiskAnalysis.zip "TechDoc-DM-AtariST-FloppyDiskAnalysis.zip")

This archive contains the complete results of DrCoolZic's tools when run against a floppy disk of Dungeon Master for Atari ST version 1.2 English. These files were kindly produced for me by DrCoolZic. Please read the PDF document above to better understand their contents.

### Credits

Jean Louis-Guérin (DrCoolZic) for his detailed analysis of the original floppy disk as shown in his great document about the many copy protection schemes that were used by Atari ST games, and for the help he gave me in writing this article.

### History of this document

Version 1.2, July 18, 2015

Added graphics and description of flux transition timings for track 0, sector 7.

Version 1.1, February 14, 2009

Minor edits.

The Fuzzy Bits section was updated with a better explanation. Thanks to Jean Louis-Guérin for his help.

Version 1.0, January 25, 2009

First release.

  
  
from Hacker News https://ift.tt/2nChNmk