---
title: 'How I write back ends'
date: 2020-01-22T04:53:00+01:00
draft: false
---

![](https://avatars3.githubusercontent.com/u/1160018?s=400&v=4 "GitHub - fpereiro/backendlore: How I write backends")  

[](https://github.com/fpereiro/backendlore#how-i-write-backends)How I write backends
====================================================================================

From late 2012 to the present I have been writing backends (server-side code) for web applications. This document summarizes many aspects of how I write these pieces of code.

I'm writing this lore down for three purposes:

1.  Share it with you.
2.  Systematize it for future reference and improvement.
3.  Learn from your feedback.

Your questions and observations are very welcome!

If you must sting, please also be nice. But above all, please be accurate.

[](https://github.com/fpereiro/backendlore#the-approach)The approach
--------------------------------------------------------------------

My approach to backends (as with code in general) is to iteratively strive for simplicity. This approach - and a share of good luck - has enabled me to write lean, solid and maintainable server code with a relatively small time investment and minimal hardware resources.

To see how this approach works in practice, you can see the code of the backend for an open source service, [ac;pic](https://github.com/altocodenl/acpic).

[](https://github.com/fpereiro/backendlore#the-core-tools)The core tools
------------------------------------------------------------------------

*   The latest [Ubuntu Long Term Support version](https://wiki.ubuntu.com/LTS) as the underlying OS. I use it both on the cloud (see [Architecture](https://github.com/fpereiro/backendlore#architecture) below) and locally.
*   The latest [Node.js Long Term Support version](https://nodejs.org/en/), although older (even much older) versions of node would suffice. The latest version is recommended because of security and performance improvements.
*   The latest version of [Redis](https://redis.io/) that is available to the package manager of the current Ubuntu.
*   The latest version of [NginX](https://www.nginx.com/) that is available to the package manager of the current Ubuntu.
*   [Amazon Web Services](https://aws.amazon.com/), in particular [S3](https://aws.amazon.com/s3/) (files), [SES](https://aws.amazon.com/ses/) (email) and optionally [EC2](https://aws.amazon.com/ec2/).

[](https://github.com/fpereiro/backendlore#architecture)Architecture
--------------------------------------------------------------------

The simplest version of the architecture is that for local development. It looks like this:

```
Architecture A ____local ubuntu box_______________________________ | | internet <----|----------------> node <------> local filesystem | (localhost) | |\ | | | --------> redis | | \ | | -----------------------------|---> AWS S3 & SES |__________________________________________________| 
```

The simplest version of the architecture on a remote environment (a server connected to the internet with a public IP address) looks like this:

```
Architecture B ____remote ubuntu box______________________________ | | internet <----|--> nginx <-----> node <------> local filesystem | | |\ | | | --------> redis ------------|--------| | \ | v | -----------------------------|---> AWS S3 & SES |__________________________________________________| 
```

nginx works as a [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy). Its main use is to provide HTTPS support - in particular, HTTPS support with nginx is extremely easy to configure with [Let's Encrypt](https://letsencrypt.org/) free, automated and open certificates. For more about HTTPS and nginx, please refer to the [HTTPS section](https://github.com/fpereiro/backendlore/HTTPS).

This architecture, which runs everything on a single Ubuntu instance (node, redis, and access to the local filesystem) can take you surprisingly far. It is definitely sufficient as a test environment. It can also serve as the production environment of a [MVP](https://en.wikipedia.org/wiki/Minimum_viable_product) or even of an application with moderate use that is not mission critical.

redis can be replaced or complemented by another NoSQL database (such as [MongoDB](https://www.mongodb.com/)) or a relational database (such as [Postgres](https://www.postgresql.org/)). Throughout this section, where you see _redis_, feel free to replace it with the database you might want to use.

Notice that there's an arrow connecting redis to AWS. This reflects the (highly recommended) possibility of periodically and automatically uploading redis dumps to AWS S3, to restore the database from a snapshot in case of an issue.

Relying on the local FS is optional, since we're also using AWS S3. For a discussion, see the [File section](https://github.com/fpereiro/backendlore/file).

The performance of this simple setup can be outstanding. I have personally witnessed virtual instances (which have significantly less power than a comparable dedicated server) with 4-8 cores and 4-8GB of RAM handling over a thousand requests per second (100M requests per day) with sub-10 millisecond latencies. Unless your application logic is CPU intensive, performance should not be a reason for changing this architecture unless you expect your load to be closer to a billion requests per day.

The two main reasons for using an architecture involving more machines are:

1.  Resilience to outages. If we only use one machine, we have a single point of failure.
2.  Too much data: > 16GB in Redis and/or > 100GB in files. Not all of that fits into one instance.

An architecture with several instances of node running is of course possible, in case loads are very high and/or latency needs to be kept to the bare minimum. In this case, nginx can be placed on its own machine and also the filesystem and redis are placed in another instance.

```
Architecture C ___api_1____ | | /----|-> node <--|----\/---> AWS S3 & SES <------- | |___________| | | | | | _load balancer_ | ___api_2____ | ___data_server___ | | | | | | | | | | internet <----|---> nginx <---|---------|-> node <--|---------|--> FS server | | |_______________| |___________| |\-> redis ------|----| |________________| 
```

Notice that we now have a data server, comprising both a database and files. This seems to reflect a pattern that has been repeated since the very beginnings of computing, where there are always two types of storage (one fast and small, another one larger and slower). redis and the FS serve as the particular incarnations of this pattern within our architecture.

In Architecture C, a further modification is necessary: instead of relying on local access to the filesystem, a node server must act as a filesystem server. It should implement routes for reading, writing, listing and deleting files. In my experience, this logic can be done in 100-200 lines, but the code must be written down carefully. If the data server is publicly accessible, redis must be secured through either a password or (better) through [spiped](https://www.tarsnap.com/spiped.html); the FS server, meanwhile, will probably have to use either a password in a header or (better) an auth system with cookies to authorize/deny access.

In either case, the FS server will also communicate with AWS S3 and will handle its contents.

It is highly recommended that redis should have a follower/slave replica on a separate server.

```
Architecture D ___api_1____ | | /----|-> node <--|----\/---> AWS S3 & SES <----- | |___________| | | | | | _load balancer_ | ___api_2____ | ___data_server_1_ | __data_server_2_ | | | | | | | | | | | internet <----|---> nginx <---|---------|-> node <--|---------|--> FS server | | | redis | |_______________| |___________| |\-> redis <-----|------|--> replica | |________________| |_______________| 
```

With n node servers, it is possible to scale horizontally, to improve performance and avoid an outage if one of the node servers is down.

This architecture, however, still has two points of failure: the load balancer and the data server. Having multiple load balancers is also possible by having multiple A records ([DNS load balancing](https://www.nginx.com/resources/glossary/dns-load-balancing/)) or by using [AWS ELB](https://aws.amazon.com/elasticloadbalancing/).

This leaves the problem of scaling the data server. The FS can be split among several servers, although this undertaking is nontrivial; in any case, if you have very large amounts of data, you can rely mostly on AWS S3 and use a FS server as a mere cache.

The truly difficult thing to scale (and where you should be very careful with vendor statements) is the scaling of the database. Scaling a database allows for 1) partitioning the data into sizes that will fit a single server, no matter how much data you have; 2) depending on what type of partitioning/sharding you use, allow for no downtime or data loss in the event of a database node failing.

Here it is essential to be aware of the [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem). When we partition a database into multiple nodes that are connected through the internet (and thus are susceptible to delays or errors in their communication), we can only choose between **consistency** and **availability**. You can either decide to respond to all requests and risk serving & storing inconsistent data, or you can choose to remain fully consistent at the price of having some downtime. This hard choice is an interesting one. Most of the solutions out there, including [redis cluster](https://redis.io/topics/cluster-spec) favor availability over consistency. Whatever solution you use, it should be one of the default ways in which your database of choice is meant to scale, unless you **really** know what you're doing.

[](https://github.com/fpereiro/backendlore#https)HTTPS
------------------------------------------------------

Providing HTTPS support with node is possible, but in my experience it is quite more cumbersome. Using nginx seems to reduce the overall complexity of the architecture & setup.

Using nginx to receive all requests also has the advantage that our node server can run as a non-root user, which prevents an exploit in node from giving access to an attacker to the OS. Without further configuration, the default ports for HTTP (80) and HTTPS (443) can only be used by the root user of the system (any port under 1024, actually); in this architecture, nginx runs as root and listens on those two ports, and forwards traffic to node, which is listening on a port higher than 1024.

_Questions for future research: having node instead of nginx running as root reduces the attack surface of the application or is it mere [cculte](https://en.wikipedia.org/wiki/Cargo_cult)? Are there concrete security advantages to not run nginx as root and which merit taking the trouble to set up port forwarding?_

To configure HTTPS with nginx: if you own a domain `DOMAIN` (could be either a domain (`mydomain.com`) or a subdomain (`app.mydomain.com`)) and its main A record is pointing to the IP of an Ubuntu server under your control, here's how you can set up HTTPS (be sure to replace occurrences of `DOMAIN` with your actual domain :):

```
sudo add-apt-repository ppa:certbot/certbot -y sudo apt-get update sudo apt-get install python-certbot-nginx -y 
```

In the file `/etc/nginx/sites-available/default`, change `server_name` to `DOMAIN`.

```
sudo service nginx reload sudo certbot --nginx -d DOMAIN 
```

Add the following line to your crontab file (through `sudo crontab -e`: `M H * * * sudo certbot renew`, where `M` is a number between 0 and 59 and `H` is a number between 0 and 23. This command ensures that every day, at the specified hour, the certificates will be updated automatically so that they don't expire.

[](https://github.com/fpereiro/backendlore#redis)Redis
------------------------------------------------------

Redis is an amazing choice for database. While it may not be the best choice for you, I highly recommend that you take a look at it, particularly if you've never used it before.

Redis is much more than a key-value store: it is a server that implements data structures in memory. In practice, this means that you have access to fundamental constructs like lists, hashes, sets. These data structures are implemented with amazing quality, consistency and performance.

As stated above in the Architecture section, it is highly recommended that [RDB persistence](https://redis.io/topics/persistence) (and possibly AOF) should be turned on. I highly recommend backing up redis dumps into AWS S3, instead of just locally - this can be done by the node instance itself.

I recommend writing down in the readme the key structure used by your application in redis. Here's [an example](https://github.com/altocodenl/acpic#redis-structure).

I don't like the redis cluster (partitioning/sharding) model; for me, scaling redis to multiple nodes while maintaining consistency and understandability of the overall structure is an open problem.

[](https://github.com/fpereiro/backendlore#file)File
----------------------------------------------------

Using AWS S3 is highly recommended. It is a highly secure, redundant and cheap way to store files. To use S3 from node, I recommend using the official SDK (`aws-sdk`). Here's an example initialization.

```
var s3 \= new (require ('aws-sdk')).S3 ({ apiVersion: '2006-03-01', sslEnabled: true, credentials: {accessKeyId: ..., secretAccessKey: ...}, params: {Bucket: ...} });
```

The main methods I use are `s3.upload`, `s3.getObject`, `s3.headObject`, `s3.deleteObjects` and `s3.listObjects`. It's possible to write a ~60 line code layer that provides consistent access to these methods and which can be used by the rest of the server.

I usually also use the local FS to serve files, relying on S3 only for recovery in case there's a server or disk issue. There are two main reasons for this:

1.  Cost - if your application potentially serves a lot of data, S3 cost can be very significant; downloading a GB once currently costs 3-4x the cost of storing it for an entire month. What makes this worse is that it is hard to predict how much data you may use on a given month, so you have an unlimited financial downside. An ideal service would not charge for downloads, just for storage.
2.  Speed - S3 is not very fast, even accounting for network delays. Latencies of 20-50ms are par for the course, compared for sub 5ms for a local FS.

By serving the files from your own servers, you have much better speed and your cost is low and predictable.

The downside of using the local FS is that it requires extra code and management of the files themselves. It also requires a FS server in an architecture with multiple node instances; and it requires multiple servers with partitioning logic if the data is too large to fit in a single FS server.

Whether you go with using the local FS, a single FS server or a full-fledged scalable FS server, the idea is to use S3 as the ultimate storage of the file and its guarantee of durability. When deleting files, it is recommended to delete them from S3 by moving them to a separate bucket that has a 30-day deletion lifecycle, so they are automatically deleted later; this may help in case there are unwanted deletions. This is also a good pattern in case an object is overwritten.

[](https://github.com/fpereiro/backendlore#node)Node
----------------------------------------------------

The application logic lives in node. Node serves all incoming requests through an HTTP API.

An HTTP API allows us to serve, with the same code, the needs of a user facing UI (either web or native), an admin and also programmatic access by third parties. We get all three for the price of one.

The data transmitted between client and server is of two types:

*   Files: HTTP, images. Clients can also upload files through requests of type `multipart/form-data`.
*   JSON data. This is the preferred format for most interactions.

[](https://github.com/fpereiro/backendlore#one-server-one-service)One server, one service
-----------------------------------------------------------------------------------------

In my experience, a non-trivial application which contains its own application logic plus a set of functions for interacting with FS, S3, redis and its own auth logic can be written in 2000-3000 lines of code. In my eyes, this warrants to keep the server as a single centralized concern. 2-3k of code can hardly be called a monolith.

Before you rush to embrace the microservices paradigm, I offer you the following rule of thumb: if two pieces of information are dependent on each other, they should belong to a single server. In other words, the natural boundaries for a service should be the natural boundaries of its data.

[](https://github.com/fpereiro/backendlore#server-library)Server library
------------------------------------------------------------------------

In projects where I own and maintain the code, I prefer [??i??ek](http://github.com/fpereiro/cicek) - although the library is begging for a rewrite. In other cases, I use [express](https://expressjs.com/) with the addons [body-parser](https://www.npmjs.com/package/body-parser), [busboy-body-parser](https://www.npmjs.com/package/busboy-body-parser) and [cookie-parser](https://www.npmjs.com/package/cookie-parser).

[](https://github.com/fpereiro/backendlore#environment-variables--configuration)Environment variables & configuration
---------------------------------------------------------------------------------------------------------------------

I only use a single environment variable, to specify the name of the environment. Typical options are `dev` and `prod`. When no environment is provided, I default to `dev`. The environment can be passed as an argument when running the server: `node server ENV` and then retrieved from the server code as follows: `var ENV = process.argv [2];`.

I store the configuration for the server on a js file, usually named `config.js`. In case the server is open source code, I create a separate file `secret.js` to store credentials and secrets. Both of these files will be referred to henceforth as `config`.

In case that `secret.js` is present, be sure to add it to your `.gitignore` file!

Typical things that go in `config`:

*   Port where node listens.
*   Name of the cookie where the session is stored.
*   Redis configuration.
*   Cookie secret (for signing cookies).
*   AWS credentials.
*   Whitelisted users/admins.

The config is simply required as `var CONFIG = require ('./config.js');`.

To specify configuration items per environment, rather than have separate objects, it's better to split only those properties that change from environment to environment. For example:

```
var ENV \= process.argv \[2\]; module.exports \= { port: 1111, bucket: ENV \=== 'prod' ? 'prodbucket' : 'devbucket' }
```

[](https://github.com/fpereiro/backendlore#notification)Notification
--------------------------------------------------------------------

I find it useful to have a single function, `notify`, to report errors or warnings. This function acts as a funnel through which pass all the events that may concern us. This function can then do a variety of things, like printing to a log, sending an email, or sending the data to a remote logging service.

I suggest invoking the notify function in the following cases:

*   Master process fails.
*   Worker process fails.
*   Server starts.
*   Client transmission errors.
*   Client is replied with an error code (>= 400).

[](https://github.com/fpereiro/backendlore#code-structure)Code structure
------------------------------------------------------------------------

*   `admin.js`: admin client, optional.
*   `client.js`: user UI.
*   `config.js` & `secret.js`: configuration.
*   `deploy.sh`, script for deploying the app.
*   `mongroup.conf`, for keeping the app running.
*   `package.json`, dependency list.
*   `provision.sh`, for creating new instances.
*   `package.json`, dependency list.
*   `server.js`, with all server code.
*   `test.js`, the test suite.

[](https://github.com/fpereiro/backendlore#documentation)Documentation
----------------------------------------------------------------------

Contained in a single markdown file, `readme.md`. Usually contain the following:

*   Purpose of the project and general description.
*   Todo list.
*   Routes, including description of behavior and payloads.
*   DB structure.
*   FS structure, if any.
*   Further configuration instructions, if any.
*   License.

[](https://github.com/fpereiro/backendlore#provisioning)Provisioning
--------------------------------------------------------------------

When provisioning a new server, upgrade all the packages first.

```
ssh $HOST apt-get update ssh $HOST DEBIAN_FRONTEND=noninteractive apt-get upgrade -y --with-new-pkgs 
```

I recommend installing `fail2ban`, which will rate-limit IPs that perform invalid SSH logins:

```
ssh $HOST apt-get install fail2ban -y 
```

To provision a node server, we merely need to install node plus [mon](https://github.com/tj/mon) and [mongroup](https://www.npmjs.com/package/mongroup).

```
# install node ssh $HOST "curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -" ssh $HOST apt-get install nodejs -y # install mon & mongroup ssh $HOST apt-get install build-essential -y ssh $HOST '(mkdir /tmp/mon && cd /tmp/mon && curl -L# https://github.com/tj/mon/archive/master.tar.gz | tar zx --strip 1 && make install && rm -rf /tmp/mon)' ssh $HOST npm install -g mongroup 
```

To use mongroup to keep the server running, you need a file `mongroup.conf` which can look like this:

```
logs \= /tmp/MYAPP/logs pids \= /tmp/MYAPP/pids node server ENV
```

where `ENV` is `dev` or `prod`.

You can place most of these commands on a single `provision.sh` file, or create different files for provisioning different machines. To me, the important thing is to have a set and unambiguous set of commands that will run successfully and which represent the entire configuration needed in the instance. There should be no unspecified or unwritten steps for provisioning an instance.

As long as you fully control the remote instances/servers, I don't see a need for running the application within [Docker](https://www.docker.com/) or any other sort of virtualization. Since the full environment is replicable (starting with a given OS, you run a certain number of commands to reach a provisioned instance), there's no idempotence benefit to virtualization. And by running the service on the host itself, everything else is simpler. I can only recommend virtualization if you're deploying to environments you don't fully control.

[](https://github.com/fpereiro/backendlore#deploying-the-server)Deploying the server
------------------------------------------------------------------------------------

I normally deploy through a bash script that performs the following:

*   Determines the IP depending on the environment.
*   Asks for an extra parameter "confirm" if deploying to `prod`.
*   Compresses the entire repo folder, ignoring the `node_modules` folder and `.swp` temporary files generated by Vim (my text editor).
*   Copies the compressed folder to the target server.
*   Uncompresses the folder.
*   Adds the environment to `mongroup.conf`.
*   Runs `npm i --no-save` to install/update the dependencies.
*   Restarts the server through the command `mg restart`.
*   Deletes the compressed folder from the server and my local computer.

To run the server locally, after installing the dependencies with `npm i --no-save`, you can merely run `node server`.

I eschew automatic code deployment triggered by a commit to a certain repository branch because:

1.  Deploying manually with a script takes only a few seconds.
2.  I like to see if the deployment is indeed successful at that very moment, instead of finding out through an email later.
3.  Committing and deploying can reasonably be considered separate processes.

[](https://github.com/fpereiro/backendlore#identity--security)Identity & security
---------------------------------------------------------------------------------

Identity is managed by the server itself, without reliance on external services. User data is stored in the database.

It is absolutely critical to hash user passwords. I recommend using [bcryptjs](https://www.npmjs.com/package/cookie-parser).

Side note: wherever possible, I use pure js modules and avoid those that have C++ bindings. The latter sometimes require native packages to be installed and in my experience tend to be more fickle. js code only needs the runtime and its dependencies to run, and no compilation.

Cookies are used to identify a session. The session itself is a quantity that is cryptographically hard to guess. The cookie name is predetermined in the configuration (for example, `myappname`); its value is the session itself. The session doesn't contain any user information - this is stored in the database.

Currently, the cookie is accessible by client-side javascript; the main use case for this is to send it back as an extra field in POST requests (be them JSON or `multipart/form-data`) as [CSRF prevention](https://en.wikipedia.org/wiki/Cross-site_request_forgery). This pattern is called [double submit cookie pattern](https://medium.com/cross-site-request-forgery-csrf/double-submit-cookie-pattern-65bb71d80d9f).

Lately, however, I have decided to change the cookie to be httponly (which means that cannot be seen by client-side js) and provide the client with a separate CSRF token. The main reason for this is that if the app is ever victim of [XSS](https://es.wikipedia.org/wiki/Cross-site_scripting) through malicious user content that I've failed to filter, users will be fully vulnerable. I'd rather have an extra layer of security to protect my users at the cost of more code and a somewhat higher complexity. _Future work: I haven't implemented yet this change since I'm still finding an elegant way to generate, use and clean up CSRF tokens._

Cookies are also signed. The session within the cookie should not be easily guessable, so signing it doesn't make it harder to guess. The reason for signing them, however, is that this allows us to distinguish a cookie that was valid but has now expired from an invalid cookie. In other words, we can distinguish an expired session from an attack without having to keep all expired sessions in the database.

_Future work: it might be interesting to see if signing cookies with salts (random quantities) per user (instead of using a global salt) would increase security. The only extra cost would be to store an extra quantity per user in the database._

[](https://github.com/fpereiro/backendlore#routes)Routes
--------------------------------------------------------

Both in ??i??ek and express, routes are executed in the order in which they are defined. A request might be matched by one or more routes, executed in order. Any route has the power to either "pass" the request to the next matching route, or instead to reply to that request from itself. It can't, however, do both.

A few routes are executed for every incoming request. They exist in the following order.

*   Avant route: happens at the beginning creates a `log` object into the `response`, including a timestamp, for profiling and debugging purposes.
*   Public routes (those not requiring to be logged in).
*   Auth routes.
*   Gatekeeper route: this route checks for the presence of a session in the cookie; if no cookie is present, the request is replied with a 403 code and possibly `notify` us. If the session is invalid, checking for its signature can either determine an expired session or a malicious attempt. If the session is valid, the associated user data is retrieved from the database and placed within the request object; in this case, this route invokes `response.next` to pass the request to the following route.
*   CSRF route: checks for the CSRF token in the body of every `POST` request.
*   Private routes (those requiring to be logged in).
*   Admin gatekeeper route: any request looking to match a route after this one must be an admin, otherwise a 403 is returned.
*   Admin routes.

The following are the typical auth routes:

*   `POST /auth/signup`
*   `POST /auth/login`
*   `POST /auth/logout`
*   `POST /auth/destroy` (eliminates the account)
*   `POST /auth/verifyEmail`. This route is optional. This route requires sending emails.
*   `POST /auth/recover`. This route requires sending emails.
*   `POST /auth/reset`.
*   `POST /auth/changePassword`. This route possibly requires sending emails (to notify the user).

[](https://github.com/fpereiro/backendlore#whitelisting-of-users)Whitelisting of users
--------------------------------------------------------------------------------------

For systems with few and predefined users, its easiest to put a list of valid email addresses in `CONFIG`, then when the signup logic is triggered, the system only allows the whitelisted addresses to create an account. This pattern allows for reusing the code of a more normal application with open sign in, without backdoors and without having to create the user accounts with a seed script.

[](https://github.com/fpereiro/backendlore#admin-users)Admin users
------------------------------------------------------------------

They can be implemented in two ways: either by setting a flag in the database manually (or through admin routes to this effect), or through reading a list of admin users from `config`. In any case, admin users still use sessions as normal users.

[](https://github.com/fpereiro/backendlore#master-node)Master node
------------------------------------------------------------------

The master node uses [cluster](https://nodejs.org/api/cluster.html) to fork one child process. It is recommended to fork one process per CPU - you can get the number of CPUs with this command `require ('os').cpus ().length`. By doing this, you'll have n nodes serving requests, one per CPU.

In case a worker node fails, it is recommended to use the `uncaughtException` handler to `notify` the error, like this:

```
if (! cluster.isMaster) return process.on ('uncaughtException', function (error) { notify (error); });
```

[](https://github.com/fpereiro/backendlore#master-tasks)Master tasks
--------------------------------------------------------------------

A few tasks, besides the API, can be done by the master process. These include:

*   Uploading redis dumps to S3 periodically.
*   `notify` if CPU or RAM usage is dangerously high.
*   Perform DB consistency/cleanup checks, particularly in `dev`.

I usually write these functions at the end of the `server.js` file, after the routes.

[](https://github.com/fpereiro/backendlore#reply-function)Reply function
------------------------------------------------------------------------

To keep the code fluid and short, whenever I'm replying to a request with JSON data, I use a `reply` function (which comes already defined in ??i??ek - if I'm using express, I define it at the top of `server.js`) of the form `reply (response, CODE, body, [headers])`.

[](https://github.com/fpereiro/backendlore#validation--auto-activation)Validation & auto-activation
---------------------------------------------------------------------------------------------------

I consider it indispensable that every route that receives data should do perform a deep validation of it. If a payload breaks a server, whether inadvertently or maliciously, it is the server's fault. This is embodied in the concept of [auto-activation](https://github.com/fpereiro/teishi#auto-activation).

For performing validations, I use a combination of [teishi](https://github.com/fpereiro/teishi) and custom code. Checks are usually done first synchronously, and then sometimes asynchronously against data stored in the database (which necessarily has to be reached asynchronously).

A global type of validation that happens before the actual routes (as middleware) is to check that requests with a `application/json` `content-type` header contain a body that is valid JSON.

[](https://github.com/fpereiro/backendlore#payload-style)Payload style
----------------------------------------------------------------------

I usually just use `GET` and `POST` methods when interchanging JSON. Often, `PUT` and `PATCH` can be dealt with almost the same code as `POST`.

When retrieving data (`GET`), the query (request payload) cannot be larger than 2048 characters. In cases where this is not enough, I send the queries through `POST`. Since `POST` requests can be cached with the right response headers, this entails no performance issue.

With apologies to the Church of [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)!

[](https://github.com/fpereiro/backendlore#caching)Caching
----------------------------------------------------------

I use [ETags](https://en.wikipedia.org/wiki/HTTP_ETag); to compute this cache header, I use the actual response body if it is JSON; and the modification time and file size in the case of a static file. Avoiding dates in caching has made my code and debugging much much simpler.

[](https://github.com/fpereiro/backendlore#testing)Testing
----------------------------------------------------------

Since we're writing HTTP APIs, it makes sense to test them through HTTP requests. I use [hitit](https://github.com/fpereiro/hitit), which is a tool that triggers HTTP requests.

My style of testing is end to end - the API is test from the outside only. Any internals are tested through the outcomes that they provide to the routes that use them. If an internal is convoluted enough, it should be moved to its own module and have its own tests, but so far I haven't seen the need for this - code seems to become either an application or a [separate tool](https://github.com/fpereiro/ustack).

Whenever a test fails, the entire suite fails. No errors or warnings are tolerated. The test suite either passes or it does not.

The tests use no backdoors and are indistinguishable from client requests. The only allowance I make for them in server code is to not send emails when the environment is local.

I further simplify things by not specifying a test database, and only running the tests locally. Since my development environment is very similar to the environment where the code runs, this seems to work well.

The tests should clean up after themselves using requests - i.e., by deleting the test user just created through a proper route.

Another advantage of testing through HTTP is that the test payloads can work as a complementary documentation of the payloads sent and received by the server for each route.

I recommend not using random quantities when sending payloads, to make the tests replicable.

If you want to break a given route, it is possible to write a function that given a schema, will generate invalid payloads. This is a sort of brute-force way of testing the validation of your route. Here's [an example](https://github.com/altocodenl/acpic/blob/67d5408d6df555ed9f92cbbedf79ffd929a75d1e/test.js#L26).

Tests are run manually: `node test`, while the server is already running.

[](https://github.com/fpereiro/backendlore#development-cycle)Development cycle
------------------------------------------------------------------------------

First, I write the server routes.

Then, I write the tests.

For each route, first I try to break it. When I can't break it, I send different payloads that should cover all the main cases.

Once the tests are passing, the backend is ready. Time to write the client; and any bugs you'll find will very likely be in the client, since the server is debugged. In this way, errors don't have to be chased on both sides of the wire.

[](https://github.com/fpereiro/backendlore#future-directions)Future directions
------------------------------------------------------------------------------

I have recently decided to take some common parts of applications that I've been building and provide them as services in the future. This should have the following advantages:

1.  Reduce code size by ~500 lines and tests by ~250 lines.
2.  Allow for unlimited scaling.
3.  Provide an unified admin to see different aspects of the application.

The services I plan to extract are:

*   Identity: store identities and cookies; server code should only consist of calling these functions within the routes, plus sending emails on a couple of routes. Rate limiting can also be piggybacked here.
*   Files: as a service, backed by S3, served from fast, node-powered servers. Will also allow for tailing and filtering files for fast querying.
*   Redis: redis will be accessible as a service through HTTP, backed by a consistent, configurable and incremental partitioning model.
*   Logging: `notify` will send data to an unified service. Will allow for sending emails in certain situations.
*   Beat: track CPU and RAM usage in a dashboard. Will allow for sending emails in certain situations.
*   Stats: unified statistics for measuring different things.

Once these are matured, they will be [rolled out publicly](https://github.com/altocodenl/actools). But the road ahead is long indeed!

[](https://github.com/fpereiro/backendlore#license)License
----------------------------------------------------------

This document is written by Federico Pereiro ([fpereiro@gmail.com](mailto:fpereiro@gmail.com)) and released into the public domain.

  
  
from Hacker News https://ift.tt/2tFCYqZ