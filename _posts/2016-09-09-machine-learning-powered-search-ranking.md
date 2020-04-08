---
title: 'Machine Learning-Powered Search Ranking of Airbnb Experiences'
date: 2019-10-27T03:52:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*94HRsddpMqQbWt0nGm3ENw.png "Machine Learning-Powered Search Ranking of Airbnb Experiences")  

Since offline testing often has too many assumptions, e.g. in our case it was limited to re-ranking what users clicked and not the entire inventory, we conducted an online experiment, i.e. A/B test, as our next step. We compared the Stage 1 ML model to the rule-based random ranking in terms of number of bookings. The results were very encouraging as we were able to **improve bookings by +13%** with the Stage 1 ML ranking model.

**Implementation details:** In this stage, our ML model was limited to using only _Experience Features,_ and as a result, the ranking of Experiences was the same for all users. In addition, all query parameters (number of guests, dates, location, etc.) served only as filters for retrieval (e.g. fetch Paris Experiences available next week for 2 guests), and ranking of Experiences did not change based on those inputs.

Given such a simple setup, the entire ranking pipeline, including training and scoring, was implemented offline and ran daily in [Airflow](https://airflow.apache.org). The output was just a complete ordering of all Experiences, i.e. an ordered list, which was uploaded to production machines and used every time a search was conducted to rank a subset of Experiences that satisfied the search criteria.

Stage 2: Personalize
====================

The next step in our Search Ranking development was to add the _Personalization_ capability to our ML ranking model.

From the beginning, we knew that Personalization was going to play a big role in the ranking of Experiences because of the diversity of both the inventory and the guest interest.

Unlike our Home business, where two _Private Rooms_ in the same city at a similar price point are very similar, two randomly chosen Experiences are likely to be very different, e.g. a _Cooking Class_ vs. a _Surf Lesson_. At the same time, guests may have different interests and ideas of what they want to do on their trip, and it is our goal to capture that interest fast and serve the right content higher in search results.

We introduced two different types of personalization, mostly by doing feature engineering given collected data about users.

1\. Personalize based on booked Airbnb Homes
--------------------------------------------

A large portion of Experience bookings come from guests who already booked an Airbnb Home. Therefore, we have quite a bit of information we can use to build features for personalization:

*   **Booked Home location**
*   **Trip dates**
*   **Trip length**
*   **Number of guests**
*   **Trip price** (Below/Above Market)
*   **Type of trip:** Family, Business
*   **First trip or returning to location**
*   **Domestic / International trip**
*   **Lead days**

To give examples of features that can be built to guide ranking, we demonstrate two important ones:

*   _Distance between Booked Home and Experience._ Knowing Booked Home location (latitude and longitude) as well as Experience meeting location, we can compute their distance in miles. Data shows that users like convenience, i.e. large fraction of booked Airbnb Experiences are near booked Airbnb Home.
*   _Experience available during Booked Trip._ Given Home check-in and check-out dates, we have an idea on which dates the guest is looking to book Experiences and can mark Experiences as _available_ or _not_ during those dates.

These two features (in addition to others) were used when training the new ML ranking model. Below we show their partial dependency plots.

The plots confirmed that features behavior matches what we intuitively expected the model will learn, i.e. Experiences that are closer to Booked Home will rank higher (have higher scores), and Experiences that are available for Booked Trip dates will rank higher (which is very convenient because even in dateless search we can leverage trip dates).

2\. Personalize based on the user’s clicks
------------------------------------------

Given the user’s short-term search history, we can infer useful information that can help us personalize future searches:

*   **Infer user interest in certain categories:** For example, if the user is mostly clicking on _Music_ Experiences we can infer that the user’s interest is in _Music_
*   **Infer the user’s time-of-day availability:** For example, if the user is mostly clicking on _Evening_ Experiences we can infer that the user is available at that time of day

At the time they are published to the platform, each Experience is manually tagged with a category (e.g. hiking, skiing, horseback riding, etc.). This structured data gives us the ability to differentiate between types of Experiences. It also gives us the ability to create user interest profiles in each category by aggregating their clicks on different categories.

For this purpose, we compute two features derived from user clicks and categories of clicked Experiences:

**Category Intensity:** Weighted sum of user clicks on Experiences that have that particular category,

where the sum is over the last 15 days (d\_0 to d\_now) and _A_ is the number of actions (in this case clicks) on certain category on day _d._

**Category Recency:** Number of days that passed since the user last clicked on an Experience in that category.

Note that the user may have clicked on many different categories with different intensities and recencies, but when the feature is computed for a particular Experience that needs to be ranked, we use the intensity and recency of that Experience category.

To illustrate what our model learned for these two features, we show the partial dependency plots below. As it can be observed on the left side, Experiences in categories for which the user had high intensities will rank **higher.** At the same time, having the recency feature (on the right) allows the model to forget history as time goes by, and Experiences in categories that the user last clicked a long time ago will rank **lower.**

We built the same types of features (intensity & recency) for several different user actions, including wishlisting and booking a certain category.

**Time of Day Personalization:** Different Experiences are held at different times of day (e.g. early morning, evening, etc.). Similar to how we track clicks on different categories, we can also track clicks on different times of day and compute _Time of Day Fit_ between the user’s time-of-day percentages and the Experience’s time of day, as described below.

As it can be observed, the model learned to use this feature in a way that ranks Experiences held at time of day that the user prefers higher.

**Training the ranking model:** To train the model with _Personalization_ features, we first generated training data that contains those features by reconstructing the past based on search logs. By that time we already had a bigger inventory (4000 experiences) and were able to collect more training data (250K labeled examples) with close to 50 ranking features.

When creating personalization features it is _very important_ not to “_leak the label,”_ i.e. expose some information that happened after the event used for creating the label. Therefore, we only used user clicks that happened before bookings. In addition, to reduce leakage further, when creating training data we computed the personalization features only if the user interacted with more than one Experience and category (to avoid cases where the user clicked only one Experience / category, e.g. _Surfing_, and ended up booking that category).

Another important aspect to think about was that our search traffic contains searches by both _logged-in_ and _logged-out_ users. Considering this, we found it more appropriate to train **two models**, one with personalization features for _logged-in_ users and one without personalization features that will serve _log-out_ traffic. The main reason was that the _logged-in_ model trained with personalization features relies too much on the presence of those features, and as such is not appropriate for usage on _logged-out_ traffic.

**Testing the ranking model:** We conducted an A/B test to compare the new setup with 2 models with Personalization features to the model from Stage 1. The results showed that Personalization matters as we were able to **improve bookings by +7.9%** compared to the Stage 1 model.

**Implementation details:** To implement serving of the Stage 2 model in production, we chose a simple solution that required the least time to implement. We created a look-up table keyed off of user id that contained personalized ranking of all Experiences for that user, and use key 0 for ranking for logged-out users.

This required daily offline computation of all these rankings in [Airflow](https://airflow.apache.org) by computing the latest features and scoring the two models to produce rankings. Because of the high cost involved with pre-computing personalized rankings for all users (_O_(_NM_), where _N_ is the number of users and _M_ is the number of Experiences), we limited _N_ to only 1 million most active users.

The personalization features at this point were computed only daily, which means that we have up to one day latency (also a factor that can be greatly improved with more investment in infrastructure).

Stage 2 implementation was a temporary solution used to validate personalization gains before we invest more resources in building an **_Online Scoring Infrastructure_** in Stage 3, which was needed as both _N_ and _M_ are expected to grow much more.

Stage 3: Move to Online Scoring
===============================

After we demonstrated significant booking gains from iterating on our ML ranking model and after inventory and training data grew to the extent where training a more complex model is possible, we were ready to invest more engineering resources to build an _Online Scoring Infrastructure_ and target more booking gains.

Moving to _Online Scoring_ also unlocks a whole new set of features that can be used: _Query Features_ (highlighted in image below).

This means that we would be able to use the entered _location_, _number of guests_, and _dates_ to engineer more features.

For example, we can use the entered _location_, such as city, neighborhood, or place of interest, to compute _Distance between Experience and Entered Location_. This feature helps us rank those Experiences closer to entered location higher.

In addition, we can use the entered _number of guests_ (singles, couple, large group) to calculate how it relates to the number of guests in an average booking of Experience that needs to be ranked. This feature helps us rank better fit Experiences higher.

In the online setting, we are also able to leverage the user’s _browser language_ setting to do language personalization on the fly. Some Experiences are offered and translated in multiple languages. If the browser setting language translation is available, that one is displayed. With ranking in the online world we can take it a step further and rank language-matching Experiences higher by engineering a feature that determines if the _Experience is offered in Browser Language_. In the image below we show an example of Stage 3 ML model ranking Experiences offered in Russian higher when browser language is Russian.

Finally, in the online setting we also know the Country which the user is searching from. We can use the country information to personalize the Experience ranking based on Categories preferred by users from those countries. For example, historical data tells us that when visiting Paris _Japanese travelers_ prefer _Classes & Workshops (e.g. Perfume making)_, _US travelers_ prefer _Food & Drink Experiences_, while _French travelers_ prefer _History & Volunteering_. We used this information to engineer several personalization features at the Origin — Destination level.

**Training the ranking model:** To train the model with _Query Features_ we first added them to our historical training data. The inventory at that moment was 16,000 Experiences and we had more than 2 million labeled examples to be used in training with a total of 90 ranking features. As mentioned before, we trained two GBDT models:

*   **Model for logged-in users**_,_ which uses _Experience Features_, _Query Features,_ and _User (Personalization) Features_
*   **Model for logged-out traffic**, which uses _Experience & Query Features,_ trained using data (clicks & bookings) of logged-in users but not considering _Personalization Features_

The advantage of having an online scoring infrastructure is that we can use _logged-in_ model for **far more** uses than before, because there is no need to pre-compute personalized rankings as we did in Stage 2. We used the _logged-in_ model whenever personalization signals were available for a particular user id, else we fall back to using _logged-out_ model.

**Testing the ranking model:** We conducted an A/B test to compare the Stage 3 models to Stage 2 models. Once again, we were able to **grow the bookings, this time by +5.1%**.

**Implementation details:** To implement online scoring of thousands of listings in real time, we have built our own ML infra in the context of our search service. There are mainly three parts of the infrastructure, 1) getting model input from various places in real time, 2) model deployment to production, and 3) model scoring.

