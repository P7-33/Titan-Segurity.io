---
title: 'I wrote Gocache: a complete and extensible Go cache library'
date: 2020-01-06T01:38:00+01:00
draft: false
---

![Gocache: Go cache library](https://vincent.composieux.fr/img/blog/gocache-high-load.jpg)

In the previous weeks, I wrote Gocache, an extensible and full of set cache library for Go developers. The goal of this library is to provide all that you need to start caching your data, maybe use multiple (chaning) cache, retrieve some metrics about things you cache and all the needs you could encounter.

History
=======

When I started working on implementing a cache on a GraphQL Go project, it already had a memory cache that used a little library that have a simple API but also used another memory cache library to load data using batch mode with a different library and API, to do the same thing: cache items. Later, we had another need: in addition of this memory cache, we wanted to add a layer of distributed cache using Redis principally to avoid our new Kubernetes pods to have an empty cache when rolling a new version of the application into production.

Here comes the Gocache idea: it's time to have a unified API to rule multiple cache storages: memory, redis, memcache or whatever you want.

Oh, that's not all, we also wanted to have metrics (to be scrapped by our Prometheus server) on these cache items.

Project Gocache is born: [https://github.com/eko/gocache](https://github.com/eko/gocache).

Store adapters
==============

First of all, when you want to cache items, you have to select where you want to cache your items: in memory? in a shared redis or memcache? or maybe in another storage.

At this time, Gocache have the following stores implemented:

*   [BigCache](https://github.com/allegro/bigcache): An in memory store,
*   [Ristretto](https://github.com/dgraph-io/ristretto): Another in memory store provided by DGraph,
*   [Memcache](https://github.com/bradfitz/gomemcache): A memcache store based on the bradfitz/gomemcache client library,
*   [Redis](https://github.com/go-redis/redis): A redis store based on the go-redis/redis client library.

All of these stores implement a really simple API that respect the following interface:

```
type StoreInterface interface { Get(key interface{}) (interface{}, error) Set(key interface{}, value interface{}, options *Options) error Delete(key interface{}) error Invalidate(options InvalidateOptions) error Clear() error GetType() string } 
```

This interface represents all the actions you can do on the stores and each of them call the necessary methods in the client libraries.

All of these stores have different configuration, depending on the client libraries you want to use, for instance, to initialize a Memcache store:

```
store := store.NewMemcache( memcache.New("10.0.0.1:11211", "10.0.0.2:11211", "10.0.0.3:11212"), &store.Options{ Expiration: 10*time.Second, }, ) 
```

Then, the initialized store have have to be passed into a cache object constructor.

Cache adapters
==============

One cache interface to rule them all. The cache interface is quite the same to the store one because basically, a cache will do actions on a store:

```
type CacheInterface interface { Get(key interface{}) (interface{}, error) Set(key, object interface{}, options *store.Options) error Delete(key interface{}) error Invalidate(options store.InvalidateOptions) error Clear() error GetType() string } 
```

With this interface, I have all the necessary actions I have to perform on my cache items: Set, Get, Delete, Invalidate data, Clear all the cache and another method (GetType) that allows to know what is the current cache item, useful in some cases.

Starting from this interface, the implemented cache types are the following:

*   `Cache`: The basic cache that allows to manipulate data from the given stores,
*   `Chain`: A special cache adapter that allows to chain multiple cache (could be because you have a memory cache, a redis cache, etc…),
*   `Loadable`: A special cache adapter that allows to specify a kind of callback function to automatically reload data into your cache if expired or invalidated,
*   `Metric`: A special cache adapter that allows to store metrics about your cache data: how many items setted, getted, invalidated, successfully or not.

The beauty comes when all of these cache implements the same interface and can be wrapped each other: a metrics cache can take a loadable cache that can take a chained cache that can take multiple caches.

Remember, I wanted to have a clean API. Here is a simple Memcache example:

```
memcacheStore := store.NewMemcache( memcache.New("10.0.0.1:11211", "10.0.0.2:11211", "10.0.0.3:11212"), &store.Options{ Expiration: 10*time.Second, }, ) cacheManager := cache.New(memcacheStore) err := cacheManager.Set("my-key", []byte("my-value"), &cache.Options{ Expiration: 15*time.Second, // Override default value of 10 seconds defined in the store }) if err != nil { panic(err) } value := cacheManager.Get("my-key") cacheManager.Delete("my-key") cacheManager.Clear() // Clears the entire cache, in case you want to flush all cache 
```

Now, let's say you want to have a chained cache with a memory Ristretto store and a distributed Redis store as a fallback, with a marshaller and metrics in bonus:

```
// Initialize Ristretto cache and Redis client ristrettoCache, err := ristretto.NewCache(&ristretto.Config{NumCounters: 1000, MaxCost: 100, BufferItems: 64}) if err != nil { panic(err) } redisClient := redis.NewClient(&redis.Options{Addr: "127.0.0.1:6379"}) // Initialize stores ristrettoStore := store.NewRistretto(ristrettoCache, nil) redisStore := store.NewRedis(redisClient, &cache.Options{Expiration: 5*time.Second}) // Initialize Prometheus metrics promMetrics := metrics.NewPrometheus("my-amazing-app") // Initialize chained cache cacheManager := cache.NewMetric(promMetrics, cache.NewChain( cache.New(ristrettoStore), cache.New(redisStore), )) // Initializes a marshaler marshal := marshaler.New(cacheManager) key := BookQuery{Slug: "my-test-amazing-book"} value := Book{ID: 1, Name: "My test amazing book", Slug: "my-test-amazing-book"} // Set the value in cache using given key err = marshal.Set(key, value) if err != nil { panic(err) } returnedValue, err := marshal.Get(key, new(Book)) if err != nil { panic(err) } // Then, do what you want with the value 
```

We didn't talked about the Marshaler yet but it's another feature of Gocache: we provided a service to help your automatically marshal/unmarshal your objects from/to your storages.

That's useful when working with struct objects as key and other than memory storages because you have to convert your objects into bytes.

All of these features: a chained cache with memory & redis, Prometheus metrics and marshaler are ready in only ~20 lines of code.

Write your own cache or storage
===============================

If you want to implement your own proprietary cache, it's also really easy to do.

Here is a simple example in case you want to log each action that is done in your cache (not really a good idea but well, that's simple todo as an example):

```
package customcache import ( "log" "github.com/eko/gocache/cache" "github.com/eko/gocache/store" ) const LoggableType = "loggable" type LoggableCache struct { cache cache.CacheInterface } func NewLoggable(cache cache.CacheInterface) *LoggableCache { return &LoggableCache{ cache: cache, } } func (c *LoggableCache) Get(key interface{}) (interface{}, error) { log.Print("Get some data...") return c.cache.Get(key) } func (c *LoggableCache) Set(key, object interface{}, options *store.Options) error { log.Print("Set some data...") return c.cache.Set(key, object, options) } func (c *LoggableCache) Delete(key interface{}) error { log.Print("Delete some data...") return c.cache.Delete(key) } func (c *LoggableCache) Invalidate(options store.InvalidateOptions) error { log.Print("Invalidate some data...") return c.cache.Invalidate(options) } func (c *LoggableCache) Clear() error { log.Print("Clear some data...") return c.cache.Clear() } func (c *LoggableCache) GetType() string { return LoggableType } 
```

In a same way, you can also implement a custom storage.

If you think other people can benefit your cache or storage implementation, please do not hesitate to open a pull request and contribute directly on the project so we could discuss your idea together and bring a more powerful cache library.

Conclusion
==========

By writing this library, I also try to improve the Go community tools to help build better softwares.

I hope you enjoyed this post and I would be happy to discuss about your needs or special use cases if you have some.

Finally, if you need some help implementing something about caching, do not hesitate to contact me via Twitter or email.

  
  
from Hacker News https://ift.tt/2QqKLS5