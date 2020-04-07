---
title: 'Google Releases 3D Model of a Fruit Fly''s Brain'
date: 2020-01-26T11:56:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2020/01/Google-Releases-3D-Model-of-a-Fruit-Flys-Brain.jpg)

Researchers from Google and the Howard Hughes Medical Institute’s Janelia Research Campus have created a sophisticated 3D neural representation of a fruit fly’s brain. The 3D map is called connectome and it contains around 25,000 neurons along with about 20 million synapses.  

The researchers claim that their work is the **largest synaptic-level connectome created so far**. The process involved imaging, reconstructing, and proofreading the 3D model for accuracy.  

The fly’s brain tissue was divided into separate 20-micron thick slabs. The slabs were imaged at 8x8x8nm3 voxel-resolution using focused ion beam scanning electron microscopes.  

Google’s team reconstructed the entire hemibrain using a technique called [flood-filling networks](https://ai.googleblog.com/2018/07/improving-connectomics-by-order-of.html) (FFNs). _“FFNs were the first automated segmentation technology to yield reconstructions that were sufficiently accurate to enable the overall hemibrain project to proceed.”_  

Using FFNs, Google was able to reduce the time necessary to proofread when compared to human proofreaders. Google’s blog notes that human proofreading would have taken tens of millions of hours while FFN achieves it in hundreds of thousands of human hours.  

It took the team two years to proofread their findings even with the help of FFN, which signifies the complexity. _“We applied numerous machine learning algorithms and over 50 person-years of proofreading effort over 2 calendar years to extract a variety of more compact and useful representations, such as neuron skeletons, synapse locations, and connectivity graphs.”,_ [wrote](https://www.biorxiv.org/content/10.1101/2020.01.21.911859v1) the researchers in the paper.  

The project strives to be a public resource for scientists. The research team has also released a few tools that you can use for visualization and analysis. You can learn more regarding the project in the [research paper](https://www.biorxiv.org/content/10.1101/2020.01.21.911859v1) and browse the data [here](https://hemibrain-dot-neuroglancer-demo.appspot.com/#!%7B%22dimensions%22:%7B%22x%22:%5B8e-9%2C%22m%22%5D%2C%22y%22:%5B8e-9%2C%22m%22%5D%2C%22z%22:%5B8e-9%2C%22m%22%5D%7D%2C%22position%22:%5B17114%2C20543%2C18610%5D%2C%22crossSectionScale%22:54.23751620061224%2C%22crossSectionDepth%22:-37.62185354999912%2C%22projectionScale%22:64770.91726975332%2C%22layers%22:%5B%7B%22type%22:%22image%22%2C%22source%22:%22precomputed://gs://neuroglancer-janelia-flyem-hemibrain/emdata/clahe_yz/jpeg%22%2C%22name%22:%22emdata%22%7D%2C%7B%22type%22:%22segmentation%22%2C%22source%22:%22precomputed://gs://neuroglancer-janelia-flyem-hemibrain/v1.0/segmentation%22%2C%22tab%22:%22segments%22%2C%22name%22:%22segmentation%22%7D%2C%7B%22type%22:%22segmentation%22%2C%22source%22:%7B%22url%22:%22precomputed://gs://neuroglancer-janelia-flyem-hemibrain/v1.0/rois%22%2C%22subsources%22:%7B%22default%22:true%2C%22mesh%22:true%7D%2C%22enableDefaultSubsources%22:false%7D%2C%22tab%22:%22segments%22%2C%22pick%22:false%2C%22selectedAlpha%22:0%2C%22saturation%22:0%2C%22objectAlpha%22:0.8%2C%22ignoreNullVisibleSet%22:false%2C%22colorSeed%22:2685294016%2C%22meshSilhouetteRendering%22:3%2C%22name%22:%22roi%22%7D%2C%7B%22type%22:%22annotation%22%2C%22source%22:%22precomputed://gs://neuroglancer-janelia-flyem-hemibrain/v1.0/synapses%22%2C%22tab%22:%22rendering%22%2C%22shader%22:%22#uicontrol%20vec3%20preColor%20color%28default=%5C%22red%5C%22%29%5Cn#uicontrol%20vec3%20postColor%20color%28default=%5C%22blue%5C%22%29%5Cn#uicontrol%20float%20preConfidence%20slider%28min=0%2C%20max=1%2C%20default=0%29%5Cn#uicontrol%20float%20postConfidence%20slider%28min=0%2C%20max=1%2C%20default=0%29%5Cn%5Cnvoid%20main%28%29%20%7B%5Cn%20%20setColor%28defaultColor%28%29%29%3B%5Cn%20%20setEndpointMarkerColor%28%5Cn%20%20%20%20vec4%28preColor%2C%200.5%29%2C%5Cn%20%20%20%20vec4%28postColor%2C%200.5%29%29%3B%5Cn%20%20setEndpointMarkerSize%282.0%2C%202.0%29%3B%5Cn%20%20setLineWidth%282.0%29%3B%5Cn%20%20if%20%28prop_pre_synaptic_confidence%28%29%3C%20preConfidence%20%7C%7C%5Cn%20%20%20%20%20%20prop_post_synaptic_confidence%28%29%3C%20postConfidence%29%20discard%3B%5Cn%7D%5Cn%22%2C%22ignoreNullSegmentFilter%22:false%2C%22linkedSegmentationLayer%22:%7B%22pre_synaptic_cell%22:%22segmentation%22%2C%22post_synaptic_cell%22:%22segmentation%22%7D%2C%22filterBySegmentation%22:%5B%22post_synaptic_cell%22%2C%22pre_synaptic_cell%22%5D%2C%22name%22:%22synapse%22%7D%2C%7B%22type%22:%22segmentation%22%2C%22source%22:%22precomputed://gs://neuroglancer-janelia-flyem-hemibrain/mito_20190717.27250582%22%2C%22tab%22:%22segments%22%2C%22pick%22:false%2C%22selectedAlpha%22:0.82%2C%22name%22:%22mito%22%2C%22visible%22:false%7D%2C%7B%22type%22:%22segmentation%22%2C%22source%22:%22precomputed://gs://neuroglancer-janelia-flyem-hemibrain/mask_normalized_round6%22%2C%22tab%22:%22segments%22%2C%22pick%22:false%2C%22selectedAlpha%22:0.53%2C%22segments%22:%5B%222%22%5D%2C%22name%22:%22mask%22%2C%22visible%22:false%7D%5D%2C%22showSlices%22:false%2C%22selectedLayer%22:%7B%22layer%22:%22segmentation%22%2C%22visible%22:true%2C%22size%22:290%7D%2C%22layout%22:%22xy-3d%22%2C%22selection%22:null%7D).  

  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/google-releases-3d-model-brain/)  
\[the\_ad id='1307'\]