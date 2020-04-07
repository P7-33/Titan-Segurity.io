---
title: 'Show HN: Chromda – Serverless Website Screenshots'
date: 2019-12-30T03:55:00+01:00
draft: false
---

[![](https://github.com/luisfarzati/chromda/raw/master/chromda.png)](https://github.com/luisfarzati/chromda/blob/master/chromda.png)

[](https://github.com/luisfarzati/chromda#chromda-serverless-screenshots)Chromda – Serverless screenshots
=========================================================================================================

Chromda is an AWS Lambda function for serverless capturing screenshots of websites.

### [](https://github.com/luisfarzati/chromda#multiple-sources)Multiple sources

*   SNS topics
*   SQS queues
*   CloudWatch scheduled events
*   API Gateway proxy

### [](https://github.com/luisfarzati/chromda#configurable)Configurable

*   Capture full page, viewport or specific DOM element
*   Exclude DOM elements (useful for ads or other unwanted content)
*   Override styles

[](https://github.com/luisfarzati/chromda#quick-start)Quick start
-----------------------------------------------------------------

Provided you already have AWS credentials for Serverless, do:

```
git clone https://github.com/luisfarzati/chromda cd chromda git submodule update --init npm install
```

Edit the `serverless.yml` file and change the example bucket name with one of your own:

```
# serverless.yml custom: s3Bucket: 
```

Deploy the function into your AWS account:

Open the [AWS Lambda Console](https://console.aws.amazon.com/lambda/home?region=us-east-1#/functions/chromda-dev-captureScreenshot) and create the following test event:

```
{ "source": "aws.events", "time": "1970-01-01T00:00:00Z", "detail": { "url": "https://www.nytimes.com" } }
```

Click **Test**, wait a few seconds (it might take around 8-10 secs), then you should see a response like:

```
{ "url": "https://.s3.amazonaws.com/.png" }
```

[](https://github.com/luisfarzati/chromda#usage)Usage
-----------------------------------------------------

### [](https://github.com/luisfarzati/chromda#invocation)Invocation

The function accepts different kind of events, extracting the data from the proper body attribute as follows:

### [](https://github.com/luisfarzati/chromda#options)Options

```
{ // required "url": "https://google.com", // optional - valid options: page, viewport, element // default: viewport "capture": "page", // selector of element to capture // required if capture: element "selector": ".container", // optional - S3 key for the image file // default: uuid() "s3key": "test.png", // optional - selectors of elements to exclude "exclude": \[".ad", "video"\], // optional - styles to override // see Puppeteer.addStyleTag "styles": \[ { "content": "body { color: #f00; }" } \], // optional - puppeteer options "puppeteer": { // see Puppeteer.goto options "navigation": { "timeout": 30000, "waitUntil": \["domcontentloaded", "networkidle2"\] }, // see Puppeteer.screenshot options "screenshot": { "type": "jpeg", "quality": 50, "omitBackground": false }, // viewport size, overrides env defaults "viewport": { "width": 1200, "height": 2000 } } }
```

### [](https://github.com/luisfarzati/chromda#environment-variables)Environment Variables

Name

Default

S3\_BUCKET\*

S3\_REGION\*

S3\_ACL

`"public-read"`

CHROMIUM\_ARGS

`"[]"`

TIMEOUT

`"30000"`

IGNORE\_HTTPS\_ERRORS

`"false"`

VIEWPORT\_WIDTH

`"1920"`

VIEWPORT\_HEIGHT

`"1200"`

DEVICE\_SCALE\_FACTOR

`"1"`

IS\_MOBILE

`"false"`

IS\_LANDSCAPE

`"false"`

[](https://github.com/luisfarzati/chromda#deploy)Deploy
-------------------------------------------------------

```
# serverless.yml # ... custom: s3Bucket:  provider: # ... layers: # Replace  with the latest version of chrome-aws-lambda-layer # It depends on the region you are deploying. # https://github.com/shelfio/chrome-aws-lambda-layer#available-regions - arn:aws:lambda:${self:provider.region}:764866452798:layer:chrome-aws-lambda: functions: captureScreenshot: # ... environment: # configure the environment variables VIEWPORT\_WIDTH: "1920" VIEWPORT\_HEIGHT: "1200" # ... events: # add any of the supported event source(s) you want to use # the provided example uses SNS - sns: arn: !Ref chromdaTopic topicName: ${self:custom.snsTopic} resources: # following the example, we provision an SNS topic chromdaTopic: Type: AWS::SNS::Topic Properties: TopicName: ${self:custom.snsTopic}
```

[](https://github.com/luisfarzati/chromda#x-ray)X-Ray
-----------------------------------------------------

AWS X-Ray support is provided and there are segments for Puppeteer navigation and screenshot:

[![AWS X-Ray screenshot](https://camo.githubusercontent.com/a629676ead1375722638f594a8fab75ca314a0de/68747470733a2f2f692e696d6775722e636f6d2f7559773550684c2e706e67)](https://camo.githubusercontent.com/a629676ead1375722638f594a8fab75ca314a0de/68747470733a2f2f692e696d6775722e636f6d2f7559773550684c2e706e67)

  
  
from Hacker News https://ift.tt/39rfNky