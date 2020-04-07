---
title: 'VidGear: Complete Video Processing library for all Python lovers'
date: 2020-01-01T11:55:00+01:00
draft: false
---

[](https://github.com/abhiTronix/vidgear#--)[![VidGear Logo](https://camo.githubusercontent.com/631e0d44d47ce2f834d26022272def4a030bdfc8/68747470733a2f2f6162686974726f6e69782e6769746875622e696f2f696d672f766964676561722f76696467656172206c6f676f2e737667)](https://camo.githubusercontent.com/631e0d44d47ce2f834d26022272def4a030bdfc8/68747470733a2f2f6162686974726f6e69782e6769746875622e696f2f696d672f766964676561722f76696467656172206c6f676f2e737667)
=============================================================================================================================================================================================================================================================================================================================================================================================================================================================

[](https://github.com/abhiTronix/vidgear#---1)[![VidGear Banner](https://camo.githubusercontent.com/b3f97d3980eb1ac9fbbf0861b67a21f696195eba/68747470733a2f2f6162686974726f6e69782e6769746875622e696f2f696d672f766964676561722f766964676561722062616e6e65722e737667)](https://camo.githubusercontent.com/b3f97d3980eb1ac9fbbf0861b67a21f696195eba/68747470733a2f2f6162686974726f6e69782e6769746875622e696f2f696d672f766964676561722f766964676561722062616e6e65722e737667)
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

VidGear is a powerful python Video Processing library built with multi-threaded [**Gears**](https://github.com/abhiTronix/vidgear#gears) each with a unique set of trailblazing features. These APIs provides a easy-to-use, highly extensible, and multi-threaded wrapper around many underlying state-of-the-art libraries such as _[OpenCV ➶](https://github.com/opencv/opencv), [FFmpeg ➶](https://www.ffmpeg.org/), [picamera ➶](https://github.com/waveform80/picamera), [pafy ➶](https://github.com/mps-youtube/pafy), [pyzmq ➶](https://github.com/zeromq/pyzmq) and [python-mss ➶](https://github.com/BoboTiG/python-mss)_

The following **functional block diagram** clearly depicts the functioning of VidGear library:

[![@Vidgear Functional Block Diagram](https://camo.githubusercontent.com/7eb66b31e45072cd99ee988690242b93388705db/68747470733a2f2f6162686974726f6e69782e6769746875622e696f2f696d672f766964676561722f766964676561725f66756e6374696f6e322d30312e737667)](https://camo.githubusercontent.com/7eb66b31e45072cd99ee988690242b93388705db/68747470733a2f2f6162686974726f6e69782e6769746875622e696f2f696d672f766964676561722f766964676561725f66756e6374696f6e322d30312e737667)

[](https://github.com/abhiTronix/vidgear#table-of-contents)Table of Contents
============================================================================

[**TL;DR**](https://github.com/abhiTronix/vidgear#tldr)

[**Gears: What are these?**](https://github.com/abhiTronix/vidgear#gears)

[**Installation**](https://github.com/abhiTronix/vidgear#installation)

[**New-Release SneekPeak: v0.1.6**](https://github.com/abhiTronix/vidgear#new-release-sneekpeak--vidgear-016)

[**Documentation**](https://github.com/abhiTronix/vidgear#documentation)

**For Developers/Contributors**

**Additional Info**

[](https://github.com/abhiTronix/vidgear#tldr)TL;DR
===================================================

#### [](https://github.com/abhiTronix/vidgear#what-is-vidgear)What is vidgear?

> _**"VidGear is an [ultrafast➶](https://github.com/abhiTronix/vidgear/wiki/FAQ-&-Troubleshooting#2-vidgear-is-ultrafast-but-how), compact, flexible and easy-to-adapt complete Video Processing Python Library."**_

#### [](https://github.com/abhiTronix/vidgear#what-does-it-do)What does it do?

> _**"VidGear can read, write, process, send & receive video frames from various devices in real-time."**_

#### [](https://github.com/abhiTronix/vidgear#what-is-its-purpose)What is its purpose?

> _**"Built with simplicity in mind, VidGear lets programmers and software developers to easily integrate and perform complex Video Processing tasks in their existing or new applications, without going through various underlying library's documentation and using just a few lines of code. Beneficial for both, if you're new to programming with Python language or already a pro at it."**_

**For more advanced information, see the [_Wiki Documentation ➶_](https://github.com/abhiTronix/vidgear/wiki).**

[](https://github.com/abhiTronix/vidgear#gears)Gears
====================================================

> **VidGear is built with various **Multi-Threaded APIs** _(a.k.a Gears)_ each with some unique function/mechanism.**

Each of these API is designed exclusively to handle/control different device-specific video streams, network streams, and media encoders. These APIs provides an easy-to-use, highly extensible, and a multi-threaded wrapper around various underlying libraries to exploit their features and functions directly while providing robust error-handling.

**These Gears can be classified as follows:**

**A. VideoCapture Gears:**

*   [**CamGear:**](https://github.com/abhiTronix/vidgear#camgear) _Targets various IP-USB-Cameras/Network-Streams/YouTube-Video-URL._
*   [**PiGear:**](https://github.com/abhiTronix/vidgear#pigear) _Targets various Raspberry Pi Camera Modules._
*   [**ScreenGear:**](https://github.com/abhiTronix/vidgear#screengear) _Enables ultra-fast Screen Casting._
*   [**VideoGear:**](https://github.com/abhiTronix/vidgear#videogear) _A common API with Video Stabilizer wrapper._

**B. VideoWriter Gear:**

*   [**WriteGear:**](https://github.com/abhiTronix/vidgear#writegear) _Handles easy Lossless Video Encoding and Compression._

**C. Network Gear:**

*   [**NetGear:**](https://github.com/abhiTronix/vidgear#netgear) _Targets synchronous/asynchronous video frames transferring between interconnecting systems over the network._

[](https://github.com/abhiTronix/vidgear#camgear)CamGear
--------------------------------------------------------

> _CamGear can grab ultra-fast frames from diverse range of devices/streams, which includes almost any IP/USB Cameras, multimedia video file format ([_upto 4k tested_](https://github.com/abhiTronix/vidgear/blob/e0843720202b0921d1c26e2ce5b11fadefbec892/vidgear/tests/benchmark_tests/test_benchmark_playback.py#L65)), various network stream protocols such as `http(s), rtp, rstp, rtmp, mms, etc.`, plus support for live Gstreamer's stream pipeline and YouTube video/livestreams URLs._

CamGear provides a flexible, high-level multi-threaded wrapper around `OpenCV's` [VideoCapture class](https://docs.opencv.org/master/d8/dfe/classcv_1_1VideoCapture.html#a57c0e81e83e60f36c83027dc2a188e80) with access almost all of its available parameters and also employs [`pafy`](https://github.com/mps-youtube/pafy) python APIs for live [YouTube streaming](https://github.com/abhiTronix/vidgear/wiki/CamGear#2-camgear-api-with-live-youtube-piplineing-using-video-url). Furthermore, CamGear implements exclusively on [**Threaded Queue mode**](https://github.com/abhiTronix/vidgear/wiki/Threaded-Queue-Mode) for ultra-fast, error-free and synchronized frame handling.

**Following simplified functional block diagram depicts CamGear API's generalized working:**

[![CamGear Functional Block Diagram](https://github.com/abhiTronix/Imbakup/raw/master/Images/CamGear.png)](https://github.com/abhiTronix/Imbakup/raw/master/Images/CamGear.png)

### [](https://github.com/abhiTronix/vidgear#camgear-api-guide)CamGear API Guide:

[**\>>> Usage Guide**](https://github.com/abhiTronix/vidgear/wiki/CamGear#camgear-api)

[](https://github.com/abhiTronix/vidgear#videogear)VideoGear
------------------------------------------------------------

> _VideoGear API provides a special internal wrapper around VidGear's exclusive [**Video Stabilizer**](https://github.com/abhiTronix/vidgear/wiki/Stabilizer-Class) class._

Furthermore, VideoGear API can provide internal access to both [CamGear](https://github.com/abhiTronix/vidgear#camgear) and [PiGear](https://github.com/abhiTronix/vidgear#pigear) APIs separated by a special flag. Thereby, _this API holds the exclusive power for any incoming VideoStream from any source, whether it is live or not, to access and stabilize it directly with minimum latency and memory requirements._

**Below is a snapshot of a VideoGear Stabilizer in action:**

[![VideoGear Stabilizer in action!](https://github.com/abhiTronix/Imbakup/raw/master/Images/stabilizer.gif)](https://github.com/abhiTronix/Imbakup/raw/master/Images/stabilizer.gif)  
_Original Video Courtesy [@SIGGRAPH2013](http://liushuaicheng.org/SIGGRAPH2013/database.html "opensourced video samples database")_

Code to generate above VideoGear API Stabilized Video(_See more detailed usage examples [here](https://github.com/abhiTronix/vidgear/wiki/Real-time-Video-Stabilization#usage)_):

```
# import libraries from vidgear.gears import VideoGear import numpy as np import cv2 stream\_stab \= VideoGear(source\='test.mp4', stabilize \= True).start() # To open any valid video stream with \`stabilize\` flag set to True. stream\_org \= VideoGear(source\='test.mp4').start() # open same stream without stabilization for comparison # infinite loop while True: frame\_stab \= stream\_stab.read() # read stabilized frames # check if frame is None if frame\_stab is None: #if True break the infinite loop break #read original frame frame\_org \= stream\_org.read() #concatenate both frames output\_frame \= np.concatenate((frame\_org, frame\_stab), axis\=1) #put text cv2.putText(output\_frame, "Before", (10, output\_frame.shape\[0\] \- 10),cv2.FONT\_HERSHEY\_SIMPLEX, 0.6, (0,255,0), 2) cv2.putText(output\_frame, "After", (output\_frame.shape\[1\]//2+10, frame.shape\[0\] \- 10),cv2.FONT\_HERSHEY\_SIMPLEX, 0.6, (0,255,0), 2) cv2.imshow("Stabilized Frame", output\_frame) # Show output window key \= cv2.waitKey(1) & 0xFF # check for 'q' key-press if key \== ord("q"): #if 'q' key-pressed break out break cv2.destroyAllWindows() # close output window stream\_org.stop() stream\_stab.stop() # safely close video streams.
```

### [](https://github.com/abhiTronix/vidgear#videogear-api-guide)VideoGear API Guide:

[**\>>> Usage Guide**](https://github.com/abhiTronix/vidgear/wiki/VideoGear#videogear-api)

[](https://github.com/abhiTronix/vidgear#pigear)PiGear
------------------------------------------------------

> _PiGear is similar to CamGear but made to support various Raspberry Pi Camera Modules _(such as [OmniVision OV5647 Camera Module](https://github.com/techyian/MMALSharp/wiki/OmniVision-OV5647-Camera-Module) and [Sony IMX219 Camera Module](https://github.com/techyian/MMALSharp/wiki/Sony-IMX219-Camera-Module))_._

PiGear provides a flexible multi-threaded wrapper around complete [**picamera**](https://github.com/waveform80/picamera) python library to interface with these modules correctly, and also grants the ability to exploit its various features like `brightness, saturation, sensor_mode, etc.` effortlessly.

Best of all, PiGear API provides excellent Error-Handling with features like a threaded internal timer that keeps active track of any frozen threads and handles hardware failures/frozen threads robustly thereby will exit safely if any failure occurs. So now if you accidently pulled your camera module cable out when running PiGear API in your script, instead of going into possible kernel panic/frozen threads, API exit safely to save resources.

**Following simplified functional block diagram depicts PiGear API:**

[![PiGear Functional Block Diagram](https://github.com/abhiTronix/Imbakup/raw/master/Images/PiGear.png)](https://github.com/abhiTronix/Imbakup/raw/master/Images/PiGear.png)

### [](https://github.com/abhiTronix/vidgear#pigear-api-guide)PiGear API Guide:

[**\>>> Usage Guide**](https://github.com/abhiTronix/vidgear/wiki/PiGear#pigear-api)

[](https://github.com/abhiTronix/vidgear#screengear)ScreenGear
--------------------------------------------------------------

> _ScreenGear API act as Screen Recorder, that can grab frames from your monitor in real-time either by define an area on the computer screen or fullscreen at the expense of insignificant latency. It also provide seemless support for capturing frames from multiple monitors._

ScreenGear provides a high-level multi-threaded wrapper around [**python-mss**](https://github.com/BoboTiG/python-mss) python library API and also supports a easy and flexible direct internal parameter manipulation.

**Below is a snapshot of a ScreenGear API in action:**

[![ScreenGear in action!](https://github.com/abhiTronix/Imbakup/raw/master/Images/screengear.gif)](https://github.com/abhiTronix/Imbakup/raw/master/Images/screengear.gif)

Code to generate the above result:

```
# import libraries from vidgear.gears import ScreenGear import cv2 stream \= ScreenGear().start() # infinite loop while True: frame \= stream.read() # read frames # check if frame is None if frame is None: #if True break the infinite loop break cv2.imshow("Output Frame", frame) # Show output window key \= cv2.waitKey(1) & 0xFF # check for 'q' key-press if key \== ord("q"): #if 'q' key-pressed break out break cv2.destroyAllWindows() # close output window stream.stop() # safely close video stream.
```

### [](https://github.com/abhiTronix/vidgear#screengear-api-guide)ScreenGear API Guide:

[**\>>> Usage Guide**](https://github.com/abhiTronix/vidgear/wiki/ScreenGear#screengear-api)

[](https://github.com/abhiTronix/vidgear#writegear)WriteGear
------------------------------------------------------------

> _WriteGear handles various powerful Writer Tools that provide us the freedom to do almost anything imagine with multimedia files._

WriteGear API provide a complete, flexible & robust wrapper around [**FFmpeg**](https://www.ffmpeg.org/), a leading multimedia framework. With WriteGear, we can process real-time video frames into a lossless compressed format with any suitable specification in just few easy [lines of codes](https://github.com/abhiTronix/vidgear/wiki/Compression-Mode:-FFmpeg#1-writegear-bare-minimum-examplecompression-mode). These specifications include setting any video/audio property such as `bitrate, codec, framerate, resolution, subtitles, etc.` easily as well complex tasks such as multiplexing video with audio in real-time(see this [example wiki](https://github.com/abhiTronix/vidgear/wiki/Working-with-Audio#a-live-audio-input-to-writegear-class)). Best of all, WriteGear grants the freedom to play with any FFmpeg parameter with its exclusive custom Command function(see this [example wiki](https://github.com/abhiTronix/vidgear/wiki/Custom-FFmpeg-Commands-in-WriteGear-API#custom-ffmpeg-commands-in-writegear-api)), while handling all errors robustly.

In addition to this, WriteGear also provides flexible access to [**OpenCV's VideoWriter API**](https://docs.opencv.org/master/dd/d9e/classcv_1_1VideoWriter.html#ad59c61d8881ba2b2da22cff5487465b5) which provides some basic tools for video frames encoding but without compression.

**WriteGear primarily operates in the following two modes:**

*   **Compression Mode:** In this mode, WriteGear utilizes [**`FFmpeg's`**](https://www.ffmpeg.org/) inbuilt encoders to encode lossless multimedia files. It provides us the ability to exploit almost any available parameters available within FFmpeg, with so much ease and flexibility and while doing that it robustly handles all errors/warnings quietly. **You can find more about this mode [here](https://github.com/abhiTronix/vidgear/wiki/Compression-Mode:-FFmpeg)**.
    
*   **Non-Compression Mode:** In this mode, WriteGear utilizes basic OpenCV's inbuilt [**VideoWriter API**](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html). Similar to compression mode, WriteGear also supports all parameters manipulation available within OpenCV's VideoWriter API. But this mode lacks the ability to manipulate encoding parameters and other important features like video compression, audio encoding, etc. **You can learn about this mode [here](https://github.com/abhiTronix/vidgear/wiki/Non-Compression-Mode:-OpenCV)**.
    

**Following functional block diagram depicts WriteGear API's generalized working:**

[![WriteGear Functional Block Diagram](https://github.com/abhiTronix/Imbakup/raw/master/Images/WriteGear.png)](https://github.com/abhiTronix/Imbakup/raw/master/Images/WriteGear.png)

### [](https://github.com/abhiTronix/vidgear#writegear-api-guide)WriteGear API Guide:

[**\>>> Usage Guide**](https://github.com/abhiTronix/vidgear/wiki/WriteGear#writegear-api)

[](https://github.com/abhiTronix/vidgear#netgear)NetGear
--------------------------------------------------------

> _NetGear is exclusively designed to transfer video frames synchronously and asynchronously between interconnecting systems over the network in real-time._

NetGear implements a high-level wrapper around [**PyZmQ**](https://github.com/zeromq/pyzmq) python library that contains python bindings for [ZeroMQ](http://zeromq.org/) - a high-performance asynchronous distributed messaging library that aim to be used in distributed or concurrent applications. It provides a message queue, but unlike message-oriented middleware, a ZeroMQ system can run without a dedicated message broker.

NetGear provides seamless support for bidirectional data transmission between receiver(client) and sender(server) through bi-directional synchronous messaging patterns such as zmq.PAIR _(ZMQ Pair Pattern)_ & zmq.REQ/zmq.REP _(ZMQ Request/Reply Pattern)_.

NetGear also supports real-time frame Encoding/Decoding compression capabilities for optimizing performance while sending the frames directly over the network, by encoding the frame before sending it and decoding it on the client's end automatically in real-time.

For security, NetGear implements easy access to ZeroMQ's powerful, smart & secure Security Layers, that enables strong encryption on data, and unbreakable authentication between the Server and the Client with the help of custom certificates/keys and brings easy, standardized privacy and authentication for distributed systems over the network.

Best of all, NetGear can robustly handle Multiple Servers devices at once, thereby providing access to seamless Live Streaming of the multiple device in a network at the same time.

**NetGear as of now seamlessly supports three ZeroMQ messaging patterns:**

**Following functional block diagram depicts generalized functioning of NetGear API:**

[![NetGear Functional Block Diagram](https://github.com/abhiTronix/Imbakup/raw/master/Images/NetGear.png)](https://github.com/abhiTronix/Imbakup/raw/master/Images/NetGear.png)

### [](https://github.com/abhiTronix/vidgear#netgear-api-guide)NetGear API Guide:

[**\>>> Usage Guide**](https://github.com/abhiTronix/vidgear/wiki/NetGear#netgear-api)

[](https://github.com/abhiTronix/vidgear#new-release-sneekpeak--vidgear-016)New Release SneekPeak : VidGear 0.1.6
=================================================================================================================

*   _**⚠️ Python 2.7 legacy support [dropped in v0.1.6](https://github.com/abhiTronix/vidgear/issues/29) !**_
    
*   **NetGear API:**
    
    *   Added powerful ZMQ Authentication & Data Encryption features for NetGear API
    *   Added robust Multi-Server support for NetGear API.
    *   Added exclusive Bi-Directional Mode for bidirectional data transmission.
    *   Added frame-compression support with on-the-fly flexible encoding/decoding.
    *   Implemented new _Publish/Subscribe(`zmq.PUB/zmq.SUB`)_ pattern for seamless Live Streaming in NetGear API.
*   **PiGear API:**
    
    *   Added new threaded internal timing function for PiGear to handle any hardware failures/frozen threads
    *   PiGear will not exit safely with `SystemError` if Picamera ribbon cable is pulled out to save resources.
*   **WriteGear API:** Added new `execute_ffmpeg_cmd` function to pass a custom command to its internal FFmpeg pipeline.
    
*   **Stabilizer class:** Added new _Crop and Zoom_ feature.
    
*   _**Added VidGear's official native support for MacOS environment and [many more...](https://github.com/abhiTronix/vidgear/blob/master/changelog.md)**_
    

[](https://github.com/abhiTronix/vidgear#installation)Installation
==================================================================

[](https://github.com/abhiTronix/vidgear#prerequisites)Prerequisites:
---------------------------------------------------------------------

Before installing VidGear, you must verify that the following dependencies are met:

*   ⚠️ Must be using only [**supported Python legacies**](https://github.com/abhiTronix/vidgear#supported-python-legacies) and also [**pip**](https://pip.pypa.io/en/stable/installing/) already installed and configured.
    
*   **`OpenCV:`** VidGear must require OpenCV(3.0+) python enabled binaries to be installed on your machine for its core functions. For its installation, you can follow these online tutorials for [linux](https://www.pyimagesearch.com/2018/05/28/ubuntu-18-04-how-to-install-opencv/) and [raspberry pi](https://www.pyimagesearch.com/2018/09/26/install-opencv-4-on-your-raspberry-pi/), otherwise, install it via pip:
    
    ```
     pip3 install -U opencv-python #or install opencv-contrib-python similarly
    ```
    
*   **`FFmpeg:`** VidGear must require FFmpeg for its powerful video compression and encoding capabilities. 🌟 Follow this [**FFmpeg wiki page**](https://github.com/abhiTronix/vidgear/wiki/FFmpeg-Installation) for its installation. 🌟
    
*   **`picamera:`** Required if using Raspberry Pi Camera Modules(_such as OmniVision OV5647 Camera Module_) with your Raspberry Pi machine. You can easily install it via pip:
    
    Also, make sure to enable Raspberry Pi hardware-specific settings prior to using this library.
    
*   **`mss:`** Required for using Screen Casting. Install it via pip:
    
*   **`pyzmq:`** Required for transferring live video frames through _ZeroMQ messaging system_ over the network. Install it via pip:
    
*   **`pafy:`** Required for direct YouTube Video streaming capabilities. Both [`pafy`](https://github.com/mps-youtube/pafy) and latest only [`youtube-dl`](https://github.com/ytdl-org/youtube-dl/)(_as pafy's backend_) libraries must be installed via pip as follows:
    
    ```
     pip3 install pafy pip3 install -U youtube-dl
    ```
    

[](https://github.com/abhiTronix/vidgear#available-installation-options)Available Installation Options:
-------------------------------------------------------------------------------------------------------

### [](https://github.com/abhiTronix/vidgear#option-1-pypi-install)Option 1: PyPI Install

> Best option for **quickly** getting VidGear installed.

### [](https://github.com/abhiTronix/vidgear#option-2-release-archive-download)Option 2: Release Archive Download

> Best option if you want a **compressed archive**.

VidGear releases are available for download as packages in the [latest release](https://github.com/abhiTronix/vidgear/releases/latest).

### [](https://github.com/abhiTronix/vidgear#option-3-clone-the-repository)Option 3: Clone the Repository

> Best option for trying **latest patches(_maybe experimental_), Pull Requests**, or **contributing** to development.

You can clone this repository's `testing` branch for development and thereby can install as follows:

```
 git clone https://github.com/abhiTronix/vidgear.git cd vidgear git checkout testing sudo pip3 install .
```

[](https://github.com/abhiTronix/vidgear#documentation)Documentation
====================================================================

The full documentation for all VidGear classes and functions can be found in the link below:

[](https://github.com/abhiTronix/vidgear#testing)Testing
========================================================

[](https://github.com/abhiTronix/vidgear#contributing)Contributing
==================================================================

See [**contributing.md**](https://github.com/abhiTronix/vidgear/blob/master/contributing.md).

[](https://github.com/abhiTronix/vidgear#supported-python-legacies)Supported Python legacies
============================================================================================

*   **Python 3+ are only supported legacies for installing Vidgear v0.1.6 and above.**
*   **⚠️ Python 2.7 legacy support [dropped in v0.1.6](https://github.com/abhiTronix/vidgear/issues/29).**

[](https://github.com/abhiTronix/vidgear#changelog)Changelog
============================================================

See [**changelog.md**](https://github.com/abhiTronix/vidgear/blob/master/changelog.md)

[](https://github.com/abhiTronix/vidgear#citing)Citing
======================================================

**Here is a Bibtex entry you can use to cite this project in a publication:**

```
@misc{vidgear, Title = {vidgear}, Author = {Abhishek Thakur}, howpublished = {\\url{https://github.com/abhiTronix/vidgear}} }
```

[](https://github.com/abhiTronix/vidgear#license)License
========================================================

**Copyright © abhiTronix 2019**

This library is licensed under the **[Apache 2.0 License](https://github.com/abhiTronix/vidgear/blob/master/LICENSE)**.

  
  
from Hacker News https://ift.tt/2ucfgiT