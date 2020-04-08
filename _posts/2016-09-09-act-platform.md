---
title: 'ACT Platform'
date: 2019-10-01T15:50:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-JPkii6RP-xQ/XXz0xwwnYNI/AAAAAAAAQUk/D_n3XzSrhfc9HW4elKRgcLmplF-BwPLSQCNcBGAsYHQ/s640/brain-cyber.jpg)](https://1.bp.blogspot.com/-JPkii6RP-xQ/XXz0xwwnYNI/AAAAAAAAQUk/D_n3XzSrhfc9HW4elKRgcLmplF-BwPLSQCNcBGAsYHQ/s1600/brain-cyber.jpg)

**ACT Platform - Open Platform For Collection And Exchange Of Threat Intelligence Information**

  

[_Semi-Automated Cyber Threat Intelligence_](https://www.mnemonic.no/research-and-development/semi-automated-cyber-threat-intelligence/ "Open platform for collection and exchange of threat intelligence information (2)") (ACT) is a research project led by mnemonic as with contributions from the University of Oslo, NTNU, Norwegian Security Authority (NSM), KraftCERT and Nordic Financial CERT.  
The main objective of the ACT project is to develop a platform for cyber [threat intelligence](https://www.kitploit.com/search/label/Threat%20Intelligence "threat intelligence") to uncover cyber attacks, cyber espionage and sabotage. The project will result in new methods for data enrichment and data analysis to enable identification of threat agents, their motives, resources and attack methodologies. In addition, the project will develop new methods, work processes and mechanisms for creating and distributing threat [intelligence](https://www.kitploit.com/search/label/Intelligence "intelligence") and countermeasures to stop ongoing and prevent future attacks.  
In this repository the code of the ACT platform is published under an Open Source license.  
[](https://www.blogger.com/u/1/null)

  

  
**Usage**  
The ACT platform exposes a set of REST APIs. See this [guideline](https://github.com/mnemonic-no/act-platform/wiki/REST-API-Usage-Guideline "guideline") on how to work with the API.  
  
**Installation**  
  
**Prerequisites**  

*   Java 8 for running the application.
*   Maven for managing dependencies, building the code, running the unit tests, etc.
*   An installation of [Apache Cassandra](https://cassandra.apache.org/ "Apache Cassandra") for storage. Any version of Apache [Cassandra](https://www.kitploit.com/search/label/Cassandra "Cassandra") 3.x is support.
    *   Import the Cassandra database schema from `deployment-service/resources/cassandra.cql`.
*   An installation of [Elasticsearch](https://www.elastic.co/products/elasticsearch "Elasticsearch") for indexing. Version 6.8 of [Elasticsearch](https://www.kitploit.com/search/label/Elasticsearch "Elasticsearch") is required.
*   (Optional) An installation of [ActiveMQ](https://activemq.apache.org/ "ActiveMQ") for the multi-node environment.
*   (Optional) An installation of [Docker](https://www.docker.com/ "Docker") for running the integration tests.

  
**Compilation**  

*   Execute `mvn clean install -DskipTests` from the repository's root folder to compile the code.
*   Afterwards follow the [deployment guide](https://github.com/mnemonic-no/act-platform/wiki/Architecture-and-Deployment-Guide "deployment guide") to run the application.

  
**Testing**  

*   Download a Cassandra image by `docker pull cassandra`.
*   Download an Elasticsearch image by `docker pull [docker.elastic.co/elasticsearch/elasticsearch:6.8.2](http://docker.elastic.co/elasticsearch/elasticsearch:6.8.2)`.
*   Download an ActiveMQ image by `docker pull webcenter/activemq`.
*   Execute `mvn clean install` for running all tests including integration tests.
*   Execute `mvn clean install -DskipSlowTests` for skipping the integration tests.
*   By default the integration tests will try to connect to Docker on localhost and port 2375. Set the $DOCKER\_HOST environment variable to override this behaviour.

  
  

**[Download Act-Platform](http://eunsetee.com/DQ01 "Download Act-Platform")**

**Regards**

**Kang Asu**