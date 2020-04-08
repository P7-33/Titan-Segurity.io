---
title: 'Show HN: Unifrost – Stream PubSub Messages to the Browser'
date: 2019-12-20T07:46:00+01:00
draft: false
---

[](https://github.com/unifrost/unifrost#unifrost-a-go-module-that-makes-it-easier-to-stream-pubsub-events-to-the-web)unifrost: A go module that makes it easier to stream pubsub events to the web
==================================================================================================================================================================================================

[![GoDoc](https://camo.githubusercontent.com/732c479a0792ceb9ee4fc75414f8e13da8c73e8e/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f72616a766565726d616c766979612f756e6966726f73743f7374617475732e737667)](https://godoc.org/github.com/rajveermalviya/unifrost) [![Go Report Card](https://camo.githubusercontent.com/75fa26606662cd1e4e6eb4e119d318f5ced4f36c/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f72616a766565726d616c766979612f756e6966726f7374)](https://goreportcard.com/report/rajveermalviya/unifrost) [![FOSSA Status](https://camo.githubusercontent.com/912f8e4dff3d82533382045fc4af7b6fd98cb6ea/68747470733a2f2f6170702e666f7373612e696f2f6170692f70726f6a656374732f6769742532426769746875622e636f6d25324672616a766565726d616c76697961253246756e6966726f73742e7376673f747970653d736869656c64)](https://app.fossa.io/projects/git%2Bgithub.com%2Frajveermalviya%2Funifrost?ref=badge_shield) [![CII Best Practices](https://camo.githubusercontent.com/1ad245af753b55cacb9498f15f9586d48f676b7f/68747470733a2f2f626573747072616374696365732e636f7265696e6672617374727563747572652e6f72672f70726f6a656374732f333239382f6261646765)](https://bestpractices.coreinfrastructure.org/projects/3298)

⚠ This project is on early stage, it's not ready for production yet ⚠

Previously named gochan

unifrost is a go module for relaying pubsub messages to the web via [SSE(Eventsource)](https://en.wikipedia.org/wiki/Server-sent_events). It is based on Twitter's implementation for real-time event-streamingin their new web app.

unifrost is named after bifrost, the rainbow bridge that connects Asgard with Midgard (Earth), that is MCU reference which is able to transport people both ways. But because unifrost sends messages from server to client (only one way), hence unifrost. 😎

It uses the [Go CDK](https://gocloud.dev) as vendor neutral pubsub driver that supports multiple pubusub vendors:

*   Google Cloud Pub/Sub
*   Amazon Simple Queueing Service (Pending)
*   Azure Service Bus (Pending)
*   RabbitMQ
*   NATS
*   Kafka
*   In-Memory (Only for testing)

[](https://github.com/unifrost/unifrost#installation)Installation
-----------------------------------------------------------------

unifrost supports Go modules and built against go version 1.13

```
go get github.com/rajveermalviya/unifrost
```

[](https://github.com/unifrost/unifrost#documentation)Documentation
-------------------------------------------------------------------

For documentation check [godoc](https://godoc.org/github.com/rajveermalviya/unifrost).

[](https://github.com/unifrost/unifrost#usage)Usage
---------------------------------------------------

unifrost uses Server-Sent-Events, because of this it doesn't require to run a standalone server, unlike websockets it can be embedded in your api server. unifrost's streamer has a ServeHTTP method i.e it implements http.Handler interface so that it can be used directly or can be wrapped with middlewares like Authentication easily.

```
// Using streamer directly streamer, err := unifrost.NewStreamer( &memdriver.Client{}, unifrost.ClientTTL(2\*time.Second), ) log.Fatal("HTTP server error: ", http.ListenAndServe("localhost:3000", streamer))
```

```
// Using streamer by wrapping it in auth middleware streamer, err := unifrost.NewStreamer( &memdriver.Client{}, unifrost.ClientTTL(2\*time.Second), ) mux := http.NewServeMux() mux.HandleFunc("/events", func (w http.ResponseWriter, r \*http.Request) { err := Auth(w,r) if err != nil { return } streamer.ServeHTTP(w,r) }) log.Fatal("HTTP server error: ", http.ListenAndServe("localhost:3000", mux))
```

When client connects to the server it will send a message that will contain two things the configuration and an array of all the topics to which the client has subscribed.

1.  Configuration: it contains the client-id and client-ttl set by the streamer config
2.  Subscriptions associated with the specified client id.

Example first message:

```
{ "config": { "client\_id": "9ba6f4e1-8f80-4e61-944e-e3f409ae514f", "client\_ttl\_millis": 60000 }, "subscriptions": \["topic5", "topic1", "topic3", "topic4"\] }
```

Example error messaage:

```
{ "error": { "topic": "topic10", "code": "subscription-failure", "message": "Cannot recieve message from subscription, closing subscription" } }
```

All the info events are streamed over message channel i.e using the EventSource JS API, `onmessage` or `addEventListener('message', () => {})` method will listen to them. All the subscription events have event name same as their topic name, so to listen to topic events you need to add an event-listener on the EventSource object.

Client example:

```
const sse \= new EventSource('/events?id=9ba6f4e1-8f80-4e61-944e-e3f409ae514f'); // for info events like first-message and errors sse.addEventListener('message', e \=> { console.log(e); }); // for subscription events sse.addEventListener('topic10', e \=> { console.log(e); });
```

**Note:** _The only way to listen to subscription events is by adding an eventlistener to that specific topic. `onmessage` method will only listen to info messages._

New client is created explicitly using the `streamer.NewClient()` for client with auto generated id or `streamer.NewCustomClient()` for client with specified id.

This makes it easy to integrate authentication to the streamer, just create a new client when user connects to your application and return the unifrost streamer `client_id` (custom or autogenerated) with your API auth workflow. If you don't care about authentication, you can also generate a new client automatically everytime a new client connects without the `id` parameter use the following middleware with the streamer.

```
mux.HandleFunc("/events", func(w http.ResponseWriter, r \*http.Request) { // Auto generate new clientID, when new client connects. (Not recommended) q := r.URL.Query() if q.Get("id") == "" { client, \_ := streamer.NewClient(ctx) q.Set("id", client.ID) r.URL.RawQuery = q.Encode() } streamer.ServeHTTP(w, r) })
```

When a client gets disconnected it has a time window to connect to the server again with the state unchanged. If client ttl is not specified in the streamer config then default ttl is set to one.

To know more, check out the [example](https://github.com/unifrost/unifrost/blob/master/examples/nats_example)

[](https://github.com/unifrost/unifrost#why-server-sent-events-sse-)Why Server Sent Events (SSE) ?
--------------------------------------------------------------------------------------------------

Why would you choose SSE over WebSockets?

One reason SSEs have been kept in the shadow is because later APIs like WebSockets provide a richer protocol to perform bi-directional, full-duplex communication. However, in some scenarios data doesn't need to be sent from the client. You simply need updates from some server action. A few examples would be friends' status updates, stock tickers, news feeds, or other automated data push mechanisms (e.g. updating a client-side Web SQL Database or IndexedDB object store). If you'll need to send data to a server, Fetch API is always a friend.

SSEs are sent over traditional HTTP. That means they do not require a special protocol or server implementation to get working. WebSockets on the other hand, require full-duplex connections and new Web Socket servers to handle the protocol. In addition, Server-Sent Events have a variety of features that WebSockets lack by design such as automatic reconnection, event IDs, and the ability to send arbitrary events.

Because SSE works on top of HTTP, HTTP protocol improvements can also benefit SSE. For example, the in-development HTTP/3 protocol, built on top of QUIC, could offer additional performance improvements in the presence of packet loss due to lack of head-of-line blocking.

[](https://github.com/unifrost/unifrost#community)Community:
------------------------------------------------------------

Join the #unifrost channel on [gophers](https://gophers.slack.com/messages/unifrost) Slack Workspace for questions and discussions.

[](https://github.com/unifrost/unifrost#future-goals)Future Goals:
------------------------------------------------------------------

*   Standalone server that can be configured by yaml, while also staying modular.
*   Making it horizontally scalabe using [raft](https://raft.github.io/) consensus algorithm.
*   Creating a website for documentation & overview, and some examples.
*   Become a [CNCF](https://cncf.io) project (...maybe).

[](https://github.com/unifrost/unifrost#users)Users
---------------------------------------------------

If you are using unifrost in production please let me know by sending an [email](mailto:rajveer0malviya@gmail.com) or file an issue.

[](https://github.com/unifrost/unifrost#show-some-love)Show some love
---------------------------------------------------------------------

The best way to show some love towards the project, is to contribute and file issues.

If you **love** unifrost, you can support by sharing the project on Twitter.

You can also support by sponsoring the project via [PayPal](https://paypal.me/rajveermalviya).

[](https://github.com/unifrost/unifrost#license)License
-------------------------------------------------------

[![FOSSA Status](https://camo.githubusercontent.com/58ebbf4d50a4ec27fa63cfaca37f8b5e34e49b7d/68747470733a2f2f6170702e666f7373612e696f2f6170692f70726f6a656374732f6769742532426769746875622e636f6d25324672616a766565726d616c76697961253246756e6966726f73742e7376673f747970653d6c61726765)](https://app.fossa.io/projects/git%2Bgithub.com%2Frajveermalviya%2Funifrost?ref=badge_large)

  
  
from Hacker News https://ift.tt/2ZbQWMS