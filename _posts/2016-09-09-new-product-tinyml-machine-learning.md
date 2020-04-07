---
title: 'NEW PRODUCT – TinyML: Machine Learning with TensorFlow Lite – Pete
Warden & Daniel Situnayake'
date: 2020-02-18T17:54:00+01:00
draft: false
---

[![4526 front ORIG 2020 02](https://cdn-blog.adafruit.com/uploads/2020/02/4526_front_ORIG_2020_02.jpg "4526_front_ORIG_2020_02.jpg")](https://www.adafruit.com/product/4526)

### NEW PRODUCT – [TinyML: Machine Learning with TensorFlow Lite – Pete Warden & Daniel Situnayake](https://www.adafruit.com/product/4526)

* * *

Deep learning networks are getting smaller. Much smaller. The Google Assistant team can detect words with a model just 14 kilobytes in size—small enough to run on a microcontroller. With this practical book, you’ll enter the field of TinyML, where deep learning and embedded systems combine to make astounding things possible with tiny devices.

Pete Warden and Daniel Situnayake explain how you can train models small enough to fit into any environment. Ideal for software and hardware developers who want to build embedded systems using machine learning, this guide walks you through creating a series of TinyML projects, step-by-step. No machine learning or microcontroller experience is necessary.

*   Build a speech recognizer, a camera that detects people, and a magic wand that responds to gestures
*   Work with Arduino and ultra-low-power microcontrollers
*   Learn the essentials of ML and how to train your own models
*   Train models to understand audio, image, and accelerometer data
*   Explore TensorFlow Lite for Microcontrollers, Google’s toolkit for TinyML
*   Debug applications and provide safeguards for privacy and security
*   Optimize latency, energy usage, and model and binary size

[![4526 inside 02 ORIG 2020 02](https://cdn-blog.adafruit.com/uploads/2020/02/4526_inside_02_ORIG_2020_02.jpg "4526_inside_02_ORIG_2020_02.jpg")](https://www.adafruit.com/product/4526)

[![4526 inside 01 ORIG 2020 02](https://cdn-blog.adafruit.com/uploads/2020/02/4526_inside_01_ORIG_2020_02.jpg "4526_inside_01_ORIG_2020_02.jpg")](https://www.adafruit.com/product/4526)

[![4526 inside 03 ORIG 2020 02](https://cdn-blog.adafruit.com/uploads/2020/02/4526_inside_03_ORIG_2020_02.jpg "4526_inside_03_ORIG_2020_02.jpg")](https://www.adafruit.com/product/4526)

**Table of Contents:**

*   Preface
    *   Conventions Used in This Book
    *   Using Code Examples
    *   O’Reilly Online Learning
    *   How to Contact Us
    *   Acknowledgments
*   1\. Introduction
    *   Embedded Devices
    *   Changing Landscape
*   2\. Getting Started
    *   Who Is This Book Aimed At?
    *   What Hardware Do You Need?
    *   What Software Do You Need?
    *   What Do We Hope You’ll Learn?
*   3\. Getting Up to Speed on Machine Learning
    *   What Machine Learning Actually Is
    *   The Deep Learning Workflow
        *   Decide on a Goal
        *   Collect a Dataset
        *   Design a Model Architecture
        *   Train the Model
        *   Convert the Model
        *   Run Inference
        *   Evaluate and Troubleshoot
    *   Wrapping Up
*   4\. The “Hello World” of TinyML: Building and Training a Model
    *   What We’re Building
    *   Our Machine Learning Toolchain
        *   Python and Jupyter Notebooks
        *   Google Colaboratory
        *   TensorFlow and Keras
    *   Building Our Model
        *   Importing Dependencies
        *   Generating Data
        *   Splitting the Data
        *   Defining a Basic Model
    *   Training Our Model
        *   Training Metrics
        *   Graphing the History
        *   Improving Our Model
        *   Testing
    *   Converting the Model for TensorFlow Lite
        *   Converting to a C File
    *   Wrapping Up
*   5\. The “Hello World” of TinyML: Building an Application
    *   Walking Through the Tests
        *   Including Dependencies
        *   Setting Up the Test
        *   Getting Ready to Log Data
        *   Mapping Our Model
        *   Creating an AllOpsResolver
        *   Defining a Tensor Arena
        *   Creating an Interpreter
        *   Inspecting the Input Tensor
        *   Running Inference on an Input
        *   Reading the Output
        *   Running the Tests
    *   Project File Structure
    *   Walking Through the Source
        *   Starting with main\_functions.cc
        *   Handling Output with output\_handler.cc
        *   Wrapping Up main\_functions.cc
        *   Understanding main.cc
        *   Running Our Application
    *   Wrapping Up
*   6\. The “Hello World” of TinyML: Deploying to Microcontrollers
    *   What Exactly Is a Microcontroller?
    *   Arduino
        *   Handling Output on Arduino
        *   Running the Example
        *   Making Your Own Changes
    *   SparkFun Edge
        *   Handling Output on SparkFun Edge
        *   Running the Example
        *   Testing the Program
        *   Viewing Debug Data
        *   Making Your Own Changes
    *   ST Microelectronics STM32F746G Discovery Kit
        *   Handling Output on STM32F746G
        *   Running the Example
        *   Making Your Own Changes
    *   Wrapping Up
*   7\. Wake-Word Detection: Building an Application
    *   What We’re Building
    *   Application Architecture
        *   Introducing Our Model
        *   All the Moving Parts
    *   Walking Through the Tests
        *   The Basic Flow
        *   The Audio Provider
        *   The Feature Provider
        *   The Command Recognizer
        *   The Command Responder
    *   Listening for Wake Words
        *   Running Our Application
    *   Deploying to Microcontrollers
        *   Arduino
        *   SparkFun Edge
        *   ST Microelectronics STM32F746G Discovery Kit
    *   Wrapping Up
*   8\. Wake-Word Detection: Training a Model
    *   Training Our New Model
        *   Training in Colab
    *   Using the Model in Our Project
        *   Replacing the Model
        *   Updating the Labels
        *   Updating command\_responder.cc
        *   Other Ways to Run the Scripts
    *   How the Model Works
        *   Visualizing the Inputs
        *   How Does Feature Generation Work?
        *   Understanding the Model Architecture
        *   Understanding the Model Output
    *   Training with Your Own Data
        *   The Speech Commands Dataset
        *   Training on Your Own Dataset
        *   How to Record Your Own Audio
        *   Data Augmentation
        *   Model Architectures
    *   Wrapping Up
*   9\. Person Detection: Building an Application
    *   What We’re Building
    *   Application Architecture
        *   Introducing Our Model
        *   All the Moving Parts
    *   Walking Through the Tests
        *   The Basic Flow
        *   The Image Provider
        *   The Detection Responder
    *   Detecting People
    *   Deploying to Microcontrollers
        *   Arduino
        *   SparkFun Edge
    *   Wrapping Up
*   10\. Person Detection: Training a Model
    *   Picking a Machine
    *   Setting Up a Google Cloud Platform Instance
    *   Training Framework Choice
    *   Building the Dataset
    *   Training the Model
    *   TensorBoard
    *   Evaluating the Model
    *   Exporting the Model to TensorFlow Lite
        *   Exporting to a GraphDef Protobuf File
        *   Freezing the Weights
        *   Quantizing and Converting to TensorFlow Lite
        *   Converting to a C Source File
    *   Training for Other Categories
    *   Understanding the Architecture
    *   Wrapping Up
*   11\. Magic Wand: Building an Application
    *   What We’re Building
    *   Application Architecture
        *   Introducing Our Model
        *   All the Moving Parts
    *   Walking Through the Tests
        *   The Basic Flow
        *   The Accelerometer Handler
        *   The Gesture Predictor
        *   The Output Handler
    *   Detecting Gestures
    *   Deploying to Microcontrollers
        *   Arduino
        *   SparkFun Edge
    *   Wrapping Up
*   12\. Magic Wand: Training a Model
    *   Training a Model
        *   Training in Colab
        *   Other Ways to Run the Scripts
    *   How the Model Works
        *   Visualizing the Input
        *   Understanding the Model Architecture
    *   Training with Your Own Data
        *   Capturing Data
        *   Modifying the Training Scripts
        *   Training
        *   Using the New Model
    *   Wrapping Up
        *   Learning Machine Learning
        *   What’s Next
*   13\. TensorFlow Lite for Microcontrollers
    *   What Is TensorFlow Lite for Microcontrollers?
        *   TensorFlow
        *   TensorFlow Lite
        *   TensorFlow Lite for Microcontrollers
        *   Requirements
        *   Why Is the Model Interpreted?
        *   Project Generation
    *   Build Systems
        *   Specializing Code
        *   Makefiles
        *   Writing Tests
    *   Supporting a New Hardware Platform
        *   Printing to a Log
        *   Implementing DebugLog()
        *   Running All the Targets
        *   Integrating with the Makefile Build
    *   Supporting a New IDE or Build System
    *   Integrating Code Changes Between Projects and Repositories
    *   Contributing Back to Open Source
    *   Supporting New Hardware Accelerators
    *   Understanding the File Format
        *   FlatBuffers
    *   Porting TensorFlow Lite Mobile Ops to Micro
        *   Separate the Reference Code
        *   Create a Micro Copy of the Operator
        *   Port the Test to the Micro Framework
        *   Build a Bazel Test
        *   Add Your Op to AllOpsResolver
        *   Build a Makefile Test
    *   Wrapping Up
*   14\. Designing Your Own TinyML Applications
    *   The Design Process
    *   Do You Need a Microcontroller, or Would a Larger Device Work?
    *   Understanding What’s Possible
    *   Follow in Someone Else’s Footsteps
    *   Find Some Similar Models to Train
    *   Look at the Data
    *   Wizard of Oz-ing
    *   Get It Working on the Desktop First
*   15\. Optimizing Latency
    *   First Make Sure It Matters
    *   Hardware Changes
    *   Model Improvements
        *   Estimating Model Latency
        *   How to Speed Up Your Model
    *   Quantization
    *   Product Design
    *   Code Optimizations
        *   Performance Profiling
    *   Optimizing Operations
        *   Look for Implementations That Are Already Optimized
        *   Write Your Own Optimized Implementation
        *   Taking Advantage of Hardware Features
        *   Accelerators and Coprocessors
    *   Contributing Back to Open Source
    *   Wrapping Up
*   16\. Optimizing Energy Usage
    *   Developing Intuition
        *   Typical Component Power Usage
        *   Hardware Choice
    *   Measuring Real Power Usage
    *   Estimating Power Usage for a Model
    *   Improving Power Usage
        *   Duty Cycling
        *   Cascading Design
    *   Wrapping Up
*   17\. Optimizing Model and Binary Size
    *   Understanding Your System’s Limits
    *   Estimating Memory Usage
        *   Flash Usage
        *   RAM Usage
    *   Ballpark Figures for Model Accuracy and Size on Different Problems
        *   Speech Wake-Word Model
        *   Accelerometer Predictive Maintenance Model
        *   Person Presence Detection
    *   Model Choice
    *   Reducing the Size of Your Executable
        *   Measuring Code Size
        *   How Much Space Is Tensorflow Lite for Microcontrollers Taking?
        *   OpResolver
        *   Understanding the Size of Individual Functions
        *   Framework Constants
    *   Truly Tiny Models
    *   Wrapping Up
*   18\. Debugging
    *   Accuracy Loss Between Training and Deployment
        *   Preprocessing Differences
        *   Debugging Preprocessing
        *   On-Device Evaluation
    *   Numerical Differences
        *   Are the Differences a Problem?
        *   Establish a Metric
        *   Compare Against a Baseline
        *   Swap Out Implementations
    *   Mysterious Crashes and Hangs
        *   Desktop Debugging
        *   Log Tracing
        *   Shotgun Debugging
        *   Memory Corruption
    *   Wrapping Up
*   19\. Porting Models from TensorFlow to TensorFlow Lite
    *   Understand What Ops Are Needed
    *   Look at Existing Op Coverage in Tensorflow Lite
    *   Move Preprocessing and Postprocessing into Application Code
    *   Implement Required Ops if Necessary
    *   Optimize Ops
    *   Wrapping Up
*   20\. Privacy, Security, and Deployment
    *   Privacy
        *   The Privacy Design Document
        *   Using a PDD
    *   Security
        *   Protecting Models
    *   Deployment
        *   Moving from a Development Board to a Product
    *   Wrapping Up
*   21\. Learning More
    *   The TinyML Foundation
    *   SIG Micro
    *   The TensorFlow Website
    *   Other Frameworks
    *   Twitter
    *   Friends of TinyML
    *   Wrapping Up
*   A. Using and Generating an Arduino Library Zip
*   B. Capturing Audio on Arduino
*   Index

[![4526 back ORIG 2020 02](https://cdn-blog.adafruit.com/uploads/2020/02/4526_back_ORIG_2020_02.jpg "4526_back_ORIG_2020_02.jpg")](https://www.adafruit.com/product/4526)

[In stock and shipping now!](https://www.adafruit.com/product/4526)