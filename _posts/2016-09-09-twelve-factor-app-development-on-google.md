---
title: 'Twelve-factor app development on Google Cloud'
date: 2019-11-01T03:22:00+01:00
draft: false
---

This document describes the popular [twelve-factor app methodology](https://12factor.net/) and how to apply it when you develop apps that run on Google Cloud Platform (GCP). If you use this methodology, you can make scalable and resilient apps that can be continuously deployed with maximum agility.

This document is intended for developers who are familiar with GCP, version control, continuous integration, and container technology.

Introduction
------------

Developers are moving apps to the cloud, and in doing so, they become more experienced at designing and deploying cloud-native apps. From that experience, a set of best practices, commonly known as the _twelve factors_, has emerged. Designing an app with these factors in mind lets you deploy apps to the cloud that are more portable and resilient when compared to apps deployed to on-premises environments where it takes longer to provision new resources.

However, designing modern, cloud-native apps requires a change in how you think about software engineering, configuration, and deployment, when compared to designing apps for on-premises environments. This document helps you understand how to apply the twelve factors to your app design.

Advantages of twelve-factor apps
--------------------------------

Twelve-factor design also helps you decouple components of the app, so that each component can be replaced easily, or scaled up or down seamlessly. Because the factors are independent of any programming language or software stack, twelve-factor design can be applied to a wide variety of apps.

The twelve factors
------------------

### 1\. Codebase

You should track code for your app in a version control system such as Git or Mercurial. You work on the app by checking out the code to your local development environment. Storing the code in a version control system enables your team to work together by providing an audit trail of changes to the code, a systematic way of resolving merge conflicts, and the ability to roll back the code to a previous version. It also provides a place from which to do continuous integration (CI) and continuous deployment (CD).

While developers might be working on different versions of the code in their development environments, at any given time the source of truth is the code in the version control system. The code in the repository is what gets built, tested, and deployed, and the number of repositories is independent of the number of environments. The code in the repository is used to produce a single build, which is combined with environment-specific configuration to produce an immutable release—a release where no changes can be made, including to the configuration—that can then be deployed to an environment. (Any changes required for the release should result in a new release.)

[Cloud Source Repositories](https://cloud.google.com/source-repositories/) enables you to collaborate and manage your code in a fully featured, scalable, private Git repository. It comes with code-search functionality across all repositories. You can also connect to other GCP products such as [Cloud Build](https://cloud.google.com/cloud-build/), [App Engine](https://cloud.google.com/appengine/), [Stackdriver](https://cloud.google.com/stackdriver/), and [Cloud Pub/Sub](https://cloud.google.com/pubsub/).

### 2\. Dependencies

There are two considerations when it comes to dependencies for twelve-factor apps: dependency declaration and dependency isolation.

Twelve-factor apps should never have implicit dependencies. You should declare any dependencies explicitly and check these dependencies into version control. This enables you to get started with the code quickly in a repeatable way and makes it easy to track changes to dependencies. Many programming languages offer a way to explicitly declare dependencies, such as pip for Python and Bundler for Ruby.

You should also isolate an app and its dependencies by packaging them into a container. Containers allow you to isolate an app and its dependencies from its environment and ensure that the app works uniformly despite any differences between development and staging environments.

[Container Registry](https://cloud.google.com/container-registry/) is a single place for your team to manage container images and perform vulnerability analysis. It also lets you decide who can access what, using fine-grained access control to the container images. Because Container Registry uses a Cloud Storage bucket as the backend for serving container images, you can control who has access to your Container Registry images by adjusting permissions for this Cloud Storage bucket.

Existing CI/CD integrations also let you set up fully automated pipelines to get fast feedback. You can push images to their registry, and then pull images using an HTTP endpoint from any machine, whether it's a Compute Engine instance or your own hardware. [Container Analysis](https://cloud.google.com/container-registry/docs/get-image-vulnerabilities) can then provide vulnerability information for the images in Container Registry.

### 3\. Configuration

Every modern app requires some form of configuration. You usually have different configurations for each environment, such as development, test, and production. These configurations usually include service account credentials and resource handles to backing services such as databases.

The configurations for each environment should be external to the code and should not be checked into version control. Everyone works on only one version of the code, but you have multiple configurations. The deployment environment determines which configuration to use. This enables one version of the binary to be deployed to each environment, where the only difference is the runtime configuration. An easy way to check whether the configuration has been externalized correctly is to see if the code can be made public without revealing any credentials.

One way of externalizing configuration is to create configuration files. However, configuration files are usually specific to a language or development framework.

A better approach is to store configuration in environment variables. These are easy to change for each environment at runtime, are not likely to be checked into version control, and are independent of programming language and development framework. In Google Kubernetes Engine (GKE), you can use [ConfigMaps](https://cloud.google.com/kubernetes-engine/docs/concepts/configmap). This lets you bind environment variables, port numbers, configuration files, command-line arguments, and other configuration artifacts to your pods' containers and system components at runtime.

### 4\. Backing services

Every service that the app consumes as part of its normal operation, such as file systems, databases, caching systems, and message queues, should be accessed as a service and externalized in the configuration. You should think of these backing services as abstractions for the underlying resource. For example, when the app writes data to storage, treating the storage as a backing service allows you to seamlessly change the underlying storage type, because it's decoupled from the app. You can then perform a change such as switching from a local PostgreSQL database to [Cloud SQL for PostgreSQL](https://cloud.google.com/sql/docs/postgres/) without changing the app code.

### 5\. Build, release, run

It's important to separate the software deployment process into three distinct stages: build, release, and run. Each stage should result in an artifact that's uniquely identifiable. Every deployment should be linked to a specific release that's a result of combining an environment's configuration with a build. This allows easy rollbacks and a visible audit trail of the history of every production deployment.

You can manually trigger the build stage, but it's usually triggered automatically when you commit code that has passed all of the required tests. The build stage takes the code, fetches the required libraries and assets, and packages these into a self-contained binary or container. The result of the build stage is a build artifact.

When the build stage is complete, the release stage combines the build artifact with the configuration of a specific environment. This produces a release. The release can be automatically deployed into the environment by a continuous deployment app. Or you can trigger the release through the same continuous deployment app.

Finally, the run stage launches the release and starts it. For example, if you're deploying to GKE, Cloud Build can call the `gke-deploy` build step to deploy to your GKE cluster. Cloud Build can manage and automate the build, release, and run stages across multiple languages and environments using build configuration files in YAML or JSON format.

### 6\. Processes

You run twelve-factor apps in the environment as one or more processes. These processes should be stateless and should not share data with each other. This allows the apps to scale up through replication of their processes. Creating stateless apps also make processes portable across the computing infrastructure.

If you're used to the concept of "sticky" sessions, this requires a change in how you think about handling and persisting data. Because processes can go away at any time, you can't rely on the contents of local storage being available, or that any subsequent request will be handled by the same process. Therefore, you must explicitly persist any data that needs to be reused in an external backing service such as a database.

If you need to persist data, you can use [Cloud Memorystore](https://cloud.google.com/memorystore/) as a backing service to cache the state for your apps, and to share common data between processes to encourage loose coupling.

### 7\. Port binding

In non-cloud environments, web apps are often written to run in app containers such as GlassFish, Apache Tomcat, and Apache HTTP Server. In contrast, twelve-factor apps don't rely on external app containers. Instead, they bundle the webserver library as a part of the app itself.

It's an architectural best practices for services to expose a port number, specified by the [`PORT`](https://cloud.google.com/run/docs/reference/container-contract#port) environment variable.

Apps that export port binding are able to consume port binding information externally (as environment variables) when using the platform-as-a-service model. In GCP, you can deploy apps on platform services such as Compute Engine, GKE, App Engine, or Cloud Run.

In these services, a routing layer routes requests from a public-facing hostname to your port-bound web processes. For example, when you deploy your apps to App Engine, you declare dependencies to add a webserver library to the app, such as Express (for Node.js), Flask and Gunicorn (for Python), or Jetty (for Java). You should not hard-code port numbers in your code. Instead, you should provide the port numbers in the environment, such as in an environment variable. This makes your apps portable when you run them on GCP.

Because Kubernetes has built-in service discovery, in Kubernetes you can abstract port bindings by mapping service ports to containers. Service discovery is accomplished using internal DNS names.

Instead of hard-coding the port that the webserver listens on, the configuration uses an environment variable. The following code snippet from an App Engine app shows how to accept a port value that's passed in an environment variable.

```
const express = require('express') const request = require('got' const app = express() app.enable('trust proxy') const PORT = process.env.PORT || 8080 app.listen(PORT, () => { console.log('App listening on port ${PORT}') console.log('Press Ctrl+C to quit.') }) 
```

### 8\. Concurrency

You should decompose your app into independent processes based on process types such as background, web, and worker processes. This enables your app to scale up and down based on individual workload requirements. Most cloud-native apps let you scale on demand. You should design the app as multiple distributed processes that are able to independently execute blocks of work and scale out by adding more processes.

The following sections describe some constructs to make it possible for apps to scale. Apps that are built with the principles of disposability and statelessness at their core are well positioned to gain from these constructs of horizontal scaling.

#### Using App Engine

You can host your apps on GCP's managed infrastructure using App Engine. [Instances](https://cloud.google.com/appengine/docs/standard/java/how-instances-are-managed) are the computing units that App Engine uses to automatically scale your app. At any given time, your app can be running on one instance or on many instances, with requests being spread across all of them.

The App Engine scheduler decides how to serve each new request. The scheduler might use an existing instance (either one that's idle or one that accepts concurrent requests), put the request in a pending request queue, or start a new instance for that request. The decision takes into account the number of available instances, how quickly your app has been serving requests (its latency), and how long it takes to start a new instance.

If you use automatic scaling, you can create a balance between performance and cost by setting target CPU utilization, target throughput, and maximum concurrent requests.

You can specify the type of scaling in the `app.yaml` file, which you upload for your service version. Based on this configuration input, the App Engine infrastructure uses dynamic or resident instances. For more information on scaling types, see the [App Engine documentation](https://cloud.google.com/appengine/docs/standard/python/how-instances-are-managed).

#### Using Compute Engine

Alternatively, you can deploy and manage your apps on Compute Engine. In that case, you can scale your app to respond to variable loads using [managed instance groups (MIG)](https://cloud.google.com/compute/docs/instance-groups/) based on CPU utilization, requests being handled, or other telemetry signals from your app.

The following figure illustrates the key features that managed instance groups provide.

![Overview of MIG capabilities and common workloads](https://cloud.google.com/solutions/images/twelve-factor-apps-mig-overview.svg)

Using [managed instance groups](https://cloud.google.com/compute/docs/instance-groups/#managed_instance_groups) lets your app scale to incoming demand and be highly available. This concept works inherently well for stateless apps such as web front-ends and for batch-based, high-performance workloads.

#### Using Cloud Functions

[Cloud Functions](https://cloud.google.com/functions/) are stateless, single-purpose functions that run on GCP, where the underlying architecture on which they run is managed for you by Google. Cloud Functions respond to event triggers such as an upload into a Cloud Storage bucket or a Cloud Pub/Sub message. Each function invocation responds to a single event or request.

Cloud Functions handles incoming requests by assigning them to instances of your function. When inbound request volume exceeds the number of existing instances, Cloud Functions might start new instances to handle requests. This automatic, fully managed scaling behavior allows Cloud Functions to handle many requests in parallel, each using a different instance of your function.

#### Using GKE autoscaling

There are some key Kubernetes constructs that apply to scaling processes:

*   [Horizontal Pod Autoscaling (HPA)](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/). Kubernetes can be configured to scale up or down the number of pods running in the cluster based on standard or custom metrics. This comes in handy when you need to respond to a variable load on your GKE cluster. The following sample HPA YAML file shows how to configure scaling for the deployment by setting up to 10 pods based on the average CPU utilization.
    
    ```
    apiVersion: autoscaling/v2beta2 kind: HorizontalPodAutoscaler metadata: name: my-sample-web-app-hpa namespace: dev spec: scaleTargetRef: apiVersion: apps/v1 kind: Deployment name: my-sample-web-app minReplicas: 1 maxReplicas: 10 metrics: - type: Resource resource: name: cpu target: type: Utilization averageUtilization: 60 
    ```
*   [Node autoscaling](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-autoscaler). In times of increased demand, you might need to scale your cluster to accommodate more pods. With GKE, you can declaratively configure your cluster to scale. With [autoscaling](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-autoscaler) enabled, GKE automatically scales nodes when additional pods need to be scheduled and when existing nodes are unable to accommodate them. GKE also scales down nodes when the load on the cluster decreases, according to the thresholds you've configured.
    
*   [Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/). GKE supports [Kubernetes jobs](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/). A job can be broadly defined as a task that needs one or more pods to run in order to execute the task. The job might run one time or on a schedule. The pods in which the job runs are disposed of when the job completes. The YAML file that configures the job specifies details on error handling, parallelism, how restarts are handled, and so on.
    

### 9\. Disposability

For apps that run on cloud infrastructure, you should treat them and the underlying infrastructure as disposable resources. Your apps should be able to handle the temporary loss of underlying infrastructure and should be able to gracefully shut down and restart.

Key tenets to consider include the following:

*   Decouple functionality such as state management and storage of transactional data using backing services. For more information, see [Backing services](https://cloud.google.com/solutions/twelve-factor-app-development-on-gcp#backing_services) earlier in this document.
*   Manage environment variables outside of the app so that they can be used at runtime.
*   Make sure that the startup time is minimal. This means that you must decide how much layering to build into images when you use virtual machines, such as public versus custom images. This decision is specific to each app and should be based on the tasks that startup scripts perform. For example, if you're downloading several packages or binaries and initializing them during startup, a sizeable portion of your start-up time will be dedicated to completing these tasks.
*   Use native features of GCP to perform infrastructure tasks. For example, you can use rolling updates in GKE and manage your security keys using Cloud Key Management Service (Cloud KMS).
*   Use the SIGTERM signal (when it's available) to initiate a clean shutdown. For example, when App Engine Flex shuts down an instance, it normally sends a STOP (SIGTERM) signal to the app container. Your app can use this signal to perform any clean-up actions before the container shuts down. (Your app does not need to respond to the SIGTERM event.) Under normal conditions, the system waits up to 30 seconds for the app to stop and then sends a KILL (SIGKILL) signal.
    
    The following snippet in an App Engine app shows you how you can intercept the SIGTERM signal to close open database connections.
    
    ```
    const express = require('express') const dbConnection = require('./db') // Other business logic related code app.listen(PORT, () => { console.log('App listening on port ${PORT}') console.log('Press Ctrl+C to quit.') }) process.on('SIGTERM', () => { console.log('App Shutting down') dbConnection.close() // Other closing of database connection }) 
    ```

### 10\. Environment parity

Enterprise apps move across different environments during their development lifecycle. Typically, these environments are development, testing and staging, and production. It's a good practice to keep these environments as similar as possible.

Environment parity is a feature that most developers consider a given. Nonetheless, as enterprises grow and their IT ecosystems evolve, environment parity becomes more difficult to maintain.

Maintaining environment parity has become easier in the last few years because developers have embraced source control, configuration management, and templated configuration files. This makes it easier to deploy an app to multiple environments consistently. As an example, using Docker and Docker Compose, you can ensure that the app stack retains its shape and instrumentation across environments.

The following table lists GCP services and tools that you can use when you design apps to run on GCP. These components serve different purposes and collectively help you build workflows that make your environments more consistent.

**GCP component**

**Purpose**

Cloud Source Repositories

A single place for your team to store, manage, and track code.

Cloud Storage, Cloud Source Repositories

Store build artifacts.

Cloud KMS

Store your cryptographic keys in one central cloud service for direct use by other cloud resources and applications.

Cloud Storage

Store custom images that you create from from source disks, images, snapshots, or images stored in Cloud Storage. You can use these images to create virtual machine (VM) instances tailored for your apps.

Container Registry

Store, manage, and secure your Docker container images.

Deployment Manager

Write flexible template and configuration files and use them to create deployments that use a variety of GCP products.

### 11\. Logs

Logs provide you with awareness of the health of your apps. It's important to decouple the collection, processing, and analysis of logs from the core logic of your apps. Decoupling logging is particularly useful when your apps require dynamic scaling and are running on public clouds, because it eliminates the overhead of managing the storage location for logs and the aggregation from distributed (and often ephemeral) VMs.

GCP offers a suite of tools that help with the collection, processing, and structured analysis of logs. It's a good practice to install the Stackdriver Logging Agent in your Compute Engine VMs. (The agent is preinstalled in App Engine and GKE VM images by default.) The agent monitors a preconfigured set of logging locations. The logs generated by your apps running in the VM are collected and streamed to Stackdriver Logging.

When logging is enabled for a GKE cluster, a logging agent is deployed on every node that's part of the cluster. The agent collects logs, enriches the logs with relevant metadata, and persists them in a data store. These logs are available for review using Stackdriver Logging. If you need more control over what's logged, you can use Fluentd daemonsets. For more information, see [Customizing Stackdriver logs for Google Kubernetes Engine with Fluentd](https://cloud.google.com/solutions/customizing-stackdriver-logs-fluentd).

### 12\. Admin processes

Administrative processes usually consist of one-off tasks or timed, repeatable tasks such as generating reports, executing batch scripts, starting database backups, and migrating schemas. The admin processes factor in the [twelve-factor manifesto](https://www.12factor.net/) was written with one-off tasks in mind. For cloud-native apps, this factor becomes more relevant when you're creating repeatable tasks, and the guidance in this section is oriented towards tasks like those.

Timed triggers are often built as cron jobs and handled inherently by the apps themselves. This model works, but it introduces logic that's tightly coupled to the app and that requires maintenance and coordination, especially if your apps are distributed across time zones.

Therefore, when you design for admin processes, you should decouple the management of these tasks from the app itself. Depending on the tools and infrastructure that your app runs on, use the following suggestions:

*   For running apps on GKE, start separate containers for admin tasks. You can take advantage of [CronJobs](https://cloud.google.com/kubernetes-engine/docs/how-to/cronjobs) in GKE. CronJobs run in ephemeral containers and let you control the timing, execution frequency, and retries if jobs fail or if they take too long to complete.
*   For hosting apps on App Engine or Compute Engine, you can externalize the triggering mechanism and create an endpoint for the trigger to invoke. This approach helps define a boundary around what the apps are responsible for, in contrast to the single-purpose focus of the endpoint. [Cloud Tasks](https://cloud.google.com/tasks/docs/) is a fully managed, asynchronous task execution service that you can use to implement this pattern with App Engine. You can also use [Cloud Scheduler](https://cloud.google.com/scheduler/), an enterprise-grade, fully managed scheduler on GCP, to trigger timed operations.

### Going beyond the twelve factors

The twelve factors described in this document offer guidance for how you should approach building cloud-native apps. These apps are the foundational building blocks of an enterprise.

A typical enterprise has many apps like these, often developed by several teams collaboratively to deliver business capability. It's important to establish some additional principles during the app development lifecycle, and not as an afterthought, to address how apps communicate with each other, and how they are secured and access controlled.

The following sections outline some of these additional considerations that you should make during app design and development.

#### Think API-first

Apps communicate using APIs. When you're building apps, think about how the app will be consumed by your app's ecosystem, and start by designing an API strategy. A good API design makes the API easy to consume by app developers and external stakeholders. It's a good practice to start by documenting the API using the [OpenAPI](https://www.openapis.org) specification before you implement any code.

APIs abstract the underlying app functionality. A well-designed API endpoint should isolate and decouple the consuming applications from the app infrastructure that provides the service. This decoupling gives you the ability to change the underlying service and its infrastructure independently, without impacting the app's consumers.

It's important to catalog, document, and publish the APIs that you develop so that the consumers of the APIs are able to discover and use the APIs. Ideally, you want the API consumers to serve themselves. You can accomplish this by setting up a developer portal. A developer portal serves as an entry point for all API consumers— internal for the enterprise, or external for consumers such as developers from your partner ecosystem.

[Apigee](https://cloud.google.com/apigee/), Google's API management product suite, helps you manage the [entire lifecycle of your APIs](https://cloud.google.com/apigee/api-management/design-apis/) from design, to build, to publish.

#### Security

The realm of security is wide, and includes operating systems, networks and firewalls, data and database security, app security, and identity and access management. It's of paramount importance to address all the dimensions of security in an enterprise's ecosystem.

From an app's point of view, APIs provide access to the apps in your enterprise ecosystem. You should therefore ensure that these building blocks address security considerations during the app design and build process. Considerations for helping to protect access to your app include the following:

*   **Transport Layer Security (TLS)**. Use TLS to help protect data in transit. You might want to use mutual TLS for your business apps; this is made easier if you use service meshes like [Istio on Google Kubernetes Engine](https://cloud.google.com/istio/). It's also common for some use cases to create allow lists and deny lists based on IP addresses as an additional layer of security. Transport security also involves protecting your services against DDoS and bot attacks.
*   **App and end-user security**. Transport security helps provide security for data in transit and establishes trust. But it's a best practice to add app-level security to control access to your app based on who the consumer of the app is. The consumers can be other apps, employees, partners, or your enterprise's end customers. You can enforce security using API keys (for consuming apps), certification-based authentication and authorization, [JSON Web Tokens (JWTs)](https://jwt.io/) exchange, or [Security Assertion Markup Language (SAML)](https://wikipedia.org/wiki/Security_Assertion_Markup_Language).

The security landscape constantly evolves within an enterprise, making it harder for you to code security constructs in your apps. API management products like Apigee help [secure APIs](https://cloud.google.com/apigee/api-management/secure-apis/) at all the layers mentioned in this section.

What's next
-----------

*   Review the [microservices demo app](https://github.com/GoogleCloudPlatform/microservices-demo) that employs twelve-factor app principles and is built using GCP products and services.
*   Review the GCP product suite for logging and monitoring; see the Stackdriver [documentation](https://cloud.google.com/logging/docs/).
*   Try out other Google Cloud Platform features for yourself. Have a look at our [tutorials](https://cloud.google.com/docs/tutorials).

  
  
from Hacker News https://ift.tt/2Ww1ftC