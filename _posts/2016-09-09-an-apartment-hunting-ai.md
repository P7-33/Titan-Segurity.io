---
title: 'An Apartment-Hunting AI'
date: 2019-10-08T03:13:00+01:00
draft: false
---

Finding a good apartment is a lot of work and includes searching websites for available places and then cross-referencing with a list of characteristics. This can take hours, days or even months but in a world where cars drive themselves, it is possible to [use machine learning in your hunt](https://habr.com/en/post/468053/).

\[veesot\] lives in a city between Europe and Asia and was looking for a new home, and his goal was to create a model that can use historical data to not only suggest if an advertised price was right, but also recommend waiting by predicting the decrease in the the future. The data-set includes parameters such as “area”, “district”, “number of balconies” etc and tried to determine an optimal property to view.

There is a lot that \[veesot\] describes in his post which includes cleaning the data in terms of removing flats that are tool small or tool large. This is essentially creating a training data-set for the machine learning system that will allow the system to generate usable output. \[veesot\] also added parameters such districts which relate to the geographical location, age of the building and even the materials used in the construction.

There is also an interesting bit about analyzing the data variables and determining cross-correlation which ultimately leads to the obvious conclusions that the central/older districts have older apartments and newer ones are larger. It makes for a few cool graphs but the code can certainly come in handy when dealing with similar data-sets. The last part of the writing discusses applying Linear Regression and then testing its accuracy. Interpreting the model produces interesting results about the trained model and the values of the coefficients.

The python code is available and the same approach can be applied to a number of problems. We loved the commentary and we hope the author will continue working on the challenge. For those how are looking at similar  problems, there is also the possibility of running regression using [TensorFlow and it can be done in your browser](https://hackaday.com/2018/04/16/tensorflow-in-your-browser/) no less.

  
  
from Hackaday https://ift.tt/2Osv5gL  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)