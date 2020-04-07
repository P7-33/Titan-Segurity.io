---
title: 'Big Prometheus: Thanos, Cortex, M3DB and VictoriaMetrics at Scale'
date: 2020-01-09T01:17:00+01:00
draft: false
---

A [recent paper from Google that will probably have an impact on the future of large-scale data processing](https://research.google/pubs/pub48388/) summarizes the situation facing many companies in early 2020:

_“Large organizations… are dealing with exploding data volume and increasing demand for data driven applications. Broadly, these can be categorized as: reporting and dashboarding, embedded statistics in pages, time-series monitoring, and ad-hoc analysis. Typically, organizations build specialized infrastructure for each of these use cases. This, however, creates silos of data and processing, and results in a complex, expensive, and harder to maintain infrastructure.”_

There are a number of interesting projects and startups addressing this problem in the open-source monitoring world, particularly for teams with dozens or hundreds of Kubernetes clusters using **[Prometheus](https://prometheus.io/)** for monitoring.

Prometheus, usually combined with **[Grafana](https://grafana.com/)** for dashboards and reporting, has become the de-facto standard for open-source monitoring in [Kubernetes](https://kubernetes.io/) and one of the [Cloud Native Computing Foundation’s](https://landscape.cncf.io/format=card-mode&grouping=organization&organization=cloud-native-computing-foundation-cncf&project=graduated) most popular projects. (The [Apache Foundation](https://www.apache.org/foundation/) also has an open-source APM project called **[Skywalking](https://skywalking.apache.org/)** that I’m told is big in China.)

A common configuration is to run a single Prometheus server per Kubernetes cluster, which is getting easier to setup and run with projects like [Prometheus Operator](https://github.com/coreos/prometheus-operator). With dozens to hundreds of clusters in an organization—Cloudflare was running _188_ [in 2017](https://www.infoq.com/news/2017/10/monitoring-cloudflare-prometheus/)—it’s complicated to maintain and slow to globally query so many Prometheuses (Prometheii?). 

[![](https://cdn.substack.com/image/fetch/w_1100,c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F6a548b2b-6fe1-4d86-8e59-d4b5756efb1e_850x468.png)](https://cdn.substack.com/image/fetch/c_limit,f_auto,q_auto:good/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F6a548b2b-6fe1-4d86-8e59-d4b5756efb1e_850x468.png)

There are four major open-source database projects written in Go working on this problem: **[Thanos](https://thanos.io/)**, **[Cortex](https://cortexmetrics.io/)**, **[M3DB](https://www.m3db.io/)**, and **[VictoriaMetrics](https://victoriametrics.com/)**. Their goals are similar:

*   Prometheus compatibility (integrate easily with existing Kubernetes clusters)
    
*   Global, fast queries (see all the data from everywhere quickly)
    
*   Long-term historical metrics (policies to store long-term metrics cheaply)
    
*   High availability (resiliency against crashes without data loss)
    

Here’s a brief overview:

### Thanos and Cortex

Thanos and Cortex are similar enough in terms of the problems they aim to solve that there was a talk at [PromCom 2019](https://promcon.io/2019-munich/) (the Prometheus conference) from [Tom Wilkie](https://twitter.com/tom_wilkie?lang=en) with the delightful title [“Two Households, Both Alike in Dignity: Cortex and Thanos”](https://grafana.com/blog/2019/11/21/promcon-recap-two-households-both-alike-in-dignity-cortex-and-thanos/). 

Cortex behaves like typical SaaS monitoring where data is pushed to a central location from remote servers (but using [native Prometheus APIs](https://prometheus.io/docs/operating/integrations/#remote-endpoints-and-storage)). Thanos is less-centralized and data remains within each Prometheus server—which is how Prometheus operates by default. These two different approaches result in different technical approaches for answering global queries like “which of my clusters is on fire?”. Tom Wilkie’s talk [has more details](https://grafana.com/blog/2019/11/21/promcon-recap-two-households-both-alike-in-dignity-cortex-and-thanos/).

The other interesting architectural aspect of both projects is they both can leverage cloud-managed services to store long-term historical data (“what was the error rate seven weeks ago?”) in order to lower operational cost.

Thanos can use cheap-ish object-stores like [Amazon S3](https://aws.amazon.com/s3/) or [Azure Blob Storage](https://azure.microsoft.com/en-us/services/storage/blobs/), while Cortex prefers more expensive NoSQL stores like [AWS DynamoDB](https://aws.amazon.com/dynamodb/) or [Google BigTable](https://cloud.google.com/bigtable/). (Cortex is now adding support for object-stores as well.) This lets teams adopting either project make deliberate choices around cost and performance for historical metrics.

It seems like there will be more collaboration between the projects in the future, and [there’s a juicy twitter hot take on it](https://twitter.com/fredbrancz/status/1043060822988259333?lang=en).

### M3DB

[Uber wrote their own thing, too](https://eng.uber.com/m3/). 

M3DB follows a Thanos-like model, but [according to a post from the creator on Hacker News](https://news.ycombinator.com/item?id=17713374), the main issue in adopting Thanos was that Uber frequently needed historical metrics that were too slow to fetch from an object-store like Amazon S3 and there were massive bandwidth costs when historical data was moving between the cloud and Uber’s on-prem data centers.

There’s now a startup called **[Chronosphere](https://chronosphere.io/)** that has spun off from this work and they’ve raised an [$11 million Series-A round from Greylock Partners](https://techcrunch.com/2019/11/05/chronosphere-launches-with-11m-series-a-to-build-scalable-cloud-native-monitoring-tool/). According to TechCrunch, it will will take over management of the M3 project going forward.

### VictoriaMetrics

Like M3DB, Thanos, and Cortex, the creators of VictoriaMetrics also faced a cost and performance problem. They were inspired by ideas from **[ClickHouse](https://clickhouse.yandex/)**, a cool kid database created by Yandex that people [publish extremely impressive performance and cost metrics for when they run it on a three-year old Intel hardware](https://www.altinity.com/blog/2020/1/1/clickhouse-cost-efficiency-in-action-analyzing-500-billion-rows-on-an-intel-nuc).

The VictoriaMetrics team, [according to their FAQ](https://github.com/VictoriaMetrics/VictoriaMetrics/wiki/FAQ), is prioritizing low operational cost and good developer/operator experience. There’s even a way to run it in a single node configuration. The performance numbers [look impressive](https://medium.com/@valyala/measuring-vertical-scalability-for-time-series-databases-in-google-cloud-92550d78d8ae), and it seems like they also sell (or plan to sell) some kind of managed cloud service.

Coming soon to a startup near you?
----------------------------------

At this point, you mind be asking, “why bother? I’d rather pay \[SaaS vendor\] and not deal with any of this.”

The interesting thing is \[SaaS vendor\] may very well be using one of these projects to power the oberservability solution they’re selling. Cortex, notably, is being used by **[Weave Cloud](https://cloud.weave.works/)**, **[Grafana Cloud](https://grafana.com/products/cloud/)**, and a new enterprise service mesh called **[AspenMesh](https://aspenmesh.io/)**. Thanos was developed at (and is presumably still being used by) the gaming software company **[Improbable](https://improbable.io/)** and M3DB, of course, is being used at Uber. 

Another exciting thing about these projects is that they offer a front-row seat to talented engineers solving hard distributed systems problems related to large-scale monitoring and making different decisions along the way. All this activity suggests a healthy open-source ecosystem that’s supporting a number of observability startups and providing solutions for other companies that need to run some kind of Big Prometheus. There are more high-quality open-source choices than ever.

Thanks for reading. If you enjoyed this newsletter, feel free to share using the link below or subscribe [here](https://monitoring2.substack.com/).

_Disclosure: Opinions my own. I am not employed, consulting, or an investor in any of the mentioned companies or their competitors._

  
  
from Hacker News https://ift.tt/2T6y7te