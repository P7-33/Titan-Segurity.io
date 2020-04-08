---
title: 'Robot Allows Remote Colleagues To Enjoy Office Shenanigans'
date: 2019-10-18T06:04:00+01:00
draft: false
---

\[Esther Rietmann\] and colleagues built a [Telepresence Robot](https://tryolabs.com/blog/hackathon-robot-remote-work-iot-computer-vision/) to allow work at home teammates to have a virtual, but physical presence in the office. A telepresence robot is like a tablet mounted on a Roomba, providing motion capability in addition to an audio/video connection. Built during a 48 hour hackathon, it is a bit crude under the hood and misses out on some features, such as a bidirectional video feed. But overall, it pretty much does what is expected from such a device.

The main structure is build from cheap aluminium profiles and sheets. A Raspberry Pi is at the heart of the electronics hardware, with a servo mounted Pi-camera and speaker-microphone pair taking care of video and audio. The two DC motors are driven by H-bridges controlled from the Pi and an idle swivel caster is attached as the third wheel. The whole thing is powered by a power bank. The one important thing missing is an HDMI display which can show a video feed from the remote laptop camera. That may have been due to time constraints, but this feature should not be too difficult to add as a future upgrade. It’s important for both sides to be able to see each other.

The software is built around WebRTC protocol, with the [WebRTC Extension](https://www.linux-projects.org/uv4l/webrtc-extension/) from [UV4L](https://www.linux-projects.org/uv4l/) doing most of the heavy lifting. The UV4L Streaming Server not only provides its own built-in set of web applications and services, but also embeds a general-purpose web server on another port, allowing the user to run and deploy their own custom web apps. This allowed \[Esther Rietmann\]’s team to build a basic but functional front-end to transmit data from the remote interface for controlling the robot. The remote computer runs a Python control script, running as a system service, to control the drive motors and camera servo.

The team also played with adding basic object, gesture and action recognition features. This was done using [PoseNet](https://github.com/tensorflow/tfjs-models/tree/master/posenet) – a machine learning model, which allows for real-time human pose estimation in the browser using TensorFlowJS – allowing them to demonstrate some pose detection capability. This could be useful as a “follow me” feature for the robot.

Another missing feature, which most other commercial telepresence robots have, is a sensor suite for collusion avoidance, object detection and awareness such as micro switches, IR / ultrasonic detectors, time of flight cameras or LiDAR’s. It would be relatively easy to add one or several sensors to the robot.

If you’d like to build one for yourself, check out their [code repository](https://github.com/tryolabs/vierjavibot) on Github and the videos below.

  
  
from Hackaday https://ift.tt/2VR9AHV  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)