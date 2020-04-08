---
title: 'Message DB: Event Store and Message Store for PostgreSQL'
date: 2019-12-17T05:11:00+01:00
draft: false
---

![](https://blog.eventide-project.org/assets/images/message-db-logo-text-1200x630.png "Announcing Message DB: Event Store and Message Store for PostgreSQL - Eventide Blog")  

The Eventide Project team is excited to announce Message DB: A fully-featured event store and message store implemented in [PostgreSQL](https://www.postgresql.org) for pub/sub, event sourcing, and evented microservices applications.

For more specifics, visit Message DB on GitHub:  
[https://github.com/message-db/message-db](https://github.com/message-db/message-db)

Message DB was distilled from the [Eventide Project](http://docs.eventide-project.org) to make it easier for users to write clients in the language of their choosing.

Features:

*   Pub/Sub
*   JSON message data
*   Event streams
*   Stream categories
*   Metadata
*   Message queues
*   Message storage
*   Consumer groups
*   Service host
*   Administration tools
*   Reports

Use Message DB when you want to take advantage of the benefits of evented architecture but don’t want or need the the trade offs of technologies native to super-massive scale, like [Event Store](https://eventstore.org) or [Kafka](https://kafka.apache.org) clusters.

It’s an implementation of the minimum of features that are essential to evented applications, service architecture, and stream processing, but without the operations overhead of running infrastructure at extreme scale.

It’s built on the battle-tested data storage technology that you know and trust, supported by countless commodity cloud and hosting options like AWS, Google, and Heroku, with a massive open source and commercial ecosystem.

Message DB can be installed either as an NPM package, a Ruby Gem, or can simply be cloned from its Git repository.

It supports reading and writing events and commands to streams and categories, Pub/Sub, horizontal scale through consumer groups, concurrency protection via writes with an expected sequence number, an idempotence key mechanism, serialized writes, stream name parsing, and a host of other features.

A complete user guide is available on the Eventide Project docs site:  
[http://docs.eventide-project.org/user-guide/message-db/](http://docs.eventide-project.org/user-guide/message-db/)

Follow message DB on Twitter: [https://twitter.com/message\_db](https://twitter.com/message_db)

Happy eventing!

  
  
from Hacker News https://ift.tt/2tqexgT