---
title: 'What Is Color Management?'
date: 2020-01-20T07:53:00+01:00
draft: false
---

**What is Color Management?**

The term 'color managed' is used a lot at Netflix and within the industry, but can mean different things to different people depending on their goals and methodology. These methodologies can range from a full ACES pipeline, preserving all color information until the final deliverable, to a more legacy Rec. 709 pipeline, where color information is limited either upon capture or mastering. The purpose of this article is to define what “color managed” means for Netflix productions.

For Netflix, there are three main goals of color management.

*   To ensure **a predictable and repeatable way to view images, and convert between different color spaces** based on a variety of capture devices and display types. This ensures that creative intent is maintained throughout production and post processes.
*   To ensure **all color grading and computer-generated imagery (e.g. VFX, GFX) are done in a scene-referred color space** in order to maximize creative flexibility in post.
*   To ensure that** picture archival masters are of high quality and future proof**, by preserving all color information from capture to archival.

A tech blog post ("[Protecting a Story’s Future with History and Science](https://medium.com/netflix-techblog/protecting-a-storys-future-with-history-and-science-e21a9fb54988)") was written by members of the Netflix Creative Technologies team in order to give some historical and scientific context around what Netflix means by color management, some tips on how to achieve it, and how it protects the Netflix archive for the future.

**Color Pipeline**

A color pipeline represents the essential color space definitions, transforms, and deliverables for a project. This usually requires knowledge of the source(s), working, and final delivery color spaces to ensure that all points in a color pipeline are aligned. This must be defined in coordination with all departments responsible for viewing, sending, and receiving images on a production.

If there is misalignment on the color pipeline, images will look different in different places, costing the production time and resources that could otherwise be spent on the creative process.

**Input Color Space(s)**

This is based on the initial image capture device or source color space. Some examples are Sony SLog3 / SGamut3.cine, RED Log3G10 / WideGamutRGB, ARRI LogC / WideGamut. For certain workflows, this could include archival footage or graphics already in a display-referred color space such as Rec. 709 / BT.1886 or sRGB.

**Working Color Space**

This is the color space where manipulations of the image take place. If the source is not already in the working color space, the source should be converted into the working color space prior to any image manipulation done. Examples of working color spaces are Sony SLog3 / SGamut3.cine, RED Log3G10 / WideGamutRGB, ARRI LogC / WideGamut, or ACES.

Think of this working color space as the ‘digital negative’ - just like a film negative, it is not designed or intended to be viewed directly. These color spaces are designed to store the full dynamic range and color information from the scene, rather than storing the image in the display's color space. This is advantageous since it preserves all of the information from the original capture. Without the use of an appropriate output transform (see below), they will not look normal.

**Output Transform**

This is an agreed-upon color transform which converts the image from the Working Color Space to the Display Color Space. Using an Output Transform - such as a creative display LUT designed by a colorist or DI facility, or even a default camera LUT like ARRI's 709 LUT — can not only serve as the base “look” of the show, but it protects and preserves the working color space and the full dynamic range it has to offer for color and VFX, and the eventual NAM and GAM archival assets.

**Display Color Space**

This is the final color space intended for display, such as on a monitor or projector. The calibration of these displays should be to standard reference targets, standardized by SMPTE and ITU for critical review of images in reference environments. The images will look "correct" in this color space. Examples of these standard display color spaces are Rec. 709 / BT.1886, PQ (ST.2084) P3-D65 or Rec. 2020, etc.

