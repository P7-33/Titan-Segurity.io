---
title: 'Self- Programmed Self Driving Car with Code'
date: 2019-11-18T03:38:00+01:00
draft: false
---

Sourc code can be found [here.](https://github.com/littlemountainman/selfdrive)

Introduction
------------

At the current state all we can talk about is Level 2 autonomy. Tesla is already doing a pretty good job at developing and actually shipping Level 2 self driving or rather driver assistance systems. A few days ago [@karpathy](https://twitter.com/karpathy) presented their workflow with PyTorch and also said some numbers, to train the Autopilot system with all it neural networks you would have to spend 70,000 hours with a decent gpu - that is around 8 years (depending on which GPU you are using). In total the Autopilot is a system of 48 Neural Networks. When we compare this to what I will show you, you are gonna see that this is insane.(Tesla really does a great job). I developed a model for steering, gas and brake for one camera.

Behavioral cloning
------------------

At the current state of my model the model basically just clones the human driver as good as possible. That means the the amount of brake is higher in curves and the amount of gas is higher when the car just goes straight, of course it can also steer and it does a pretty good job with controlling the steering wheel in different situations so it steers less when the car is pretty fast and steers more when the car is slower - just as a human driver. I did a few tests where pedestrians where suddenly crossing the road and the model gave it’s best job to not hit the human crossing the road.

The actual model
----------------

When I was first starting this project I started with an extremely large neural network [inspired by (page 5)](https://images.nvidia.com/content/tegra/automotive/images/2016/solutions/pdf/end-to-end-dl-using-px.pdf) and it just took ages to train and get the model to a decent level so I trashed that one. So I moved on to this smaller model:

![](https://littlemountainman.github.io/assets/smallmodel.png)

it doesnt seem small but trust me it is. This is the code for it:

```
 model = Sequential() model.add(Lambda(lambda x: x/127.5 - 1.,input\_shape=(image\_x, image\_y, 3))) model.add(BatchNormalization()) model.add(Convolution2D(16, 8, 8, subsample=(4, 4), border\_mode="same")) model.add(ELU()) model.add(Convolution2D(32, 5, 5, subsample=(2, 2), border\_mode="same")) model.add(ELU()) model.add(Convolution2D(64, 5, 5, subsample=(2, 2), border\_mode="same")) model.add(Flatten()) model.add(Dropout(.1)) model.add(ELU()) model.add(Dense(512)) model.add(Dropout(.2)) model.add(ELU()) model.add(Dense(3)) 
```

you see the model got a lot smaller compared to the one in the paper above. The reason is not that I wouldn’t have spent the time training the model but I wanted to run it on a high-end mobile phone. I wanted the model to be as small as possible be run on the less powerful devices of today.

Data
----

The data I used was from my drives and the [commaai dataset](https://github.com/commaai/comma2k19/). I copied together a tool to extract the data from the drive’s log files and to generate files from the one and only camera and the steering angle, gas and brake labels, [more here](https://github.com/littlemountainman/selfdrive/blob/master/preperation/reader.py). This file basically reads the camera file and the log files. The camera file gets turned into a numpy nd-array and saved on the hard drive. The log files are filled with [car parameters](https://github.com/littlemountainman/rlog-unzipper#possible-parameters-to-look-for-in-the-file) I was only interested in the actuators so again I extracted them and saved them into a numpy nd-array and saved them. The camera resolution is 640x480 and 3 color channels (RGB).

Results
-------

So after a long time of trying things out and throwing them away again. So far with the resources I had for training I am pretty happy with the results. Look at them yourself!

![driving](https://github.com/littlemountainman/selfdrive/raw/master/drivingman.gif) That is just lane keeping so far but it does quite a good job at doing it. It is still a bit weak when wanting to predict the angle when there is an intersection and it doesn’t see the next road and say there is an highway exit.

Future goals
------------

I definitely want to improve the project and keep working on it:

*   Implementing SLAM (Simultaneous localization and mapping), sadly a good slam system is very computing intensive and does not fit in well with running it on a mobile phone.
*   Traffic light and sign detection. I already have a basic NN for traffic ligths but it is not yet performing the way I would want it to. Traffic signs are really hard since they are different from country to country.

Thank you for reading this little post and for more updates on the project follow me on [Twitter](https://twitter.com/littlemtman).

  
  
from Hacker News https://ift.tt/2Qscdze