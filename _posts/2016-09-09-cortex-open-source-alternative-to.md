---
title: 'Cortex: An open source alternative to SageMaker'
date: 2019-10-18T02:07:00+01:00
draft: false
---

[](https://github.com/cortexlabs/cortex/tree/v0.9.0#deploy-machine-learning-models-in-production)Deploy machine learning models in production
=============================================================================================================================================

Cortex is an open source platform that takes machine learning models—trained with nearly any framework—and turns them into production web APIs in one command.  

[![Demo](https://camo.githubusercontent.com/589ff5bd598eb953df1bf151bd8c6142738cc4ff/68747470733a2f2f636f727465782d7075626c69632e73332d75732d776573742d322e616d617a6f6e6177732e636f6d2f64656d6f2f6769662f76302e382e676966)](https://camo.githubusercontent.com/589ff5bd598eb953df1bf151bd8c6142738cc4ff/68747470733a2f2f636f727465782d7075626c69632e73332d75732d776573742d322e616d617a6f6e6177732e636f6d2f64656d6f2f6769662f76302e382e676966)  

  

[](https://github.com/cortexlabs/cortex/tree/v0.9.0#quickstart)Quickstart
-------------------------------------------------------------------------

Below, we'll walk through how to use Cortex to deploy OpenAI's GPT-2 model as a service on AWS. You'll need to [install Cortex](https://www.cortex.dev/install) on your AWS account before getting started.

  

### [](https://github.com/cortexlabs/cortex/tree/v0.9.0#step-1-configure-your-deployment)Step 1: Configure your deployment

Define a `deployment` and an `api` resource. A `deployment` specifies a set of APIs that are deployed together. An `api` makes a model available as a web service that can serve real-time predictions. The configuration below will download the model from the `cortex-examples` S3 bucket. You can run the code that generated the model [here](https://colab.research.google.com/github/cortexlabs/cortex/blob/0.9/examples/text-generator/gpt-2.ipynb).

```
# cortex.yaml - kind: deployment name: text - kind: api name: generator model: s3://cortex-examples/text-generator/gpt-2/124M request\_handler: handler.py
```

  

### [](https://github.com/cortexlabs/cortex/tree/v0.9.0#step-2-add-request-handling)Step 2: Add request handling

The model requires encoded data for inference, but the API should accept strings of natural language as input. It should also decode the inference output. This can be implemented in a request handler file using the `pre_inference` and `post_inference` functions:

```
# handler.py from encoder import get\_encoder encoder \= get\_encoder() def pre\_inference(sample, metadata): context \= encoder.encode(sample\["text"\]) return {"context": \[context\]} def post\_inference(prediction, metadata): response \= prediction\["sample"\] return encoder.decode(response)
```

  

### [](https://github.com/cortexlabs/cortex/tree/v0.9.0#step-3-deploy-to-aws)Step 3: Deploy to AWS

Deploying to AWS is as simple as running `cortex deploy` from your CLI. `cortex deploy` takes the declarative configuration from `cortex.yaml` and creates it on the cluster. Behind the scenes, Cortex containerizes the model, makes it servable using TensorFlow Serving, exposes the endpoint with a load balancer, and orchestrates the workload on Kubernetes.

```
$ cortex deploy deployment started
```

You can track the status of a deployment using `cortex get`. The output below indicates that one replica of the API was requested and one replica is available to serve predictions. Cortex will automatically launch more replicas if the load increases and spin down replicas if there is unused capacity.

```
$ cortex get generator --watch status up-to-date available requested last update avg latency live 1 1 1 8s 123ms url: http://\*\*\*.amazonaws.com/text/generator
```

  

### [](https://github.com/cortexlabs/cortex/tree/v0.9.0#step-4-serve-real-time-predictions)Step 4: Serve real-time predictions

Once you have your endpoint, you can make requests:

```
$ curl http://\*\*\*.amazonaws.com/text/generator \\ -X POST -H "Content-Type: application/json" \\ -d '{"text": "machine learning"}' Machine learning, with more than one thousand researchers around the world today, are looking to create computer-driven machine learning algorithms that can also be applied to human and social problems, such as education, health care, employment, medicine, politics, or the environment...
```

Any questions? [chat with us](https://gitter.im/cortexlabs/cortex).

  

[](https://github.com/cortexlabs/cortex/tree/v0.9.0#more-examples)More examples
-------------------------------------------------------------------------------

  

[](https://github.com/cortexlabs/cortex/tree/v0.9.0#key-features)Key features
-----------------------------------------------------------------------------

*   **Autoscaling:** Cortex automatically scales APIs to handle production workloads.
    
*   **Multi framework:** Cortex supports TensorFlow, Keras, PyTorch, Scikit-learn, XGBoost, and more.
    
*   **CPU / GPU support:** Cortex can run inference on CPU or GPU infrastructure.
    
*   **Rolling updates:** Cortex updates deployed APIs without any downtime.
    
*   **Log streaming:** Cortex streams logs from deployed models to your CLI.
    
*   **Prediction monitoring:** Cortex monitors network metrics and tracks predictions.
    
*   **Minimal declarative configuration:** Deployments are defined in a single `cortex.yaml` file.
    

  
  
from Hacker News https://github.com/cortexlabs/cortex/tree/v0.9.0