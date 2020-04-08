---
title: 'Decentralized VPN Written in Go'
date: 2019-11-13T02:23:00+01:00
draft: false
---

[](https://github.com/mehrdadrad/radvpn#decentralized-vpn)Decentralized VPN
---------------------------------------------------------------------------

[![Build Status](https://camo.githubusercontent.com/206f7437dfb2543bc2b00c3b7bd6cb7491c1325c/68747470733a2f2f7472617669732d63692e6f72672f6d6568726461647261642f72616476706e2e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/mehrdadrad/radvpn) [![Go Report Card](https://camo.githubusercontent.com/5fc2ce9e5db7e94deea5198d8a468c29803f0c58/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f6d6568726461647261642f72616476706e)](https://goreportcard.com/report/github.com/mehrdadrad/radvpn) [![GoDoc](https://camo.githubusercontent.com/ad89bbd12888fba443b50c0a9341293617c21b95/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f6d6568726461647261642f72616476706e3f7374617475732e737667)](https://godoc.org/github.com/mehrdadrad/radvpn)

[![Alt text](https://github.com/mehrdadrad/radvpn/raw/master/docs/imgs/radvpn.png?raw=true "radvpn")](https://github.com/mehrdadrad/radvpn/blob/master/docs/imgs/radvpn.png?raw=true)

[](https://github.com/mehrdadrad/radvpn#build)Build
---------------------------------------------------

Given that the Go Language compiler (version 1.11 or greater is required) is installed, you can build it with:

```
go get https://github.com/mehrdadrad/radvpn cd $GOPATH/src/github.com/mehrdadrad/radvpn go build . 
```

[](https://github.com/mehrdadrad/radvpn#docker)Docker
-----------------------------------------------------

```
docker run --privileged -d -p 8085:8085 -v $(pwd)/radvpn.yaml:/etc/radvpn.yaml -e RADVPN_NODE_NAME=node1 radvp 
```

[](https://github.com/mehrdadrad/radvpn#basic-config)Basic Config
-----------------------------------------------------------------

With the default it tries to load config.yaml file indivitually at each node but can be configured to use same configuration through [etcd](https://github.com/etcd-io/etcd). once the configuration changed, it loads and applies new changes by itself. the below yaml is a simple configuration.

[![Alt text](https://github.com/mehrdadrad/radvpn/raw/master/docs/imgs/simpleconfig.png?raw=true "radvpn")](https://github.com/mehrdadrad/radvpn/blob/master/docs/imgs/simpleconfig.png?raw=true)

```
revision: 1 crypto: type: gcm key: 6368616e676520746869732070617373776f726420746f206120736563726574 nodes: - node: name: node1 address: 8.121.55.10 privateAddresses: - 10.0.1.1/24 privateSubnets: - 10.0.1.0/24 - node: name: node2 address: 84.12.92.45 privateAddresses: - 10.0.2.1/24 privateSubnets: - 10.0.2.0/24 
```

### [](https://github.com/mehrdadrad/radvpn#run)Run

```
#radvpn -config radvpn.conf 
```

### [](https://github.com/mehrdadrad/radvpn#configuration-keys)Configuration keys

*   revision - the watcher works based on the revision number once it increased, the configuration will be loaded immediatly
*   server
    *   keepalive - frequency duration of radvpn-to-radvpn ping to check if a connection is alive (default is 10 seconds)
    *   insecure - disable /enable encryption (default is false)
    *   mtu - sets the mtu of the tunnel interface
    *   maxworkers - sets number of concurrent workers (read/write to/from tunnel concurrently)
    *   address - sets ip address and ports (format : ip:port)
    *   name - sets the name of the current node
*   crypto
    *   type
        *   gcm - galois/counter mode
        *   cbc - cipher block chaining
    *   key - secret key
*   etcd
    *   endpoints - sets the etcd endpoints
    *   timeout - sets etcd endpoints timeout
*   nodes
    *   node
        *   name - node's name
        *   address - node's external ip address
        *   privateAddresses - sets private address(es) on the tunnel interface
        *   privateSubnets - sets reachable subnet(s) from currect node

### [](https://github.com/mehrdadrad/radvpn#configuration-with-etcd)Configuration with [etcd](https://github.com/etcd-io/etcd)

[![Alt text](https://github.com/mehrdadrad/radvpn/raw/master/docs/imgs/radvpnetcd.png?raw=true "radvpn etcd")](https://github.com/mehrdadrad/radvpn/blob/master/docs/imgs/radvpnetcd.png?raw=true)

[sample configuration](https://github.com/mehrdadrad/radvpn/blob/master/radvpn.yaml)

#### [](https://github.com/mehrdadrad/radvpn#run-with-etcd)Run with etcd

```
#radvpn -config radvpn.conf -etcd 
```

#### [](https://github.com/mehrdadrad/radvpn#update-etcd-from-yaml-file)Update etcd from yaml file

```
#radvpn -update etcd -config radvpn.yaml 
```

[](https://github.com/mehrdadrad/radvpn#license)License
-------------------------------------------------------

This project is licensed under MIT license. Please read the LICENSE file.

[](https://github.com/mehrdadrad/radvpn#contribute)Contribute
-------------------------------------------------------------

Welcomes any kind of contribution, please follow the next steps:

*   Fork the project on github.com.
*   Create a new branch.
*   Commit changes to the new branch.
*   Send a pull request.

  
  
from Hacker News https://github.com/mehrdadrad/radvpn