The model requires three types of signals to conduct scoring: _Experience Features_, _Query Features,_ and _User Features_. Different signals were stored differently depending on their size, update frequency, etc. Specifically, due to their large size (hundreds of millions of user keys), the _User Features_ were stored in an _online key-value store_ and search server boxes can look them up when a user does the search. The _Experience Features_ are on the other hand not that large (tens of thousands of Experiences), and as such can be stored in memory of the search server boxes and read directly from there. Finally, the _Query Features_ are not stored at all, and they are just read as they come in from the front end.

_Experience and User Features_ are both updated daily as the Airflow pipeline feature generation job finishes. We are working on transitioning some of the features to the online world, by using a key-value store that has both read and write capabilities which would allow us to update the features instantly as more data comes in (e.g. new experience reviews, new user clicks, etc.).

In the model deployment process, we transform the GBDT model file, which originally came from our training pipeline in JSON format, to an internal Java GBDT structure, and load it within the search service application when it starts.

During the scoring stage, we first pull in all the features (_User, Experience, and Query Features_) from their respective locations and concatenate them in a vector used as input to the model. Next, depending on if _User Features_ are empty or not we decide which model to use, i.e. _logged-out_ or _logged-in_ model, respectively. Finally, we return the model scores for all Experiences and rank them on the page in descending order of the scores.

