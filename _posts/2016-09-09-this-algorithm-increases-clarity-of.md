---
title: 'This Algorithm Increases Clarity of Underwater Images'
date: 2019-11-17T10:33:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/11/sea-thru.jpg)

Capturing coral reefs on cameras without artificial lights can often turn out to be disappointing due to the overall blueish hue. While casual photographers could get around this with a few minutes of photo editing, researchers are getting limited from using computer vision and machine learning techniques to study these coral reefs. To get around this problem, an engineer and oceanographer Derya Akkaynak has built an algorithm called Sea-thru.  

As the name hints, the algorithm aims to **remove the disturbances and deviations** caused by the water from capturing the actual colors of coral reefs. Akkaynak and Tali Treibitz presented [a paper](http://openaccess.thecvf.com/content_CVPR_2019/html/Akkaynak_Sea-Thru_A_Method_for_Removing_Water_From_Underwater_Images_CVPR_2019_paper.html) on this topic at the IEEE Conference on Computer Vision and Pattern Recognition this June.  

_“The Sea-thru method first calculates backscatter using the darkest pixels in the image and their known range information. Then, it uses an estimate of the spatially varying illuminant to obtain the range-dependent attenuation coefficient.”_, states Akkaynak in the research paper.  

However, this algorithm **needs distance information** to work. The distance estimation is currently done by capturing several images of the same scene from different angles which the algorithm uses to estimate the distance. A [report](https://www.scientificamerican.com/article/sea-thru-brings-clarity-to-underwater-photos1/) from Scientific American notes that scientists already include distance information in image datasets by using a technique called photogrammetry.  

_“What I like about this approach is that it’s really about obtaining true colors. Getting true color could really help us get a lot more worth out of our current data sets.”,_ says Pim Bongaerts, a coral biologist at the California Academy of Sciences.  

So, what are your thoughts on Sea-thru? Do you think it is a step in the right direction for exploring and analyzing the coral reefs? Let us know in the comments.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/algorithm-enhances-clarity-underwater-photos/)  
\[the\_ad id='1307'\]