---
title: 're:Invent 2019 Python powered
badge @AWSreInvent #reInvent @circuitpython'
date: 2019-12-01T22:58:00+01:00
draft: false
---

![12319Awspybadge](https://cdn-blog.adafruit.com/uploads/2019/12/12319awspybadge.jpg)

This project displays a count of the AWS service announcements during the week of re:Invent. The physical display is [PyBadge](https://www.adafruit.com/product/4200) with a code project running on it inspired by the [PyBadge tutorial](https://learn.adafruit.com/pybadger-event-badge). The data for the project is pulled from the [AWS announcement](https://aws.amazon.com/new/) [RSS feed](https://aws.amazon.com/about-aws/whats-new/recent/feed/). The data is polled hourly by a lambda function, which stores all the announcements, and updates a counter. A second lambda function and API gateway serve as the endpoint for the pyBadge to fetch the stats from – [GitHub](https://github.com/estranged42/pybadge-reinvent-2019).