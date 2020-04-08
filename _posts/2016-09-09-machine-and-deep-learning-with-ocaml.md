---
title: 'Machine and Deep Learning with OCaml Natively'
date: 2019-10-30T04:42:00+01:00
draft: false
---

Neural Network[¶](https://ocaml.xyz/chapter/neural.html#neural-network "Permalink to this headline")
====================================================================================================

**NOTE: many places need fixes, not finished yet.**

I will cover the neural network module in this chapter. My original purpose of introducing neural network module into Owl is two-fold:

*   Test the expressiveness of Owl. Neural network is a useful and complex tool for building modern analytical applications so I chose it.
*   To validate my research argument on how to structure modern (distributed) analytical libraries. Namely, the high-level analytical functionality (ML, DNN, optimisation, regression, and etc.) should be “glued” to the classic numerical functions via algorithmic differentiation, and the computation should be distributed via a specialised engine providing several well-defined distribution abstractions.

In the end, I only used less than 3k lines of code to implement a quite full-featured neural network module. Now let’s go through what `Neural` module offers.

Module Structure[¶](https://ocaml.xyz/chapter/neural.html#module-structure "Permalink to this headline")
--------------------------------------------------------------------------------------------------------

The [Owl.Neural](https://github.com/ryanrhymes/owl/blob/master/lib/neural/owl_neural.ml) provides two submodules `S` and `D` for both single precision and double precision neural networks. In each submodule, it contains the following modules to allow you to work with the structure of the network and fine-tune the training.

*   `Graph` : create and manipulate the neural network structure.
*   `Init` : control the initialisation of the weights in the network.
*   `Activation` : provide a set of frequently used activation functions.
*   `Params` : maintains a set of training parameters.
*   `Batch` : the batch parameter of training.
*   `Learning_Rate` : the learning rate parameter of training.
*   `Loss` : the loss function parameter of training.
*   `Gradient` : the gradient method parameter of training.
*   `Momentum` : the momentum parameter of training.
*   `Regularisation` : the regularisation parameter of training.
*   `Clipping` : the gradient clipping parameter of training.
*   `Checkpoint` : the checkpoint parameter of training.
*   `Parallel` : provide parallel computation capability, need to compose with Actor engine. (Experimental, a research project in progress.)

Types of Neuron[¶](https://ocaml.xyz/chapter/neural.html#types-of-neuron "Permalink to this headline")
------------------------------------------------------------------------------------------------------

I have implemented a set of commonly used neurons in [Owl.Neural.Neuron](https://github.com/ryanrhymes/owl/blob/master/lib/neural/owl_neural_neuron.ml). Each neuron is a standalone module and adding a new type of neuron is much easier than adding a new one in Tensorflow or other framework thanks to Owl’s [Algodiff](https://github.com/ryanrhymes/owl/blob/master/lib/owl_algodiff_generic.mli) module.

`Algodiff` is the most powerful part of Owl and offers great benefits to the modules built atop of it. In neural network case, we only need to describe the logic of the forward pass without worrying about the backward propagation at all, because the `Algodiff` figures it out automatically for us thus reduces the potential errors. This explains why a full-featured neural network module only requires less than 3.5k lines of code. Actually, if you are really interested, you can have a look at Owl’s [Feedforward Network](https://github.com/ryanrhymes/owl/blob/master/examples/feedforward.ml) which only uses a couple of hundreds lines of code to implement a complete Feedforward network.

In practice, you do not need to use the modules defined in [Owl.Neural.Neuron](https://github.com/ryanrhymes/owl/blob/master/lib/neural/owl_neural_neuron.ml) directly. Instead, you should call the functions in [Graph](https://github.com/ryanrhymes/owl/blob/master/lib/neural/owl_neural_graph.ml) module to create a new neuron and add it to the network. Currently, Graph module contains the following neurons.

*   `input`
*   `activation`
*   `linear`
*   `linear_nobias`
*   `embedding`
*   `recurrent`
*   `lstm`
*   `gru`
*   `conv1d`
*   `conv2d`
*   `conv3d`
*   `max_pool1d`
*   `max_pool2d`
*   `avg_pool1d`
*   `avg_pool2d`
*   `global_max_pool1d`
*   `global_max_pool2d`
*   `global_avg_pool1d`
*   `global_avg_pool2d`
*   `fully_connected`
*   `dropout`
*   `gaussian_noise`
*   `gaussian_dropout`
*   `alpha_dropout`
*   `normalisation`
*   `reshape`
*   `flatten`
*   `lambda`
*   `add`
*   `mul`
*   `dot`
*   `max`
*   `average`
*   `concatenate`

These neurons should be sufficient for creating from simple MLP to the most complicated Google’s Inception network.

Training & Inference[¶](https://ocaml.xyz/chapter/neural.html#training-inference "Permalink to this headline")
--------------------------------------------------------------------------------------------------------------

Owl provides a very functional way to construct a neural network. You only need to provide the shape of the date in the first node (often `input` neuron), then Owl will automatically infer the shape for you in the downstream nodes which saves us a lot of efforts and significantly reduces the potential bugs.

Let’s use the single precision neural network as an example. To work with single precision networks, you need to use/open the following modules

```
open Owl open Neural.S open Neural.S.Graph open Algodiff.S 
```

The code below creates a small convolutional neural network of six layers. Usually, the network definition always starts with `input` neuron and ends with `get_network` function which finalises and returns the constructed network. We can also see the input shape is reserved as a passed in parameter so the shape of the data and the parameters will be inferred later whenever the `input_shape` is determined.

```
let make\_network input\_shape \= input input\_shape |> lambda (fun x \-> Maths.(x / F 256.)) |> conv2d \[|5;5;1;32|\] \[|1;1|\] ~act\_typ:Activation.Relu |> max\_pool2d \[|2;2|\] \[|2;2|\] |> dropout 0.1 |> fully\_connected 1024 ~act\_typ:Activation.Relu |> linear 10 ~act\_typ:Activation.Softmax |> get\_network 
```

Next, I will show you how the `train` function looks like. The first three lines in the `train` function is for loading the `MNIST` dataset and print out the network structure on the terminal. The rest lines defines a `params` which contains the training parameters such as batch size, learning rate, number of epochs to run. In the end, we call `Graph.train_cnn` to kick off the training process.

```
let train () \= let x, \_, y \= Dataset.load\_mnist\_train\_data\_arr () in let network \= make\_network \[|28;28;1|\] in Graph.print network; let params \= Params.config ~batch:(Batch.Mini 100) ~learning\_rate:(Learning\_Rate.Adagrad 0.005) 2. in Graph.train\_cnn ~params network x y |> ignore 
```

After the training is finished, you can call `Graph.model_cnn` to generate a functional model to perform inference. Moreover, `Graph` module also provides functions such as `save`, `load`, `print`, `to_string` and so on to help you in manipulating the neural network.

```
let model \= Graph.model\_cnn network;; let predication \= model data;; ... 
```

You can have a look at Owl’s [MNIST CNN example](https://github.com/ryanrhymes/owl/blob/master/examples/mnist_cnn.ml) for more details and run the code by yourself.

Examples[¶](https://ocaml.xyz/chapter/neural.html#examples "Permalink to this headline")
----------------------------------------------------------------------------------------

In the following, I will present several neural networks defined in Owl. All have been included in Owl’s [examples](https://github.com/ryanrhymes/owl/tree/master/examples) and can be run separately. If you are interested in the computation graph Owl generated for these networks, you can also have a look at [this chapter on Algodiff](https://ocaml.xyz/chapter/algodiff.html).

### Multilayer Perceptron (MLP) for MNIST[¶](https://ocaml.xyz/chapter/neural.html#multilayer-perceptron-mlp-for-mnist "Permalink to this headline")

```
let make\_network input\_shape \= input input\_shape |> linear 300 ~act\_typ:Activation.Tanh |> linear 10 ~act\_typ:Activation.Softmax |> get\_network 
```

### Convolutional Neural Network for MNIST[¶](https://ocaml.xyz/chapter/neural.html#convolutional-neural-network-for-mnist "Permalink to this headline")

```
let make\_network input\_shape \= input input\_shape |> lambda (fun x \-> Maths.(x / F 256.)) |> conv2d \[|5;5;1;32|\] \[|1;1|\] ~act\_typ:Activation.Relu |> max\_pool2d \[|2;2|\] \[|2;2|\] |> dropout 0.1 |> fully\_connected 1024 ~act\_typ:Activation.Relu |> linear 10 ~act\_typ:Activation.Softmax |> get\_network 
```

### VGG-like Neural Network for CIFAR10[¶](https://ocaml.xyz/chapter/neural.html#vgg-like-neural-network-for-cifar10 "Permalink to this headline")

```
let make\_network input\_shape \= input input\_shape |> normalisation ~decay:0.9 |> conv2d \[|3;3;3;32|\] \[|1;1|\] ~act\_typ:Activation.Relu |> conv2d \[|3;3;32;32|\] \[|1;1|\] ~act\_typ:Activation.Relu ~padding:VALID |> max\_pool2d \[|2;2|\] \[|2;2|\] ~padding:VALID |> dropout 0.1 |> conv2d \[|3;3;32;64|\] \[|1;1|\] ~act\_typ:Activation.Relu |> conv2d \[|3;3;64;64|\] \[|1;1|\] ~act\_typ:Activation.Relu ~padding:VALID |> max\_pool2d \[|2;2|\] \[|2;2|\] ~padding:VALID |> dropout 0.1 |> fully\_connected 512 ~act\_typ:Activation.Relu |> linear 10 ~act\_typ:Activation.Softmax |> get\_network 
```

### LSTM Network for Text Generation[¶](https://ocaml.xyz/chapter/neural.html#lstm-network-for-text-generation "Permalink to this headline")

```
let make\_network wndsz vocabsz \= input \[|wndsz|\] |> embedding vocabsz 40 |> lstm 128 |> linear 512 ~act\_typ:Activation.Relu |> linear vocabsz ~act\_typ:Activation.Softmax |> get\_network 
```

### Google’s Inception for Image Classification[¶](https://ocaml.xyz/chapter/neural.html#google-s-inception-for-image-classification "Permalink to this headline")

```
let conv2d\_bn ?(padding\=SAME) kernel stride nn \= conv2d ~padding kernel stride nn |> normalisation ~training:false ~axis:3 |> activation Activation.Relu let mix\_typ1 in\_shape bp\_size nn \= let branch1x1 \= conv2d\_bn \[|1;1;in\_shape;64|\] \[|1;1|\] nn in let branch5x5 \= nn |> conv2d\_bn \[|1;1;in\_shape;48|\] \[|1;1|\] |> conv2d\_bn \[|5;5;48;64|\] \[|1;1|\] in let branch3x3dbl \= nn |> conv2d\_bn \[|1;1;in\_shape;64|\] \[|1;1|\] |> conv2d\_bn \[|3;3;64;96|\] \[|1;1|\] |> conv2d\_bn \[|3;3;96;96|\] \[|1;1|\] in let branch\_pool \= nn |> avg\_pool2d \[|3;3|\] \[|1;1|\] |> conv2d\_bn \[|1;1;in\_shape; bp\_size |\] \[|1;1|\] in concatenate 3 \[|branch1x1; branch5x5; branch3x3dbl; branch\_pool|\] let mix\_typ3 nn \= let branch3x3 \= conv2d\_bn \[|3;3;288;384|\] \[|2;2|\] ~padding:VALID nn in let branch3x3dbl \= nn |> conv2d\_bn \[|1;1;288;64|\] \[|1;1|\] |> conv2d\_bn \[|3;3;64;96|\] \[|1;1|\] |> conv2d\_bn \[|3;3;96;96|\] \[|2;2|\] ~padding:VALID in let branch\_pool \= max\_pool2d \[|3;3|\] \[|2;2|\] ~padding:VALID nn in concatenate 3 \[|branch3x3; branch3x3dbl; branch\_pool|\] let mix\_typ4 size nn \= let branch1x1 \= conv2d\_bn \[|1;1;768;192|\] \[|1;1|\] nn in let branch7x7 \= nn |> conv2d\_bn \[|1;1;768;size|\] \[|1;1|\] |> conv2d\_bn \[|1;7;size;size|\] \[|1;1|\] |> conv2d\_bn \[|7;1;size;192|\] \[|1;1|\] in let branch7x7dbl \= nn |> conv2d\_bn \[|1;1;768;size|\] \[|1;1|\] |> conv2d\_bn \[|7;1;size;size|\] \[|1;1|\] |> conv2d\_bn \[|1;7;size;size|\] \[|1;1|\] |> conv2d\_bn \[|7;1;size;size|\] \[|1;1|\] |> conv2d\_bn \[|1;7;size;192|\] \[|1;1|\] in let branch\_pool \= nn |> avg\_pool2d \[|3;3|\] \[|1;1|\] (\* padding = SAME \*) |> conv2d\_bn \[|1;1; 768; 192|\] \[|1;1|\] in concatenate 3 \[|branch1x1; branch7x7; branch7x7dbl; branch\_pool|\] let mix\_typ8 nn \= let branch3x3 \= nn |> conv2d\_bn \[|1;1;768;192|\] \[|1;1|\] |> conv2d\_bn \[|3;3;192;320|\] \[|2;2|\] ~padding:VALID in let branch7x7x3 \= nn |> conv2d\_bn \[|1;1;768;192|\] \[|1;1|\] |> conv2d\_bn \[|1;7;192;192|\] \[|1;1|\] |> conv2d\_bn \[|7;1;192;192|\] \[|1;1|\] |> conv2d\_bn \[|3;3;192;192|\] \[|2;2|\] ~padding:VALID in let branch\_pool \= max\_pool2d \[|3;3|\] \[|2;2|\] ~padding:VALID nn in concatenate 3 \[|branch3x3; branch7x7x3; branch\_pool|\] let mix\_typ9 input nn \= let branch1x1 \= conv2d\_bn \[|1;1;input;320|\] \[|1;1|\] nn in let branch3x3 \= conv2d\_bn \[|1;1;input;384|\] \[|1;1|\] nn in let branch3x3\_1 \= branch3x3 |> conv2d\_bn \[|1;3;384;384|\] \[|1;1|\] in let branch3x3\_2 \= branch3x3 |> conv2d\_bn \[|3;1;384;384|\] \[|1;1|\] in let branch3x3 \= concatenate 3 \[| branch3x3\_1; branch3x3\_2 |\] in let branch3x3dbl \= nn |> conv2d\_bn \[|1;1;input;448|\] \[|1;1|\] |> conv2d\_bn \[|3;3;448;384|\] \[|1;1|\] in let branch3x3dbl\_1 \= branch3x3dbl |> conv2d\_bn \[|1;3;384;384|\] \[|1;1|\] in let branch3x3dbl\_2 \= branch3x3dbl |> conv2d\_bn \[|3;1;384;384|\] \[|1;1|\] in let branch3x3dbl \= concatenate 3 \[|branch3x3dbl\_1; branch3x3dbl\_2|\] in let branch\_pool \= nn |> avg\_pool2d \[|3;3|\] \[|1;1|\] |> conv2d\_bn \[|1;1;input;192|\] \[|1;1|\] in concatenate 3 \[|branch1x1; branch3x3; branch3x3dbl; branch\_pool|\] let make\_network img\_size \= input \[|img\_size;img\_size;3|\] |> conv2d\_bn \[|3;3;3;32|\] \[|2;2|\] ~padding:VALID |> conv2d\_bn \[|3;3;32;32|\] \[|1;1|\] ~padding:VALID |> conv2d\_bn \[|3;3;32;64|\] \[|1;1|\] |> max\_pool2d \[|3;3|\] \[|2;2|\] ~padding:VALID |> conv2d\_bn \[|1;1;64;80|\] \[|1;1|\] ~padding:VALID |> conv2d\_bn \[|3;3;80;192|\] \[|1;1|\] ~padding:VALID |> max\_pool2d \[|3;3|\] \[|2;2|\] ~padding:VALID |> mix\_typ1 192 32 |> mix\_typ1 256 64 |> mix\_typ1 288 64 |> mix\_typ3 |> mix\_typ4 128 |> mix\_typ4 160 |> mix\_typ4 160 |> mix\_typ4 192 |> mix\_typ8 |> mix\_typ9 1280 |> mix\_typ9 2048 |> global\_avg\_pool2d |> linear 1000 ~act\_typ:Activation.Softmax |> get\_network let \_ \= make\_network 299 |> print 
```

There is a great space for optimisation. There are also some new neurons need to be added, e.g., upsampling, transposed convolution, and etc. Anyway, things will get better and better.

  
  
from Hacker News https://ift.tt/2psroxg