![what-is-color-management-1a.png](https://partnerhelp.netflixstudios.com/hc/article_attachments/360039305454/what-is-color-management-1a.png)

_In this example, the working color space is Log (logarithmic) and the display color space is Rec. 709 / BT.1886. The Output Transform separates the two, and is only baked in for the Rec. 709 / BT.1886 streaming master. The archival masters (NAM and GAM) remain in Log color space._

**What Is The Value of Color Management?**

**Alignment Between Production and Post-Production**

Fixing or re-doing work due to color issues can be very expensive and time consuming. This is why it's so important for all parties in the production and post-production stages who are responsible for viewing, sending, receiving, and/or manipulating images to align on the color pipeline. The way an image is viewed and captured on-set, to the way dailies are processed, can greatly affect the quality, flexibility, and efficiency of work that happens in post-production.

**High Quality Archivable Elements**

Color management, and specifically defining a working color space that contains all of the information captured (or CG generated) helps to protect all of the creative work in a future proof picture archival master. Please read the [Protecting a Story’s Future with History and Science](https://medium.com/netflix-techblog/protecting-a-storys-future-with-history-and-science-e21a9fb54988) tech blog post for some historical and scientific context on our NAM, GAM, and VDM deliverables, and why color management is crucial in order to achieve them.

**General Requirements for Proper Color Management**

**Consistent Color Transforms**

Consistent color management transforms provide the ability to view the same creative intent in a wide variety of viewing scenarios, all without compromising the underlying information in the images. Some color management systems, like ACES, are designed to accommodate any potential viewing scenario.

While ACES defines standard color transforms, software like OpenColorIO makes implementation of these transforms more portable across software. It also allows a project to define custom color pipelines, and share them between facilities and software packages.

**Look Management**

The Look Transform is the creative grade or “show look” separated from the output transform. Separation of the look from the output transform is instrumental to easily preserve creative intent over multiple viewing standards. The look transform should be applied in the working color space after the CDL (if applicable) and before the final output transform. Sometimes concatenation into a single 3D LUT will be necessary (on set, for example) but keeping the elements separate wherever possible will increase efficiency in any color managed workflow.

**High Bit-Depth Precision for Formats and Processing**

A high-quality color management system needs high bit-depth processing in order to transform images between color spaces non-destructively. We recognize that certain nonlinear color spaces (such as Rec. 709 and Log flavors) exist so that high-quality work can be done at lower bit-depths; however, the need for linear representations and complex operations that require 16-bit floating point or higher precision in order to be done non-destructively is increasing. We consider 10-bit a “bare minimum” for any professional imaging system handling SDR images and 12-bit for HDR images. Ideally, all systems should be capable of floating point (16-bit half or 32-bit full float) in order to reduce the chances of clipping or other destructive operations.

**Stages of Color Management**

**Pre-production**

This is a crucial point of communication which increases the likelihood of a smooth color experience through a production. Once a primary camera is chosen, or even before, conversations should be had with all parties responsible for the image. This includes the DoP, DIT, colorist, dailies and VFX facilities, and Netflix representatives responsible for the project.

While certain decisions may not be able to be made at this stage (for example, the final colorist may be TBD), it is important to have these conversations as early as possible. What camera and recording format will be used? What is the working color space? What is the agreed-upon show LUT or Output Transform?

**Display Calibration**

Calibration of all displays to industry color standards is essential. This ensures that the color transforms used are relevant, image appearance is consistent, and color decisions are meaningful. Important standards and target color spaces can be found in "[Color Grading: Calibration Guidelines](https://partnerhelp.netflixstudios.com/hc/en-us/articles/360000591787-Color-Grading-Calibration-Guidelines)".

**On-set Monitoring**

On-set is usually the first place where color and images are judged, so it is arguably the most important to get right. Hopefully, the pre-production conversations have informed an agreed-upon and widely communicated setup of on-set video signal path, LUT boxes (if required), and calibrated monitors. The goal of on-set monitoring is to have a non-destructive and repeatable color pipeline, in order to give flexibility and consistency to the downstream dailies process.

**Dailies & Editorial**

Dailies is where the color pipeline has the biggest effect on post, since the same camera RAW files which will be used in finishing are used to generate color-baked dailies and editorial media. The on-set color decisions should be communicated via ASC CDLs and be passed along into ALEs which are ingested into the NLE. Those CDLs and same show LUT / Output Transform from on-set should be applied in the same working color space so that editorial sees the same color that was seen on-set.

**VFX**

VFX vendors should receive documentation outlining the color pipeline for every project they are working on. Ideally, a VFX pull should include: a description of the VFX plate color encoding and format (i.e. 16-bit EXR, Linear ARRI Wide Gamut), a color ‘recipe' to achieve dailies color (i.e. CDL + LUT, working color space), and a reference frame for checking color against existing dailies. The VFX plate color encoding is essential in order for VFX to be done in a scene-referred color space for high-quality compositing and using physics-based rendering methods. The color ‘recipe' and reference frames are essential in order to send completed VFX shots back into the editorial cut with matching color to the surrounding shots.

**Final Color Grading**

The color pipeline culminates at the point of the online conform of original camera files (OCF) and final color grading. Ideally, the colorist should have access to the color decisions (CDL + LUT) that were used for dailies in order to have a starting point similar in appearance to what has been seen throughout the process.

Color grading should be done in the working color space, ahead of the Output Transform / show LUT, in order to protect those decisions for the archival deliverables explained below. This can be achieved by setting up the grading system with color management settings, to ensure that all creative decisions are applied in the working color space. ACES is a framework that helps in assuring such a setup, but most color grading systems offer various other methods to ensure this. In all cases, the order of operations is key.

**Archival**

When final color grading is done in a color managed environment, the future of that creative intent is protected in the archival deliverables. The "[Protecting a Story’s Future with History and Science](https://medium.com/netflix-techblog/protecting-a-storys-future-with-history-and-science-e21a9fb54988)" tech blog offers an explanation behind picture archival masters: NAM, GAM, and VDM (example below). The GAM (Graded Archival Master) is the most valuable of these assets, representing all of the creative intent, but rendered in the working color space of a project, rather than limited by the display technology of today.

![what-is-color-management-2a.png](https://partnerhelp.netflixstudios.com/hc/article_attachments/360040147553/what-is-color-management-2a.png)

Was this article helpful? 13 out of 13 found this helpful

  
  
from Hacker News https://ift.tt/37cZoyk