---
title: 'Adobe''s AI Fits Clothes on Any Body Type'
date: 2020-01-26T07:31:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/01/Adobes-AI-Fits-Clothes-on-Any-Body-Model.jpg)

Researchers at Adobe’s Media and Data Science Research Lab, IIT & IIIT Hyderabad, and Stanford University have developed a system that aims to help shoppers virtually try on a piece of clothing on any given model image.  

Dubbed SieveNet, the framework is capable of recreating the new apparel into the model’s body shape and pose while preserving the characteristics of the cloth, including minute design elements like folds.  

There are two major stages in this approach – **warping the product image**, **transferring the warped texture into the model’s body**. To achieve this, the researchers make use of a “multi-stage coarse-to-fine warping network” trained to identify unique aspects of the cloth using a conditional segmentation mask before it is transferred to the model’s body.  

Take a look at the below inference pipeline for a better visual understanding of the concept.  

![inference pipeline sievenet](https://beebom.com/wp-content/uploads/2020/01/inference-pipeline-sievenet.jpg)

Credits: SeiveNet / Adobe

Unlike existing virtual try-on methodologies, the researchers claim that their **technique does not suffer from visual malfunctions** caused due to texture bleeding and incorrect warping.  

The researchers trained SieveNet on a rich dataset consisting of about 19,000 images of front-facing female models and product images. They ran their model on a PC with 16GB of RAM and four Nvidia 1080Ti graphics cards. The images were rearranged for conducting qualitative and quantitative tests.  

From the qualitative and quantitative tests, the researchers found their systems producing better results than existing methodologies in various aspects including handling occlusion, geometric warping, variation in poses, avoiding bleeding, preserving unaffected region while maintaining the image quality.  

The researchers suggest integrating SeiveNet into online shopping websites. _“It\[SeiveNet\] is especially important for online fashion commerce because it compensates for the_ _lack of a direct physical experience of in-store shopping”,_ [wrote](https://arxiv.org/pdf/2001.06265.pdf) the researchers.  

Check out the entire research paper [here](https://arxiv.org/pdf/2001.06265.pdf) and let us know your thoughts on SeiveNet in the comments.  

_Featured Image Credits: SeiveNet / Adobe_  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/adobes-ai-fits-clothes-any-body-type/)  
\[the\_ad id='1307'\]