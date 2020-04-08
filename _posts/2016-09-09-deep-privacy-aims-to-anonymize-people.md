---
title: 'Deep Privacy Aims to Anonymize People While Retaining Expressions'
date: 2019-09-28T05:48:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/09/deep-privacy-samples.jpg)

One of the most important concerns in deepfakes is undoubtedly privacy, which is exactly what these researchers at the Norwegian University of Science and Technology has tried to fix.  

This new technique named Deep Privacy makes use of generative adversarial networks(GAN), the underlying technology employed in Deep fakes to anonymize the subjects while replicating their characteristics.  

The algorithms used in Deep Privacy extract critical facial expressions from the subject and runs it through the database trained with **1.5 million face images** to generate a new face retaining all the details from the source image.  

For accurately detecting facial features, the researchers use Mask R-CNN and Dual Shot Face Detector (DSFD). [Mask R-CNN](https://arxiv.org/abs/1703.06870) is responsible for generating sparse pose information of the face while [DSFD](https://arxiv.org/abs/1810.10220) is used for detecting the faces present in the image.  

_“We present experimental results reflecting the capability of our model to anonymize images while preserving the data distribution, making the data suitable for further training of deep learning models. As far as we know, no other solution has been proposed that guarantees the anonymization of faces while generating realistic images.”,_ wrote the [researchers](https://arxiv.org/abs/1909.04538).  

Since the project is highly experimental at this point in time, you should not be expecting state-of-the-art results here. From the implementation, however, it appears like it could improve significantly over time.  

The source code of the research paper is available on GitHub. If you’re interested to run the code yourself, you may do so from [here](https://github.com/hukkelas/DeepPrivacy). The instructions to set up the environment are given in the README.md file in the repository as well. You can also run the project in Google Colab from [here](https://drive.google.com/open?id=1mR5DcND9JCxqr1rXsavVYKzFQq4gOI5-).  

So, what do you think of Deep Privacy? Let us know your thoughts in the comments.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/deep-privacy-anonymous-facial-recognition/)  
\[the\_ad id='1307'\]