Stage 4: Handle Business Rules
==============================

Up to this point our ranking model’s objective was to grow bookings. However, a marketplace such as Airbnb Experiences may have several other secondary objectives, as we call them _Business Rules,_ that we can help achieve through machine learning_._

One such important Business Rule is to **Promote Quality**. From the beginning we believed that if guests have a really good experience they will come back and book Experiences again in the near future. For that reason, we started collecting feedback from users in terms of 1) star ratings, ranging from 1 to 5, and 2) additional structured multiple-response feedback on whether the Experience was _unique, better than expected, engaging, etc._

As more and more data became available to support our rebooking hypothesis, the trend became more clear. As it can be observed on the left in the figure below, guests who have had a great experience (leave a 5-star rating) are 1.5x more likely to rebook another Experience in the next 90 days compared to guests who have had a less good time (leave 4 star rating or lower).

This motivated us to experiment with our objective function, where we changed our binary classification (+1 = booked, -1 = click & not booked) to introduce weights in training data for different quality tiers (e.g. highest for very high quality bookings, lowest for very low quality bookings). The quality tiers were defined by our Quality Team via data analysis. For example:

*   _very high quality_ Experience is one with >50 reviews, >4.95 review rating and >55% guests saying the Experience was _unique_ and _better than expected._
*   _very low quality_ Experience is one with >10 reviews, <4.7 review rating.

When testing the model trained in such a way the A/B test results (on the right in the figure above) showed that we can leverage machine learning ranking to get more of v_ery high quality_ bookings and less of v_ery low quality bookings_, while keeping the overall bookings neutral.

In a similar way, we successfully tackled several other secondary objectives:

*   **Discovering and promoting potential _new_ _hits_ early** using cold-start signals and promoting them in ranking (this led to **+14% booking gain for _new hits_** and neutral overall bookings)
*   **Enforcing diversity** in the **top 8 results** such that we can show the diverse set of categories, which is especially important for low-intent traffic (this led to **+2.3% overall booking gain**).
*   **Optimize Search without Location for Clickability** For _Low Intent_ users that land on our webpage but do not search with specified location we think a different objective should be used. Our first attempt was to choose the _Top 18_ from _all locations_ based on our ranking model scores and then **re-rank** based on **Click-through-rate** (this led to **+2.2% overall booking gain** compared to scenario where we do not re-rank based on CTR).

Monitoring and Explaining Rankings
==================================

For any two-sided marketplace it is very important to be able to explain why certain items rank the way they do.

In our case it is valuable because we can:

*   Give hosts concrete feedback on what factors lead to improvement in the ranking and what factors lead to decline.
*   Keep track of the general trends that the ranking algorithm is enforcing to make sure it is the behavior we want to have in our marketplace.

To build out this capability we used [Apache Superset](https://superset.incubator.apache.org) and [Airflow](https://airflow.apache.org) to create two dashboards:

*   Dashboard that tracks rankings of specific Experiences in their market over time, as well as values of feature used by the ML model.
*   Dashboard that shows overall ranking trends for different groups of Experiences (e.g. how 5-star Experiences rank in their market).

To give an idea of why these types of dashboards can be useful we give several examples in the figures that follow.

In the figure below we show an example of an Experience whose ranking (left panel) **improved** from position 30 to position 1 (top ranked). To explain why, we can look at the plots that track various statistics of that Experience (right panel), which are either directly used as features in the ML model or used to derive features.

  
  
from Hacker News https://ift.tt/2tAsju8