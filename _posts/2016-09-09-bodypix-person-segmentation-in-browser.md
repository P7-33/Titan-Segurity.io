---
title: 'BodyPix: Person Segmentation in the Browser'
date: 2019-10-11T02:48:00+01:00
draft: false
---

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#bodypix---person-segmentation-in-the-browser)BodyPix - Person Segmentation in the Browser
===========================================================================================================================================================

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#note-weve-just-released-version-20-with-multi-person-support-a-new-resnet-model-and-api-check-out-the-new-documentation-below)Note: We've just released Version 2.0 with **multi-person** support, a **new ResNet** model and API. Check out the new documentation below.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This package contains a standalone model called BodyPix, as well as some demos, for running real-time person and body part segmentation in the browser using TensorFlow.js.

[Try the demo here!](https://storage.googleapis.com/tfjs-models/demos/body-pix/index.html)

[![BodyPix](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/body-pix-2.0.gif)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/body-pix-2.0.gif)

This model can be used to segment an image into pixels that are and are not part of a person, and into pixels that belong to each of twenty-four body parts. It works for a single person, and its ideal use case is for when there is only one person centered in an input image or video. It can be combined with a person detector to segment multiple people in an image by first cropping boxes for each detected person then estimating segmentation in each of those crops, but that responsibility is currently outside of the scope of this model.

To keep track of issues we use the [tensorflow/tfjs](https://github.com/tensorflow/tfjs) Github repo.

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#contributors)Contributors
-------------------------------------------------------------------------------------------

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#main-contributors)Main Contributors

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#acknowledgement)Acknowledgement

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#special-thanks-for-participants-in-the-demo-video)Special thanks for participants in the demo video

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#tables-of-contents)Tables of Contents
-------------------------------------------------------------------------------------------------------

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#installation)Installation
-------------------------------------------------------------------------------------------

You can use this as standalone es5 bundle like this:

```
 <script src\="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.0.0"\>script> <script src\="https://cdn.jsdelivr.net/npm/@tensorflow-models/body-pix@2.0.0"\>script>
```

Or you can install it via npm for use in a TypeScript / ES6 project.

```
npm install @tensorflow-models/body-pix
```

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#usage)Usage
-----------------------------------------------------------------------------

Either a person or part of the body can be segmented in an image. Each methodology has similar input parameters with different outputs.

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#loading-a-pre-trained-bodypix-model)Loading a pre-trained BodyPix Model

In the first step of person segmentation and body part segmentation, an image is fed through a pre-trained model. BodyPix **comes with a few different versions of the model,** corresponding to variances of MobileNetV1 architecture and ResNet50 architecture. To get started, a model must be loaded from a checkpoint:

```
const net \= await bodyPix.load();
```

By default, `bodyPix.load()` loads a faster and smaller model that is based on MobileNetV1 architecture and has a lower accuracy. If you want to load the larger and more accurate model, specify the architecture explicitly in `bodyPix.load()` using a `ModelConfig` dictionary:

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#mobilenet-smaller-faster-less-accurate)MobileNet (smaller, faster, less accurate)

```
const net \= await bodyPix.load({ architecture: 'MobileNetV1', outputStride: 16, inputResolution: 513, multiplier: 0.75 });
```

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#resnet-larger-slower-more-accurate-new)ResNet (larger, slower, more accurate) \*\*new!\*\*

```
const net \= await bodyPix.load({ architecture: 'ResNet50', outputStride: 32, inputResolution: 257, quantBytes: 2 });
```

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#config-params-in-bodypixload)Config params in bodyPix.load()

*   **architecture** - Can be either `MobileNetV1` or `ResNet50`. It determines which BodyPix architecture to load.
    
*   **outputStride** - Can be one of `8`, `16`, `32` (Stride `16`, `32` are supported for the ResNet architecture and stride `8`, `16`, `32` are supported for the MobileNetV1 architecture). It specifies the output stride of the BodyPix model. The smaller the value, the larger the output resolution, and more accurate the model at the cost of speed. Set this to a larger value to increase speed at the cost of accuracy.
    
*   **inputResolution** - Can be one of `161`, `193`, `257`, `289`, `321`, `353`, `385`, `417`, `449`, `481`, `513`, and `801`. Defaults to `257.` It specifies the size the image is resized to before it is fed into the BodyPix model. The larger the value, the more accurate the model at the cost of speed. Set this to a smaller value to increase speed at the cost of accuracy.
    
*   **multiplier** - Can be one of `1.0`, `0.75`, or `0.50` (The value is used _only_ by the MobileNetV1 architecture and not by the ResNet architecture). It is the float multiplier for the depth (number of channels) for all convolution ops. The larger the value, the larger the size of the layers, and more accurate the model at the cost of speed. Set this to a smaller value to increase speed at the cost of accuracy.
    
*   **quantBytes** - This argument controls the bytes used for weight quantization. The available options are:
    
    *   `4`. 4 bytes per float (no quantization). Leads to highest accuracy and original model size.
    *   `2`. 2 bytes per float. Leads to slightly lower accuracy and 2x model size reduction.
    *   `1`. 1 byte per float. Leads to lower accuracy and 4x model size reduction.
    
    The following table contains the corresponding BodyPix 2.0 model checkpoint sizes (widthout gzip) when using different quantization bytes:
    
    Architecture
    
    quantBytes=4
    
    quantBytes=2
    
    quantBytes=1
    
    ResNet50
    
    ~90MB
    
    ~45MB
    
    ~22MB
    
    MobileNetV1 (1.00)
    
    ~13MB
    
    ~6MB
    
    ~3MB
    
    MobileNetV1 (0.75)
    
    ~5MB
    
    ~2MB
    
    ~1MB
    
    MobileNetV1 (0.50)
    
    ~2MB
    
    ~1MB
    
    ~0.6MB
    
*   **modelUrl** - An optional string that specifies custom url of the model. This is useful for local development or countries that don't have access to the models hosted on GCP.
    

**By default,** BodyPix loads a MobileNetV1 architecture with a **`0.75`** multiplier. This is recommended for computers with **mid-range/lower-end GPUs.** A model with a **`0.50`** multiplier is recommended for **mobile.** The ResNet architecture is recommended for computers with **even more powerful GPUs**.

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#person-segmentation)Person segmentation

Given an image with multiple people, multi-person segmentation model predicts segmentation for _each_ person. It returns _an array_ of `PersonSegmentation` and each corresponding to one person. Each element is a binary array for one person with 1 for the pixels that are part of the person, and 0 otherwise. The array size corresponds to the number of pixels in the image.

[![Multi-person Segmentation](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/two_people_segmentation.jpg)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/two_people_segmentation.jpg)

```
const net \= await bodyPix.load(); const segmentation \= await net.estimateMultiPersonInstanceSegmentation(image, { flipHorizontal: false, segmentationThreshold: 0.7, maxDetections: 10, scoreThreshold: 0.2, nmsRadius: 20, minKeypointScore: 0.3, refineSteps: 10 });
```

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#params-in-estimatemultipersoninstancesegmentation)Params in estimateMultiPersonInstanceSegmentation()

*   **image** - ImageData|HTMLImageElement|HTMLCanvasElement|HTMLVideoElement The input image to feed through the network.
*   **config** - an optional dictionary containing:
    *   **flipHorizontal** - Defaults to false. If the segmentation & pose should be flipped/mirrored horizontally. This should be set to true for videos where the video is by default flipped horizontally (i.e. a webcam), and you want the segmentation & pose to be returned in the proper orientation.
    *   **segmentationThreshold** - Defaults to 0.7. Must be between 0 and 1. For each pixel, the model estimates a score between 0 and 1 that indicates how confident it is that part of a person is displayed in that pixel. This _segmentationThreshold_ is used to convert these values to binary 0 or 1s by determining the minimum value a pixel's score must have to be considered part of a person. In essence, a higher value will create a tighter crop around a person but may result in some pixels being that are part of a person being excluded from the returned segmentation mask.
    *   **maxDetections** - Defaults to 10. Maximum number of returned instance detections per image.
    *   **scoreThreshold** - Only return instance detections that have root part score greater or equal to this value. Defaults to 0.5
    *   **nmsRadius** - Defaults to 20. Non-maximum suppression part distance in pixels. It needs to be strictly positive. Two parts suppress each other if they are less than `nmsRadius` pixels away.
    *   **minKeypointScore** - Default to 0.3. Keypoints above the score are used for matching and assigning segmentation mask to each person..
    *   **refineSteps** - Default to 10. The number of refinement steps used when assigning the instance segmentation. It needs to be strictly positive. The larger the higher the accuracy and slower the inference.

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#returns)Returns

It returns a `Promise` that resolves with **an array** of `PersonSegmentation`s. When there are multiple people in the image, each `PersonSegmentation` object in the array represents one person. More details about the `PersonSegmentation` object can be found in the documentation of the `estimateSinglePersonSegmentation` method.

```
\[{ width: 640, height: 480, data: Uint8Array(307200) \[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1 …\] }, ... // the data array for the 1st person containing 307200 values, one for each pixel of the 640x480 image. { width: 640, height: 480, data: Uint8Array(307200) \[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 1, …\] }\] // the data array for the n-th person containing 307200 values, one for each pixel of the 640x480 image.
```

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage)Example Usage

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#via-script-tag)via Script Tag

```
<html\> <head\>  <script src\="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.0.0"\>script>  <script src\="https://cdn.jsdelivr.net/npm/@tensorflow-models/body-pix@2.0.0"\>script> head> <body\> <img id\='person' src\='/images/person.jpg '/> body>  <script\>  var imageElement \= document.getElementById('image');   bodyPix.load().then(function(net){  return net.estimateMultiPersonSegmentation(imageElement, {  flipHorizontal: false,  segmentationThreshold: 0.7,  maxDetections: 10,  scoreThreshold: 0.2,  nmsRadius: 20,  minKeypointScore: 0.3,  refineSteps: 10  });  }).then(function(allSegmentations){  console.log(allSegmentations);  })  script> html>
```

###### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#via-npm)via NPM

```
import \* as bodyPix from '@tensorflow-models/body-pix'; const imageElement \= document.getElementById('image'); // load the BodyPix model from a checkpoint const net \= await bodyPix.load(); const allSegmentations \= await net.estimateMultiPersonInstanceSegmentation(imageElement, { flipHorizontal: false, segmentationThreshold: 0.7, maxDetections: 10, scoreThreshold: 0.2, nmsRadius: 20, minKeypointScore: 0.3, refineSteps: 10 }); console.log(allSegmentations);
```

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#multi-person-body-part-segmentation)Multi-person body part segmentation

Given an image with multiple people. BodyPix's `estimateMultiPersonInstancePartSegmentation` method predicts the 24 body part segmentations for _each_ person. It returns _an array_ of `PartSegmentation`s, each corresponding to one of the people. The `PartSegmentation` object contains a width, height, `Pose` and an Int32 array with a part id from 0-24 for the pixels that are part of a corresponding body part, and -1 otherwise.

[![Multi-person Segmentation](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/two_people_parts.jpg)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/two_people_parts.jpg)

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#the-body-parts)The Body Parts

As stated above, the result contains an array with ids for one of 24 body parts, or -1 if there is no body part:

Part Id

Part Name

Part Id

Part Name

0

left\_face

12

torso\_front

1

right\_face

13

torso\_back

2

left\_upper\_arm\_front

14

left\_upper\_leg\_front

3

left\_upper\_arm\_back

15

left\_upper\_leg\_back

4

right\_upper\_arm\_front

16

right\_upper\_leg\_front

5

right\_upper\_arm\_back

17

right\_upper\_leg\_back

6

left\_lower\_arm\_front

18

left\_lower\_leg\_front

7

left\_lower\_arm\_back

19

left\_lower\_leg\_back

8

right\_lower\_arm\_front

20

right\_lower\_leg\_front

9

right\_lower\_arm\_back

21

right\_lower\_leg\_back

10

left\_hand

22

left\_feet

11

right\_hand

23

right\_feet

(Note: Part Id value -1 represents the non-person background)

```
const net \= await bodyPix.load(); const segmentation \= await net.estimateMultiPersonInstancePartSegmentation(image, { flipHorizontal: false, segmentationThreshold: 0.7, maxDetections: 10, scoreThreshold: 0.2, nmsRadius: 20, minKeypointScore: 0.3, refineSteps: 10 });
```

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#params-in-estimatemultipersoninstancesegmentation-1)Params in estimateMultiPersonInstanceSegmentation

*   **image** - ImageData|HTMLImageElement|HTMLCanvasElement|HTMLVideoElement The input image to feed through the network.
*   **inferenceConfig** - an object containing:
    *   **flipHorizontal** - Defaults to false. If the segmentation & pose should be flipped/mirrored horizontally. This should be set to true for videos where the video is by default flipped horizontally (i.e. a webcam), and you want the segmentation & pose to be returned in the proper orientation.
    *   **segmentationThreshold** - Must be between 0 and 1. For each pixel, the model estimates a score between 0 and 1 that indicates how confident it is that part of a person is displayed in that pixel. This _segmentationThreshold_ is used to convert these values to binary 0 or 1s by determining the minimum value a pixel's score must have to be considered part of a person. In essence, a higher value will create a tighter crop around a person but may result in some pixels being that are part of a person being excluded from the returned segmentation mask.
    *   **maxDetections** - Maximum number of returned instance detections per image. Defaults to 10
    *   **scoreThreshold** - Only return instance detections that have root part score greater or equal to this value. Defaults to 0.5
    *   **nmsRadius** - Non-maximum suppression part distance in pixels. It needs to be strictly positive. Two parts suppress each other if they are less than `nmsRadius` pixels away. Defaults to 20.
    *   **minKeypointScore** - Default to 0.3. Keypoints above the score are used for matching and assigning segmentation mask to each person..
    *   **refineSteps** - The number of refinement steps used when assigning the instance segmentation. It needs to be strictly positive. The larger the higher the accuracy and slower the inference.

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#returns-1)Returns

It returns a `Promise` that resolves with **an array** of `PartSegmentation`s. When there are multiple people in the image, each `PartSegmentation` object in the array represents one person. More details about the `PartSegmentation` object can be found in the documentation of the `estimateSinglePersonPartSegmentation` method.

```
\[ { width: 680, height: 480, data: Int32Array(307200) \[\-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 3, 3, 3, 3, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 0, 0, 0, 0, 0, 1, 1, 2, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 15, 15, 15, 15, 16, 16, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 23, 23, 23, 22, 22, \-1, \-1, \-1, \-1,  …\] }, { width: 680, height: 480, data: Int32Array(307200) \[\-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 3, 3, 3, 3, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 0, 0, 0, 0, 0, 1, 1, 2, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 15, 15, 15, 15, 16, 16, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, \-1, 23, 23, 23, 22, 22, \-1, \-1, \-1, \-1,  …\] } \] // the array contains 307200 values, one for each pixel of the 640x480 image that was passed to the function.
```

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage-1)Example Usage

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#via-script-tag-1)via Script Tag

