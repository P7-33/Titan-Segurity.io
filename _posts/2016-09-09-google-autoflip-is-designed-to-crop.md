---
title: 'Google''s AutoFlip Is Designed to Crop Videos Intelligently'
date: 2020-02-16T01:42:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/02/Google-AutoFlip-feat..jpg)

Traditionally, people used TVs that have a 16:9 or a 4:3 aspect ratio to watch videos. However, with recent devices, people view and create videos in an array of aspect ratios. Cropping videos to fit the screens of these devices is a tedious task for video curators. Thankfully, Google is on the case to crop videos smoothly.  

Recently in a blog post, Google announced an [open-source](https://github.com/google/mediapipe/blob/master/mediapipe/docs/autoflip.md) tool for reframing and cropping videos to fit any screen. AutoFlip is the tool that [uses machine learning](https://beebom.com/best-artificial-intelligence-courses-online/) (ML) based object detection and tracking technology to reframe videos automatically.  

AutoFlip – For Intelligent Video Cropping
-----------------------------------------

  

Google created this tool **to get rid of the conventional static cropping method** for cropping videos. The static cropping method involves unreliable techniques of video reframing, i.e., specifying a camera viewport for the video and then cropping everything outside that area. This method produces an undesirable output of the videos.  

![](https://1.bp.blogspot.com/-fJNL_npGtts/XkSQdG2AFLI/AAAAAAAAFSc/kMXOsFd0IhU8ydr3hdpJZ0lK7q4VUY66gCLcBGAsYHQ/s1600/image4.gif)

The Google Autoflip is capable of many advanced features that include **shot detection, video content analysis and lastly, reframing**. Let me break each one of these reframing strategies briefly.  

### Shot (Scene) Detection

  

A scene or a shot in a video is a continuous sequence of frames without any cuts. If there is any change in the shot or scene of a video, **Google’s AutoFlip can detect the change** by comparing the colour histogram of the previous frames with the new ones. A shot change is detected when the distribution of frame colour changes at a different rate than a sliding historical window. The tool, to optimise the reframing process, buffers the whole video before making any reframing decisions.  

![](https://1.bp.blogspot.com/-Vk2-KSerY6w/XkSZLVu10XI/AAAAAAAAFTE/2WF08ZMxnUwfbl4eA2m4oxnn2XQsDJIEwCLcBGAsYHQ/s1600/det_combined.gif)

### Video Content Analysis

  

By using this strategy, **the tool detects important objects and people in the video**. It uses deep learning-based object detection models to identify objects. With this model, the tool can even detect any text overlays or brand logos and other elements like motion or ball for sports videos. The face and object detection models are integrated into the tool through MediaPipe. It is basically a framework for processing multimodal data by developing pipelines. This framework uses [Google’s TensorFlow](https://beebom.com/google-brains-tensorflow/) Lite ML framework on CPUs.  

### Reframing

  

After identifying people and objects in videos, the tool makes logical decisions on how to reframe the video. AutoFlip chooses one of the three reframing strategies to crop the content – **stationary, panning or tracking**. The tool chooses the optimal strategy based on the content of the video. For instance, in stationary mode, the reframed camera viewport remains fixed in a stationary position where most of the important scenes of the video are present. For videos that contain motion, it uses Panning by moving the reframed camera viewport at a constant velocity. When there are interesting subjects in the frame, the Tracking mode comes into effect.

  
  

  

![](https://1.bp.blogspot.com/-5hYa0Are4vM/XkSZU3o8QZI/AAAAAAAAFTI/Xp6pSf57CTs5QZq7ZSCl7peXRTVrMG9WACLcBGAsYHQ/s1600/jitter_combined.gif)

Based on the reframing strategy chosen by the algorithm, an optimised cropping window for each frame is set by AutoFlip. This preserves the important content of the video in the best possible way.  

Google released this tool directly to the developers and film-makers aiming to “_reduce the barriers to their design creativity and reach through the automation of video editing_“. From landscape to portrait or portrait to landscape, whatever the case, AutoFlipis designed to deliver the best possible result.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/googles-autoflip-crop-videos-intelligently/)  
\[the\_ad id='1307'\]