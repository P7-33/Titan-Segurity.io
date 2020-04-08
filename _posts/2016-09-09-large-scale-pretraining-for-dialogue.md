---
title: 'Large-Scale Pretraining for Dialogue'
date: 2019-11-07T07:52:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/6154722?s=400&v=4 "GitHub - microsoft/DialoGPT: Large-scale pretraining for dialogue")  

[](https://github.com/microsoft/DialoGPT#a-state-of-the-art-large-scale-pretrained-response-generation-model-dialogpt)A State-of-the-Art Large-scale Pretrained Response generation model (DialoGPT)
====================================================================================================================================================================================================

This repository contains the source code and trained model for a large-scale pretrained dialogue response generation model. The [human evaluation results](https://github.com/microsoft/DialoGPT#human_eval) indicate that the response generated from DialoGPT is comparable to human response quality under a single-turn conversation Turing test.

The repository is based on [huggingface pytorch-transformer](https://github.com/huggingface/transfer-learning-conv-ai) and [OpenAI GPT-2](https://github.com/openai/gpt-2), containing data extraction script, model training code and pretrained small (117M) medium (345M) and large (762M) model checkpoint.

The model is trained on 147M multi-turn dialogue from Reddit discussion thread. The largest model can be trained in several hours on a 8 V100 machines (however this is not required), with distributed training and FP16 option.

The include script can be used to reproduce the results of DSTC-7 grounded dialogue generation challenge and a 6k multi-reference dataset created from Reddit data.

Project webpage: [https://www.microsoft.com/en-us/research/project/large-scale-pretraining-for-response-generation/](https://www.microsoft.com/en-us/research/project/large-scale-pretraining-for-response-generation/)

[](https://github.com/microsoft/DialoGPT#minimal-computational-configurations)Minimal Computational Configurations
------------------------------------------------------------------------------------------------------------------

This code can be run on CPU, but it would be slow. We would recommend to use GPU to train and finetune all models. There is no minimal limit of the number of GPUs. However, if using distributed train for multiple GPUs configuration, the speed-up vs the number of GPUs is roughly sub-linear. To simulate the same batchsize when using less GPUs, please use a larger `gradient_accumulation_steps` in model training.

The 117M and 345M model can be loaded in a single GPU with 12G memory. The 762M model would require a single GPU that has greater than 16G memory for efficient training. The training speed on a benchmark data with 50M training instances and V100 GPUs:

n\_gpu

epoch time (min)

token/sec

1

158

25466

2

96

41861

4

73

54994

8

65

63612

Fine-tuning from our pretrained model on a new dataset typically requires 1-2 epochs.

[](https://github.com/microsoft/DialoGPT#setup--installation-tldr)Setup & Installation (TL;DR)
----------------------------------------------------------------------------------------------

We created a demo script `demo.py` to ease the difficulty of the deployment of this system. The `demo.py` contains a pipeline of **model downloading**, data extraction, data preprocessing and model training over a dummy dataset within one commandline.

#### [](https://github.com/microsoft/DialoGPT#train-model-with-conda-environment)Train model with Conda Environment

Please use the below commandlines to clone, install the requirements and load the Conda environment (Note that Cuda 10 is required):

```
sudo apt-get install -y make wget gzip bzip2 xz-utils zstd
```

```
git clone https://github.com/microsoft/DialoGPT.git cd DialoGPT conda env create -f LSP-linux.yml -n LSP conda activate LSP
```

If you run this on an architecture other than Linux, please use `LSP-generic.yml` instead of `LSP-linux.yml` but please note that the generic one is not tested in all platform, so the stablity can not be gauranteed. To use fp16 training, please install apex by using commands below

```
conda activate LSP git clone https://github.com/NVIDIA/apex cd apex git reset --hard 3d01e4a0a188cc8df54bc6e44cf5eb40ff6b4cc5 pip install -v --no-cache-dir --global-option="\--cpp\_ext" --global-option="\--cuda\_ext" . python3.6 demo.py
```

#### [](https://github.com/microsoft/DialoGPT#train-model-with-docker-environment)Train model with Docker environment

To start, first install the docker and Nvidia-docker from their official repos. The image environment for running the code can be loaded as below:

_Nvidia-docker v2._\*

```
$ docker run --gpus all --ipc=host --rm -it -v $PWD:/workspace --network=host icaruszyz/large-scale-training:dialogpt bash
```

_Nvidia-docker v1._\*

```
$ nvidia-docker --rm -it -v $PWD:/workspace --network=host icaruszyz/large-scale-training:dialogpt bash
```

Inside the docker container, run

[](https://github.com/microsoft/DialoGPT#pipeline-details)Pipeline details
--------------------------------------------------------------------------

This section explains all components in the `demo.py`.

#### [](https://github.com/microsoft/DialoGPT#data-loading)Data loading

Before running `demo.py`, you can set _DATA\_FOLDER_ (default value `./models`) in `demo.py` as the place you want to download all the data and pretrained/fine-tuned models. Then simply run

to

*   automatically download models and data,
*   prepare raw data into db that is ready to use for the program,
*   generate a training scripts.

Note that by default the `demo.py` will use a dummy data, please specify the Reddit training data by using option `--data`. Three options are available:`dummy`,`small` and `full`.

```
python demo.py --data small python demo.py --data full
```

The small Reddit data is around 140MB and the full Reddit data is more than 30GB. You can prepare a cup of coffee when processing with the full Reddit data because **it takes a long time**!

#### [](https://github.com/microsoft/DialoGPT#pretrained-model)Pretrained model

The pretrained and fine-tuned models are available on azure blobstorage [here](https://convaisharables.blob.core.windows.net/lsp). Please run/see `demo.py` for more details about how to download/use those models.

#### [](https://github.com/microsoft/DialoGPT#preparing-data)Preparing data

First, use the `prepare4db.sh` to convert a tsv data file into the correct format that the following script can recognize. The trainig data need to be then processed into a database file with below commandline:

```
python prepro.py --corpus $DATA\_PATH
```

#### [](https://github.com/microsoft/DialoGPT#using-the-training-script)Using the training script

The training script can be used in single GPU or multiple GPU settings (distributed training across multiple GPUs within a single node):

```
python ./LSP\_train.py # Single GPU training python -m torch.distributed.launch --nproc\_per\_node=8 ./LSP\_train.py # Training on 8 GPUs
```

The training script accept several arguments to tweak the training:

Argument

Type

Default value

Description

max\_seq\_length

`int`

`128`

Maximum number of tokens for each training instance.

train\_input\_file

`str`

`""`

Path of the training dataset in a .db format

eval\_input\_file

`str`

`""`

Path of the validation set in a tsv format

continue\_from

`int`

`0`

Resuming the training after a specified number of steps

fp16

`boolean`

`True`

Whether to use 16-bits floating point for model training.

train\_batch\_size

`int`

`4`

Batch size for training

valid\_batch\_size

`int`

`4`

Batch size for validation

gradient\_accumulation\_steps

`int`

`2`

Accumulate gradients on several steps

learning\_rate

`float`

`1e-5`

Learning rate

lr\_schedule

`str`

`noam`

Learning rate schedule can be chosen from \[`noam`, `noamwd`, `BERT`, `None`\]

num\_optim\_steps

`int`

`1000000`

Number of training optimization steps

no\_token\_id

`boolean`

`True`

If set True, using all-zeros token-type embedding.

During the training, two log files will be updated. The `train_log.txt` and `eval_log.txt` contains the model loss, perplexity and training speed (tokens/sec) statistics for the training and dev set.

The log file and saved model checkpoint can be found in `./models/output_model`

#### [](https://github.com/microsoft/DialoGPT#model-decoding)Model decoding

We note that even with properly filtered Reddit dataset, sometimes our model can still generate moderately toxic/inappropriate responses. Due to this reason, we are unable to provide the decoding script at this time (The live demo and decoding script access is upon invitation only now ). We are currently still working on a controlled decoding method to prevent this system from toxic generation. Please stay tuned.

[](https://github.com/microsoft/DialoGPT#models)Models
------------------------------------------------------

We release 6 fine-tuned models which can be further fine-tuned on low-resource user-customized dataset. The total parameters in these models range from 117M to 762M, in accord with OpenAI GPT-2 model sizes.

Model

Download

DialoGPT 762M model

[link](https://convaisharables.blob.core.windows.net/lsp/multiref/large_ft.pkl)

DialoGPT 345M model

[link](https://convaisharables.blob.core.windows.net/lsp/multiref/medium_ft.pkl)

DialoGPT 117M model

[link](https://convaisharables.blob.core.windows.net/lsp/multiref/small_ft.pkl)

The model files can be loaded exactly as the GPT-2 model checkpoint from Huggingface pytorch-transformer repository.

[](https://github.com/microsoft/DialoGPT#evaluations)Evaluations
----------------------------------------------------------------

#### [](https://github.com/microsoft/DialoGPT#dstc-7-challenge)DSTC-7 challenge

Our model achieved the state-of-the-art results in [DSTC-7 Challenge response generation task](https://github.com/mgalley/DSTC7-End-to-End-Conversation-Modeling).

Experiment

NIST2

NIST4

BLEU2

BLEU4

METEOR

ENT-4

DIST-1

DIST-2

Avg. Len

Human response

2.62

2.65

12.35%

3.13%

8.31%

10.45

16.66%

67.01%

18.8

DSTC-7 Winner

2.51

2.52

14.35%

1.83%

8.07%

9.03

10.89%

32.49%

15.1

DialoGPT 345M

2.80

2.82

14.16%

2.31%

8.51%

**10.08**

9.13%

39.73%

16.9

DialoGPT 345M (BS)

**2.92**

**2.97**

**19.18%**

**6.05%**

**9.29%**

9.57

**15.73%**

**51.03%**

14.2

where ENT represents the [Entropy score](https://arxiv.org/abs/1809.05972), and DIST represents the [Distinct score](https://arxiv.org/pdf/1510.03055.pdf). For all metrics except the average length, larger are better.

Note that the superior automatic evaluation comparing to human responses does not necessary imply that our model achieves human parity. Please check out our paper for more detailed analysis.

To fine-tune the `345M` DialoGPT model on the DSTC-7 challenge data on a server with 8 V100 GPUs, please run the following commandline (The DSTC data can be found at [DSTC-7 repo](https://github.com/mgalley/DSTC7-End-to-End-Conversation-Modeling)):

```
python3 -m torch.distributed.launch --nproc\_per\_node=8 train\_LSP.py --init\_checkpoint ./models/medium/medium\_ft.pkl --train\_input\_file ./data/DSTC\_train.db --eval\_input\_file ./data/DSTC\_valid.tsv --model\_name\_or\_path ./model/medium/ --learning\_rate 1e-4 --train\_batch\_size 64 --eval\_batch\_size 64 --no\_token\_id
```

The trained model can be found at [DSTC medium model](https://convaisharables.blob.core.windows.net/lsp/DSTC/medium_ft.pkl)

#### [](https://github.com/microsoft/DialoGPT#evaluation)Evaluation

1.  Please **downloads** the following 3rd-party packages and save into the empty folder `3rdparty`:
    
2.  Please follow the [DSTC-7 official repo](https://github.com/mgalley/DSTC7-End-to-End-Conversation-Modeling/tree/master/data_extraction) to extract the data, and put `data-official-test/test.refs.txt` into `./dstc/data/` folder.
    
3.  Run the extraction script below to produce the human response hypothesis file `human.resp.txt`:
    
4.  Finally, to reproduce the results of human hypothesis on DSTC dataset, please run following commands under the repo folder:
    

The evaluation results will be generated in the folder `./dstc/eval/`

[](https://github.com/microsoft/DialoGPT#6k-multi-ref-dataset-result)6K multi-ref dataset result
------------------------------------------------------------------------------------------------

### [](https://github.com/microsoft/DialoGPT#automatic-evaluation)Automatic evaluation

We test on 6K multi-ref dataset from Reddit (this test data will be release soon). The results are summarized in below

Experiment

NIST2

NIST4

BLEU2

BLEU4

METEOR

ENT-4

DIST-1

DIST-2

Avg. Len

Human response

3.41

4.25

17.90%

7.48%

10.64%

11

14.50%

63.00%

13.1

DialoGPT 117M

2.39

2.41

10.54%

1.55%

7.53%

10.78

8.60%

39.90%

12.8

DialoGPT 345M

3

3.06

16.96%

4.56%

9.81%

9.13

6.80%

26.30%

12.2

DialoGPT 762M

2.84

2.9

18.66%

5.25%

9.66%

9.72

7.76%

29.93%

11.2

DialoGPT 345M (BS)

**3.4**

**3.5**

**21.76%**

**7.92%**

10.74%

10.48

**12.38%**

**48.74%**

11.3

DialoGPT 345M (w/MMI)

3.28

3.33

15.68%

3.94%

**11.23%**

**11.25**

9.39%

45.55%

17.2

### [](https://github.com/microsoft/DialoGPT#human-evaluation)Human evaluation

We further conduct human evaluations (6K examples for each methods, each example is evaluated by 3 human judges). The results show a strong evidence that our generation quality is towards approaching the quality of real human responses, under this non-interactive Turing test:

_Relevance_: A and B, which one is more relevant to the source prompt.

System A

A Wins (%)

Ties (%)

B Wins (%)

System B

DialoGPT 345M

2671 (45%)

513 (9%)

2816 (47%)

Human responses

DialoGPT 345M

3281 (72%)

394 (9%)

882 (19%)

[PersonalityChat](https://docs.microsoft.com/en-us/azure/cognitive-services/project-personality-chat/overview)

DialoGPT 345M w/ MMI

**2871** (48%)

522 (9%)

2607 (43%)

Human responses

_Informativeness_: A and B, which one is more contentful and informative.

System A

A Wins (%)

Ties (%)

B Wins (%)

System B

DialoGPT 345M

2722 (45%)

234 (4%)

3044 (51%)

Human responses

DialoGPT 345M

3490 (77%)

206 (5%)

861 (19%)

[PersonalityChat](https://docs.microsoft.com/en-us/azure/cognitive-services/project-personality-chat/overview)

DialoGPT 345M w/ MMI

**3011** (50%)

234 (4%)

2755 (46%)

Human responses

_Human-Like_: A and B, which one do you think is more likely to be generated by Human.

System A

A Wins (%)

Ties (%)

B Wins (%)

System B

DialoGPT 345M

2716 (45%)

263 (4%)

3021 (50%)

Human responses

DialoGPT 345M

3462 (76%)

196 (4%)

899 (20%)

[PersonalityChat](https://docs.microsoft.com/en-us/azure/cognitive-services/project-personality-chat/overview)

DialoGPT 345M w/ MMI

**2978** (50%)

241 (4%)

2781 (46%)

Human responses

Please see full details in our arXiv paper (coming soon).

[](https://github.com/microsoft/DialoGPT#generated-examples)Generated Examples
------------------------------------------------------------------------------

*   Multi-turn generation examples from an interactive environment:

Role

Response

User

Does money buy happiness?

Bot

Depends how much money you spend on it .

User

What is the best way to buy happiness ?

Bot

You just have to be a millionaire by your early 20s, then you can be happy .

User

This is so difficult !

Bot

You have no idea how hard it is to be a millionaire and happy . There is a reason the rich have a lot of money

*   Multi-turn self-playing dialogue with user prompt

Role

Response

User

what is the meaning of life ?

Bot

The meaning is to be with your family and friends .

Bot

I’m going to guess : It means that your par-ents and friends have loved you . That’s the meaning , I believe .

Bot

I think the meaning is to make sure you’re alive when you die . So you’ll be with your family , friends , and yourself .

Bot

It’s not , but thanks for trying to help .

*   Commonsense question answering examples

User

Bot

who is the first president of the United States

George Washington

what is the boiling point of water?

I think it's about 212 F.

which one is bigger, sun or moon?

The sun .

which animal has black and white stripes?

A black and white striped cat .

*   Handling context that does not appear in training examples (note that training examples are sampled from 2005 to 2017)

User

Bot

The trading war between China and US is still happening .

I'm sure the Chinese government and the U . S . will be fine with that as long as they keep their arms on the table and the money flowing .

who won the world cup in 2018 ?

Germany , I believe .

Nvidia's Titan RTX is really good .

I have this card and i love it . No complaints .

Can Porsche beat Tesla with its new Taycan EV ?

I don't think so . The Tesla is more powerful than the porsche .

*   Our bot's response to philosophy questions

User

Bot

What is the meaning of a good life ?

I think it's that we're all connected to our past lives and the meaning of life is to live the way you want to and how you want to .

Which is more important -- being successful or being happy ?

Being successful is just endless . Being happy is the only thing that matters .

Is peace the only way to stop war ?

Not if the world is not willing to work with you . Peace is the ultimate goal , but peace requires more than that .

How much freedom should people have ?

The right amount of freedom is the freedom to do as you please , as long as you don't hurt people or property .

User

Bot

What do you think of the DialoGPT repo ?

It's pretty good , but it's very easy to find a bug .

Please start a issue if you spot any :)

[](https://github.com/microsoft/DialoGPT#try-our-system)Try our system
----------------------------------------------------------------------

The live demo and decoding script access is upon invitation only now. Please stayed tuned for the full release.

[](https://github.com/microsoft/DialoGPT#related-project)Related Project
------------------------------------------------------------------------

[](https://github.com/microsoft/DialoGPT#contact)Contact
--------------------------------------------------------

Please contact [DialoGPT@microsoft.com](mailto:DialoGPT@microsoft.com) if you have any questions/suggestions. However, the response will be sporadic. Please expected delays.

[](https://github.com/microsoft/DialoGPT#contributing)Contributing
------------------------------------------------------------------

This project welcomes contributions and suggestions. Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit [https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

[](https://github.com/microsoft/DialoGPT#disclaimer)Disclaimer
--------------------------------------------------------------

This repository aims to facilitate research in large-scale pretraining for conversational data. This toolkit contains only part of the modeling machinery needed to actually produce a model weight file in a running dialog. On its own, this model provides only information about the weights of various text spans; in order for a researcher to actually use it, they will need to bring conversational data of their own and decode the response generation from the pretrained system. Microsoft is not responsible for any generation from the 3rd party utilization of the pretrained system.

[](https://github.com/microsoft/DialoGPT#citation)Citation
----------------------------------------------------------

If you use this code in your research, you can cite our [arxiv paper](https://arxiv.org/abs/1911.00536):

```
@misc{zhang2019dialogpt, title={DialoGPT: Large-Scale Generative Pre-training for Conversational Response Generation}, author={Yizhe Zhang and Siqi Sun and Michel Galley and Yen-Chun Chen and Chris Brockett and Xiang Gao and Jianfeng Gao and Jingjing Liu and Bill Dolan}, year={2019}, eprint={1911.00536}, archivePrefix={arXiv}, primaryClass={cs.CL} }
```

  
  
from Hacker News https://ift.tt/33HgJNF