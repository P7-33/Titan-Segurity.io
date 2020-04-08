---
title: 'Microsoft AI Generates Talking Heads from Noisy Audio Samples'
date: 2019-10-13T08:52:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/10/microsoft-research-sample-results.jpg)

Researchers at Microsoft have developed a technique that aims to improve the accuracy and quality of talking head generations by focusing on the audio stream. As per current talking head generation techniques, a clean and noise-free audio input with a neutral tone is mandatory but the researchers claim that their method “disentangles audio sequences” into factors like phonetic content, emotional tone, and background noise in order to work with any given audio sample.  

_“As we all know, speech is riddled with variations. Different people utter the same word in different contexts with varying duration, amplitude, tone and so on. In addition to_ _linguistic (phonetic) content, speech carries abundant information revealing about the speaker’s emotional state, identity (gender, age, ethnicity) and personality to name a few.”,_ [wrote](https://arxiv.org/pdf/1910.00726.pdf) the researchers in a paper titled “Animating Face using Disentangled Audio Representations”.  

The proposed methodology of researchers takes place in two stages. Firstly, the disentangled representations are identified from the audio source by a **variational autoencoder**(VAE). After the disentanglement is done, talking heads are generated from the categorized audio input based on the face image input by a GAN-based video generator.  

Microsoft researchers used three different data sets to train and test the VAE namely **GRID**, **CREMA-D**, and **LRS3**. GRID is an audiovisual sentence corpus that contains 1,000 recordings from 34 people – 18 male, 16 female. CREMA-D is an audio dataset consisting of 7,442 clips from 91 ethnically-diverse actors – 48 male, 43 female. LRS3 is a dataset with over 100,000 spoken sentences from TED videos.  

Based on the test results analysis, the researchers say that their method is capable to perform consistently over the entire emotional spectrum. _“We validate our model by testing on noisy and emotional audio samples, and show that our approach significantly outperforms the current state-of-the-art in the presence of such audio variations.”_  

The researchers have also mentioned that their project can be expanded to identify other speech factors like the identity of a person and the gender in the future. So, what are your thoughts on this audio-driven head generation technique? Let us know in the comments.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/microsoft-ai-talking-heads-noisy-audio-samples/)  
\[the\_ad id='1307'\]