```
<html\> <head\>  <script src\="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.0.0"\>script>  <script src\="https://cdn.jsdelivr.net/npm/@tensorflow-models/body-pix@2.0.0"\>script> head> <body\> <img id\='person' src\='/images/person.jpg '/> body>  <script\>  var imageElement \= document.getElementById('image');   bodyPix.load().then(function(net){  return net.estimateMultiPersonPartSegmentation(imageElement, {  flipHorizontal: false,  segmentationThreshold: 0.7,  maxDetections: 10,  scoreThreshold: 0.2,  nmsRadius: 20,  minKeypointScore: 0.3,  refineSteps: 10  });  }).then(function(multiPersonPartSegmentations){  console.log(multiPersonPartSegmentations);  })  script> html>
```

###### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#via-npm-1)via NPM

```
import \* as bodyPix from '@tensorflow-models/body-pix'; const imageElement \= document.getElementById('image'); // load the BodyPix model from a checkpoint const net \= await bodyPix.load(); const multiPersonPartSegmentations \= await net.estimateMultiPersonPartSegmentation(imageElement, { flipHorizontal: false, segmentationThreshold: 0.7, maxDetections: 10, scoreThreshold: 0.2, nmsRadius: 20, minKeypointScore: 0.3, refineSteps: 10 }); console.log(multiPersonPartSegmentations);
```

