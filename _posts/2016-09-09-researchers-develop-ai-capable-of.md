---
title: 'Researchers Develop AI Capable of Deblurring Photos'
date: 2020-01-26T14:09:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/01/Researchers-Develop-AI-Capable-of-Deblurring-Photos.jpg)

Have you ever posed for group selfies and portraits just to find that your face got blurred out because you couldn’t stop laughing for a lame joke a friend of yours just cracked? I have and it is quite disheartening to see the results. To solve this problem, researchers from the Inception Institute of Artificial Intelligence, the Beijing Institute of Technology, and Stony Brook University have come up with an AI that could help deblur human faces in images.  

The researchers have published their findings in a [paper](https://arxiv.org/abs/2001.06816) titled “Human-Aware Motion Deblurring”. They claim their methodology works better than existing motion deblurring methods.  

The foreground and background of an image undergo different types of image degradation due to various factors including relative motion between the camera and objects, distance, and the image plane.  

In the paper, the researchers propose a **human-aware deblurring model** based on a “triple-branch encoder-decoder architecture” that is capable of fixing the motion blur between foreground subjects (human faces) and the background.  

In the triple-branch encoder-decoder architecture, the **first two branches are responsible for sharpening humans in the foreground and the background details** while the third branch fuses the deblurring information from the other two branches.  

As part of the research, the scientists created a dataset they call [HIDE](https://beebom.com/surface-duo-a-quick-look-at-the-software/) (Humanaware Image DEblurring). The HIDE dataset consists of 8,422 pairs of images extracted from a high-speed camera. Each pair contains a blurry image and its corresponding sharp image.  

Their model was trained on an Nvidia Titan X GPU using the HIDE dataset and a dataset consisting of blurred and sharp images from 240fps 720p GoPro Hero camera videos, making a total of 10,742 images. The researchers mention that the GoPro dataset was used only to train the background decoder as it had very few pedestrians.  

You can learn more about the system in the research paper [here](https://arxiv.org/pdf/2001.06816.pdf) and you may download the HIDE dataset [here](https://github.com/joanshen0508/HA_deblur). So, what are your thoughts on this proposed methodology? Tell us in the comments.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/researchers-develop-ai-deblurring-photos/)  
\[the\_ad id='1307'\]