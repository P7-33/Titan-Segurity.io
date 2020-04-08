---
title: 'Show HN: Schema.org with GitHub and scripts: A tool to make all data more useful'
date: 2019-10-16T08:47:00+01:00
draft: false
---

Case Study
----------

How would DitaBase look in practice?

* * *

#### Ecommerce

Let's suppose Jane has a product catalog:

SKU

Product Name

Category

Price

TRO-5593

TriCool Aluminum  
Water Bottle

Water Bottles

$16.99

She needs to upload this to her own Shopify site, Amazon, Walmart, Google Shopping and about 20 other sites. However, each site has a _slightly_ different schema, with tedious changes:

SKU

Product Name Title

Category Department

Price Sale Price

TRO-5593

TriCool Aluminum  
Water Bottle

Water Bottles  
Sports & Fitness : Accessories : Sports Water Bottles

$16.99  
16,99 USD

To deal with this, Jane manually creates and edits a different spreadsheet for every site. It is very annoying and time consuming.

Fortunately, Jane only has 50 products to worry about. But this means adding new products, or expanding to more websites is very difficult, if not impossible.

#### How can DitaBase make this easier?

On DitaBase, someone may have already made a `ProductEcommerceAmazon` schema, which would be a child of the `ProductEcommerce` schema. The schemas would have all the validators and converters necessary to convert between them.

This means Jane can simply make one spreadsheet that complies with `ProductEcommerce` and then automatically convert the data to every other website. If a website doesn't have a schema, she can easily hire a freelancer to write one for that site.

* * *

#### Cross Industry

Now let's meet Tom. Tom is laying out a construction project, up in the mountains. He contracted with a Land Surveying company, which produced data that looks like this:

GPS Point

North

East

Elevation

Datum

t-125

24504.145

17948.076

3543.846

NAD83

t-126

24508.491

17950.059

3543.347

NAD83

Tom also contracted with a satellite imaging service, which produced a series of photographs so that Tom would know the number and location of trees and other land features. The photographs came with metadata which give estimates of coordinates and number of trees:

```
 `{ "images": [ { "file": "19-05-17-10:30:45:231.png", "coordinate": "41°29'14.1\"N 76°50'14.9\"W", "trees": [ "41°29'12.5\"N 76°50'10.6\"W", "41°29'12.1\"N 76°50'10.6\"W", "41°29'11.8\"N 76°50'10.7\"W", "41°29'11.1\"N 76°50'10.4\"W" ] } ] }`
```

It would save Tom a lot of time and money to be able to work with a single dataset instead of each one separately. Unfortunately, their data doesn't look alike at all, even though they are theoretically similar industries.

This also isn't the first time Tom has needed two dissimilar survey data sets to work together. The last time, Tom couldn't find another solution and hired a programmer to write custom scripts. But that was a one time solution and won't work here. What a waste of money!

#### With DitaBase...

If both or even one of the companies had their data extend the `Coordinate` schema, then Tom could convert both data sets that far and do the rest manually. Even though it's an odd, one time situation, DitaBase still helps Tom enormously.

* * *

#### Inter-Company

Sara is the CTO of large medical company, which just acquired a small medical startup. Sara's company has an old codebase, of which one component is a MySQL database. The startup has an amazing API and codebase, which includes MongoDB.

Somehow, Sara wants to move over to using the new codebase, but this must be handled delicately. Ideally, the MySQL and MongoDB could both be live in the interim, without developing a costly and unnecessary API for the old codebase.

#### DitaBase again!

Sara knows that all their customer data will be carried over using the old schema. This means that they can write a child of the DitaBase `PersonMedical` schema, and have a version for MongoDB and SQL.

DitaBase makes abstracting the container from the data itself very easy. Add a two way converter and the databases can be used as though they were a single system.

PersonID

Name

Age

Blood Type

GUL-89323

John Doe

36

O-

MAL-34106

Jane Doe

67

AB+

PersonID

ConditionID

MAL-34106

1342

MAL-34106

1305

ConditionID

Condition

1342

Arthritis

1305

High Blood Pressure

```
 `{ "people": [ { "_id": "GUL-89323", "name": "John Doe", "age": 36, "blood-type": "O-" }, { "_id": "MAL-34106", "name": "Jane Doe", "age": 67, "blood-type": "AB+", "conditions": [ "Arthritis", "High Blood Pressure" ] } ] }` 
```

  
  
from Hacker News http://www.ditabase.io/