which would produce the output:

```
\[{ width: 640, height: 480, data: Uint8Array(307200) \[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, …\] }, // the data array contains 307200 values, one for each pixel of the 640x480 image that was passed to the function. { width: 640, height: 480, data: Uint8Array(307200) \[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, …\] }\] // the data array contains 307200 values, one for each pixel of the 640x480 image that was passed to the function.
```

### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#output-visualization-utility-functions)Output Visualization Utility Functions

BodyPix contains utility functions to help with drawing and compositing using the outputs. **These API methods are experimental and subject to change.**

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#tomaskimagedata)`toMaskImageData`

Given the output of person segmentation (or multi-person instance segmentation), generates a visualization of each pixel determined by the corresponding binary segmentation value at the pixel from the output. In other words, pixels where there is a person will be colored by the foreground color and where there is not a person will be colored by the background color. This can be used as a mask to crop a person or the background when compositing.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#inputs)Inputs

*   **personSegmentation** The output from [estimatePersonSegmentation](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#Single-person-segmentation) or [estimateMultiPersonSegmentation](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#Multi-person-segmentation). The former is a PersonSegmentation object and later is an _array_ of PersonSegmentation object.
    
*   **foreground** The foreground color (r,g,b,a) for visualizing pixels that belong to people.
    
*   **background** The background color (r,g,b,a) for visualizing pixels that don't belong to people.
    
*   **drawContour** Whether to draw the contour around each person's segmentation mask.
    

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#returns-2)Returns

An [ImageData](https://developer.mozilla.org/en-US/docs/Web/API/ImageData) with the same width and height of the personSegmentation, with color and opacity at each pixel determined by the corresponding binary segmentation value at the pixel from the output.

[![MaskImageData](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/toMultiPersonMaskImageData.jpg)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/toMultiPersonMaskImageData.jpg)

_With the output from `estimateMultiPersonSegmentation` on the first image above, `toMultiPersonMaskImageData` will produce an [ImageData](https://developer.mozilla.org/en-US/docs/Web/API/ImageData) that either looks like the second image above if setting `foregroundColor` to {r: 0, g: 0, b: 0, a: 0} and `backgroundColor` to {r: 0, g: 0, b: 0, a: 255} (by default), or the third image if if setting `foregroundColor` to {r: 0, g: 0, b: 0, a: 255} and `backgroundColor` to {r: 0, g: 0, b: 0, a: 0}. This can be used to mask either the person or the background using the method `drawMask`._

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#tocoloredpartimagedata)`toColoredPartImageData`

Given the output from person body part segmentation (or multi-person instance body part segmentation) and an array of colors indexed by part id, generates an image with the corresponding color for each part at each pixel, and white pixels where there is no part.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#inputs-1)Inputs

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#returns-3)Returns

An [ImageData](https://developer.mozilla.org/en-US/docs/Web/API/ImageData) with the same width and height of the estimated person part segmentation, with the corresponding color for each part at each pixel, and black pixels where there is no part.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage-2)Example usage

```
const imageElement \= document.getElementById('person'); const net \= await bodyPix.load(); const partSegmentation \= await net.estimateMultiPersonPartSegmentation(imageElement); // The rainbow colormap const rainbow \= \[ \[110, 64, 170\], \[143, 61, 178\], \[178, 60, 178\], \[210, 62, 167\], \[238, 67, 149\], \[255, 78, 125\], \[255, 94, 99\], \[255, 115, 75\], \[255, 140, 56\], \[239, 167, 47\], \[217, 194, 49\], \[194, 219, 64\], \[175, 240, 91\], \[135, 245, 87\], \[96, 247, 96\], \[64, 243, 115\], \[40, 234, 141\], \[28, 219, 169\], \[26, 199, 194\], \[33, 176, 213\], \[47, 150, 224\], \[65, 125, 224\], \[84, 101, 214\], \[99, 81, 195\] \]; // the colored part image is an rgb image with a corresponding color from thee rainbow colors for each part at each pixel, and black pixels where there is no part. const coloredPartImage \= bodyPix.toColoredPartImageData(partSegmentation, rainbow); const opacity \= 0.7; const flipHorizontal \= true; const maskBlurAmount \= 0; const canvas \= document.getElementById('canvas'); // draw the colored part image on top of the original image onto a canvas. The colored part image will be drawn semi-transparent, with an opacity of 0.7, allowing for the original image to be visible under. bodyPix.drawMask( canvas, imageElement, coloredPartImageData, opacity, maskBlurAmount, flipHorizontal);
```

[![toColoredPartImageData](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/toMultiPersonColoredPartImage.jpg)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/toMultiPersonColoredPartImage.jpg)

_With the output from `estimateMultiPersonPartSegmentation` on the first image above, a 'spectral' or 'rainbow' color scale in `toColoredPartImageData` will produce an `ImageData` that looks like the second image or the third image above._

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#drawmask)`drawMask`

Draws an image onto a canvas and draws an `ImageData` containing a mask on top of it with a specified opacity; The `ImageData` is typically generated using `toMaskImageData`, `toMultiPersonMaskImageData`, `toColoredPartImageData` or `toMultiPersonColoredPartImageData`.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#inputs-2)Inputs

*   **canvas** The canvas to be drawn onto.
*   **image** The original image to apply the mask to.
*   **maskImage** An ImageData containing the mask. Ideally this should be generated by `toMaskImageData` or `toColoredPartImageData.`
*   **maskOpacity** The opacity when drawing the mask on top of the image. Defaults to 0.7. Should be a float between 0 and 1.
*   **maskBlurAmount** How many pixels to blur the mask by. Defaults to 0. Should be an integer between 0 and 20.
*   **flipHorizontal** If the result should be flipped horizontally. Defaults to false.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage-3)Example usage

```
const imageElement \= document.getElementById('image'); const net \= await bodyPix.load(); const segmentation \= await net.estimateSinglePersonSegmentation(imageElement); const maskBackground \= true; // Convert the personSegmentation into a mask to darken the background. const foregroundColor \= {r: 0, g: 0, b: 0, a: 0}; const backgroundColor \= {r: 0, g: 0, b: 0, a: 255}; const backgroundDarkeningMask \= bodyPix.toMaskImageData(personSegmentation, foregroundColor, backgroundColor); const opacity \= 0.7; const maskBlurAmount \= 3; const flipHorizontal \= true; const canvas \= document.getElementById('canvas'); // draw the mask onto the image on a canvas. With opacity set to 0.7 and maskBlurAmount set to 3, this will darken the background and blur the darkened background's edge. bodyPix.drawMask( canvas, imageElement, backgroundDarkeningMask, opacity, maskBlurAmount, flipHorizontal);
```

[![drawMask](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/drawMask.jpg)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/drawMask.jpg)

_The above shows drawing a mask generated by `toMaskImageData` on top of an image and canvas using `toMask`. In this case, `segmentationThreshold` was set to a lower value of 0.25, making the mask include more pixels. The top two images show the mask drawn on top of the image, and the second two images show the mask blurred by setting `maskBlurAmount` to 9 before being drawn onto the image, resulting in a smoother transition between the person and the masked background._

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#drawpixelatedmask)`drawPixelatedMask`

Draws an image onto a canvas and draws an `ImageData` containing a mask on top of it with a specified opacity; The `ImageData` is typically generated using `toColoredPartImageData`. Different from `drawMask`, this rendering function applies the pixelation effect to the BodyPix's body part segmentation prediction. This allows a user to display low resolution body part segmentation and thus offers an aesthetic interpretation of the body part segmentation prediction.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#inputs-3)Inputs

*   **canvas** The canvas to be drawn onto.
*   **image** The original image to apply the mask to.
*   **maskImage** An ImageData containing the mask. Ideally this should be generated by `toColoredPartImageData.`
*   **maskOpacity** The opacity when drawing the mask on top of the image. Defaults to 0.7. Should be a float between 0 and 1.
*   **maskBlurAmount** How many pixels to blur the mask by. Defaults to 0. Should be an integer between 0 and 20.
*   **flipHorizontal** If the result should be flipped horizontally. Defaults to false.
*   **pixelCellWidth** The width of each pixel cell. Default to 10 px.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage-4)Example usage

```
const imageElement \= document.getElementById('person'); const net \= await bodyPix.load(); const partSegmentation \= await net.estimateSinglePersonPartSegmentation(imageElement); const rainbow \= \[ \[110, 64, 170\], \[143, 61, 178\], \[178, 60, 178\], \[210, 62, 167\], \[238, 67, 149\], \[255, 78, 125\], \[255, 94, 99\], \[255, 115, 75\], \[255, 140, 56\], \[239, 167, 47\], \[217, 194, 49\], \[194, 219, 64\], \[175, 240, 91\], \[135, 245, 87\], \[96, 247, 96\], \[64, 243, 115\], \[40, 234, 141\], \[28, 219, 169\], \[26, 199, 194\], \[33, 176, 213\], \[47, 150, 224\], \[65, 125, 224\], \[84, 101, 214\], \[99, 81, 195\] \]; // the colored part image is an rgb image with a corresponding color from thee rainbow colors for each part at each pixel, and white pixels where there is no part. const coloredPartImage \= bodyPix.toColoredPartImageData(partSegmentation, rainbow); const opacity \= 0.7; const flipHorizontal \= true; const maskBlurAmount \= 0; const pixelCellWidth \= 10.0; const canvas \= document.getElementById('canvas'); // draw the pixelated colored part image on top of the original image onto a canvas. Each pixel cell's width will be set to 10 px. The pixelated colored part image will be drawn semi-transparent, with an opacity of 0.7, allowing for the original image to be visible under. bodyPix.drawPixelatedMask( canvas, imageElement, coloredPartImageData, opacity, maskBlurAmount, flipHorizontal, pixelCellWidth);
```

[![drawPixelatedMask](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/drawPixelatedMask.png)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/drawPixelatedMask.png)

_The pixelation effect is applied to part image using `drawPixelatedMask`; the result is shown in the image above._

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#drawbokeheffect)`drawBokehEffect`

Given a personSegmentation and an image, draws the image with its background blurred onto a canvas.

An example of applying a [bokeh effect](https://www.nikonusa.com/en/learn-and-explore/a/tips-and-techniques/bokeh-for-beginners.html) can be seen in this [demo](https://storage.googleapis.com/tfjs-models/demos/body-pix/index.html):

[![Bokeh](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/bokeh.gif)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/bokeh.gif)

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#inputs-4)Inputs

*   **canvas** The canvas to draw the background-blurred image onto.
*   **image** The image to blur the background of and draw.
*   **personSegmentation** A personSegmentation object, containing a binary array with 1 for the pixels that are part of the person, and 0 otherwise. Must have the same dimensions as the image.
*   **backgroundBlurAmount** How many pixels in the background blend into each other. Defaults to 3. Should be an integer between 1 and 20.
*   **edgeBlurAmount** How many pixels to blur on the edge between the person and the background by. Defaults to 3. Should be an integer between 0 and 20.
*   **flipHorizontal** If the output should be flipped horizontally. Defaults to false.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage-5)Example Usage

```
const imageElement \= document.getElementById('image'); const net \= await bodyPix.load(); const personSegmentation \= await net.estimateSinglePersonSegmentation(imageElement); const backgroundBlurAmount \= 3; const edgeBlurAmount \= 3; const flipHorizontal \= true; const canvas \= document.getElementById('canvas'); // draw the image with the background blurred onto the canvas. The edge between the person and blurred background is blurred by 3 pixels. bodyPix.drawBokehEffect( canvas, imageElement, personSegmentation, backgroundBlurAmount, edgeBlurAmount, flipHorizontal);
```

[![bokeh](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/bokehimage.png)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/bokehimage.png)

_The above shows the process of applying a 'bokeh' effect to an image (the left-most one) with `drawBokehEffect`. An **inverted** mask is generated from a `personSegmentation`. The original image is then drawn onto the canvas, and using the [canvas compositing](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/globalCompositeOperation) operation `destination-over` the mask is drawn onto the canvas, causing the background to be removed. The original image is blurred and drawn onto the canvas where it doesn't overlap with the existing image using the compositing operation `destination-over`. The result is seen in the right-most image._

#### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#blurbodypart)`blurBodyPart`

Given a PartSegmentation (or an array of PartSegmentation) and an image, blurs some person body parts (e.g. left face and right face).

An example of applying a body part blur on `left_face` and `right_face` body parts (other body parts can be specified):

[![three_people_faceblur](https://github.com/tensorflow/tfjs-models/raw/master/body-pix/images/three_people_faceblur.jpg)](https://github.com/tensorflow/tfjs-models/blob/master/body-pix/images/three_people_faceblur.jpg)

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#inputs-5)Inputs

*   **canvas** The canvas to draw the body-part blurred image onto.
*   **image** The image with people to blur the body-part and draw.
*   **partSegmentation** A PartSegmentation object or an array of PartSegmentation object. Must have the same dimensions as the image.
*   **bodyPartIdsToBlur** Default to \[0, 1\] (left-face and right-face). An array of body part ids to blur. Each must be one of the 24 body part ids.
*   **backgroundBlurAmount** How many pixels in the background blend into each other. Defaults to 3. Should be an integer between 1 and 20.
*   **edgeBlurAmount** How many pixels to blur on the edge between the person and the background by. Defaults to 3. Should be an integer between 0 and 20.
*   **flipHorizontal** If the output should be flipped horizontally. Defaults to false.

##### [](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#example-usage-6)Example Usage

```
const imageElement \= document.getElementById('image'); const net \= await bodyPix.load(); const partSegmentation \= await net.estimateMultiPersonInstancePartSegmentation(imageElement); const backgroundBlurAmount \= 3; const edgeBlurAmount \= 3; const flipHorizontal \= true; const faceBodyPartIdsToBlur \= \[0, 1\]; const canvas \= document.getElementById('canvas'); bodyPix.blurBodyPart( canvas, imageElement, partSegmentation, faceBodyPartIdsToBlur, backgroundBlurAmount, edgeBlurAmount, flipHorizontal);
```

[](https://github.com/tensorflow/tfjs-models/tree/master/body-pix#developing-the-demos)Developing the Demos
-----------------------------------------------------------------------------------------------------------

Details for how to run the demos are included in the `demos/` folder.

  
  
from Hacker News https://github.com/tensorflow/tfjs-models/tree/master/body-pix