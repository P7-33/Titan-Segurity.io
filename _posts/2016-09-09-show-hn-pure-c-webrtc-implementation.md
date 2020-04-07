---
title: 'Show HN: Pure C WebRTC implementation for embedded devices'
date: 2020-01-04T02:06:00+01:00
draft: false
---

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#--amazon-kinesis-video-streams-c-webrtc-sdk--)Amazon Kinesis Video Streams C WebRTC SDK  

==================================================================================================================================================================

#### [](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#pure-c-webrtc-client-for-amazon-kinesis-video-streams-)Pure C WebRTC Client for Amazon Kinesis Video Streams

[![Build Status](https://camo.githubusercontent.com/a548e7841d11be0851a4a6d89d31f18ecf95c3e5/68747470733a2f2f7472617669732d63692e6f72672f6177736c6162732f616d617a6f6e2d6b696e657369732d766964656f2d73747265616d732d7765627274632d73646b2d632e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c) [![Coverage Status](https://camo.githubusercontent.com/5ef20b60ff407df9eca1bd9459d040185f07cb19/68747470733a2f2f636f6465636f762e696f2f67682f6177736c6162732f616d617a6f6e2d6b696e657369732d766964656f2d73747265616d732d7765627274632d73646b2d632f6272616e63682f6d61737465722f67726170682f62616467652e737667)](https://codecov.io/gh/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c)

[Key Features](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#key-features) • [Build](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#build) • [Run](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#run) • [documentation](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#documentation) • [Related](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#related) • [License](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#license)

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#key-features)Key Features
-------------------------------------------------------------------------------------------------

*   Audio/Video Support
*   Developer Controlled Media Pipeline
*   DataChannels
*   NACKs
*   STUN/TURN Support
*   IPv4/[IPv6 TODO](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c/issues/115)
*   Signaling Client Included
    *   KVS Provides STUN/TURN and Signaling Backend
    *   Connect with [Android](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-android)/[iOS](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-ios)/[Web](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-js) using pre-made samples
*   Portable
    *   Tested on Linux/MacOS
    *   Tested on x64, ARMv5
*   Small Install Size
    *   Sub 200k library size
    *   OpenSSL, libsrtp, libjsmn, libusrsctp and libwebsockets dependencies.

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#build)Build
-----------------------------------------------------------------------------------

### [](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#download)Download

To download run the following command:

`git clone --recursive https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c.git`

You will also need to install `pkg-config` and `CMake` and a build enviroment

### [](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#configure)Configure

Create a build directory in the newly checked out repository, and execute CMake from it.

`mkdir -p amazon-kinesis-video-streams-webrtc-sdk-c/build; cd amazon-kinesis-video-streams-webrtc-sdk-c/build; cmake ..`

We have provided an example of using GStreamer to capture/encode video, and then send via this library. This is only build if `pkg-config` finds GStreamer is installed on your system.

By default we download all the libraries from GitHub and build them locally, so should require nothing to be installed ahead of time. If you do wish to link to existing libraries you can use the following flags to customize your build.

You can pass the following options to `cmake ..`.

*   `-DADD_MUCLIBC` -- Add -muclibc c flag
*   `-DBUILD_DEPENDENCIES` -- Whether or not to build depending libraries from source
*   `-DBUILD_OPENSSL` -- If building dependencies, whether or not building openssl from source
*   `-DBUILD_TEST=TRUE` -- Build unit/integration tests, may be useful for confirm support for your device. `./tst/webrtc_client_test`
*   `-DCODE_COVERAGE` -- Enable coverage reporting
*   `-DCOMPILER_WARNINGS` -- Enable all compiler warnings
*   `-DADDRESS_SANITIZER` -- Build with AddressSanitizer
*   `-DMEMORY_SANITIZER` -- Build with MemorySanitizer
*   `-DTHREAD_SANITIZER` -- Build with ThreadSanitizer
*   `-DUNDEFINED_BEHAVIOR_SANITIZER` Build with UndefinedBehaviorSanitizer\`

### [](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#build-1)Build

To build the library and the provided samples run make in the build directory you executed CMake.

`make`

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#run)Run
-------------------------------------------------------------------------------

### [](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#setup-your-environment-with-your-aws-account-credentials)Setup your environment with your AWS account credentials:

First set the appropriate environment variables so you can connect to KVS

```
export AWS_ACCESS_KEY_ID= export AWS_SECRET_ACCESS_KEY= 
```

### [](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#running-the-samples)Running the Samples

After executing `make` you will have the following sample applications in your `build` directory:

*   `kvsWebrtcClientMaster` - This application sends sample H264/Opus frames (path: `/samples/h264SampleFrames` and `/samples/opusSampleFrames`) via the signaling channel. It also accepts incoming audio, if enabled in the browser. When checked in the browser, it prints the metadata of the received audio packets in your terminal.
*   `kvsWebrtcClientViewer` - This application accepts sample H264/Opus frames and prints them out.
*   `kvsWebrtcClientMasterGstSample` - This application sends sample H264/Opus frames from a GStreamer pipeline.

Run any of the sample applications by passing to it the name that you want to give to your signaling channel. The application creates the signaling channel using the name you provide. For example, to create a signaling channel called myChannel and to start sending sample H264/Opus frames via this channel, run the following command:

```
./kvsWebrtcClientMaster myChannel 
```

When the command line application prints Connection established, you can proceed to the next step.

Now that your signaling channel is created and the connected master is streaming media to it, you can view this stream. To do so, open the [WebRTC SDK Test Page](https://awslabs.github.io/amazon-kinesis-video-streams-webrtc-sdk-js/examples/index.html) using the steps in Using the Kinesis Video Streams with WebRTC Test Page and set the following values using the same AWS credentials and the same signaling channel that you specified for the master above:

*   Access key ID
*   Secret access key
*   Signaling channel name
*   Client ID (optional)

Choose Start viewer to start live video streaming of the sample H264/Opus frames.

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#documentation)Documentation
---------------------------------------------------------------------------------------------------

All Public APIs are documented in our [Include.h](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c/blob/master/src/include/com/amazonaws/kinesis/video/webrtcclient/Include.h) refer to [related](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#related) for more about WebRTC and KVS.

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#related)Related
---------------------------------------------------------------------------------------

[](https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c#license)License
---------------------------------------------------------------------------------------

This library is licensed under the Apache 2.0 License.

  
  
from Hacker News https://github.com/awslabs/amazon-kinesis-video-streams-webrtc-sdk-c