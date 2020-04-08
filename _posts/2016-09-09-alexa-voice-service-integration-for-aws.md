---
title: 'Alexa Voice Service Integration for AWS IoT Core'
date: 2019-11-26T04:54:00+01:00
draft: false
---

![Alexa Voice Service Integration for AWS IoT Core](https://d2908q01vomqb2.cloudfront.net/f6e1126cedebf23e1463aee73f9df08783640400/2019/11/22/Alexa-Voice-Service-Integration-for-AWS-IoT-Core_SocialMedia_2.png)

Alexa Voice Service (AVS) Integration is a new feature of AWS IoT Core that enables device makers to make any connected device an Alexa Built-in device. AVS for AWS IoT reduces both the cost and complexity of producing Alexa Built-in devices by offloading compute and memory intensive tasks from physical devices to the cloud. With the reduction in the engineering bill of materials (eBoM) cost, device makers can now cost-effectively build new categories of differentiated voice-enabled products such as light switches, thermostats, small appliances and more. This allows end-consumers to talk directly to Alexa in new parts of their home, office, or hotel rooms for a truly ambient experience.

Today, smart home IoT devices are Built with low cost microcontrollers (MCU) with limited memory to run real time operating systems. Until now, AVS solutions for Alexa Built-in products required expensive application processor-based devices with >50MB memory running on Linux or Android. These expensive hardware requirements made it cost prohibitive to integrate Alexa Voice on resource constrained IoT devices. AVS for AWS IoT enables Alexa Built-in functionality on MCUs like ARM Cortex ‘M’ class with <1MB embedded RAM by offloading memory and compute tasks to a virtual Alexa Built-in device in the cloud, thus reducing eBoM cost by up-to 50%.

To make the AVS Integration for AWS IoT Core as simple as possible, APN partners have launched AVS qualified hardware development kits enabled by real time operating systems for microcontrollers like Amazon FreeRTOS that connect to AWS IoT Core by default. This helps device makers go to market quickly without worrying about writing complex security and connectivity firmware or managing the large device footprint previously associated with building Alexa Built-in devices with the AVS Device SDK.

**How AVS Integration for AWS IoT Core Works**

The AVS Integration for AWS IoT Core introduces new reserved MQTT topics for communication with AVS. Devices will communicate with AVS over a single, secure MQTT connection to AWS IoT Core from the device maker’s AWS account. The device maker’s AWS account will forward the MQTT messages to AVS, which will process the audio data and send the response back to the device through AWS IoT Core. To connect to the reserved topic, you can either use an AVS qualified development kit or develop device-side application code using the publicly available AVS for AWS IoT API.

![](https://d2908q01vomqb2.cloudfront.net/f6e1126cedebf23e1463aee73f9df08783640400/2019/11/22/Product-Page-Diagram_Skyhook@2x-1024x352.png)

To establish communication with AWS IoT Core, you must have a device certificate, private key, or root CA installed on the device firmware. You would also need to register an AVS device on the AVS Developer Portal to receive Devicetype ID and Login with Amazon (LWA) credentials to connect and authenticate your device to the AVS API.

**Customer Success**

The AVS Integration for AWS IoT Core is already helping companies deliver more value at lower price points to their customers. iDevices was looking to expand their smart home portfolio to include a product with onboard voice services. In-house engineers and designers developed Instinct™, a smart light switch with Alexa Built-in. With the backend infrastructure and industrial design complete, the team needed to choose a cloud platform to execute and analyze IoT features. iDevices chose AWS IoT, which serves as the cloud-based messaging protocol to enable Alexa voice services, lighting control, and motion sensing functionality. By employing the AVS for AWS IoT, iDevices was able to accelerate time-to-market and optimize infrastructure costs for their Instinct light switch. Instinct allows users to invisibly integrate the power of Amazon Alexa throughout their homes and reap the benefits of whole-home voice control without sacrificing valuable counter space. ![](https://d2908q01vomqb2.cloudfront.net/f6e1126cedebf23e1463aee73f9df08783640400/2019/11/22/Screen-Shot-2019-11-22-at-1.39.00-PM-1024x577.png)

**Get Started Quickly with Partner Development Kits**

Development kits launched by our APN partners make it easy to get started: [NXP i.MX RT 106 A](https://www.nxp.com/design/designs/mcu-based-solution-for-br-alexa-voice-service:MCU-VOICE-CONTROL-AVS?&&tid=vanmcu-avs) and [Qualcomm Home Hub 100 Development Kit](https://www.qualcomm.com/products/qualcomm-home-hub-100-dev-kit-amazon-avs) for Amazon AVS are the first two available kits on the market and can be found on the [Development Kits for AVS web page](https://developer.amazon.com/en-US/alexa/alexa-voice-service/dev-kits). The kits include out-of-the box connectivity to AWS IoT Core, AVS qualified Audio Algorithms for Far-Field voice pickup, Echo Cancellation, and Alexa Wake Word, and AVS for AWS IoT application code. Using the feature application code, you can quickly prototype a device and, when you’re ready, port the implementation to your chosen MCU design for testing and device production.

This [Getting Started Guide ](https://docs.aws.amazon.com/iot/latest/developerguide/avs-integration-aws-iot.html)outlines how to start using the AVS Integration for AWS IoT Core with the NXP kit.

The AVS Integration for AWS IoT Core is available in all AWS regions where AWS IoT Core is available other than China (Beijing and Ningxia), Asia Pacific (Hong Kong) and Middle East (Bahrain). See the [AWS Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) for the current list of regions for AWS IoT Core. To learn more about the AVS Integration, view the [AWS IoT Core feature page.](https://aws.amazon.com/iot-core/features/)

  
  
from Hacker News https://ift.tt/35wRizq