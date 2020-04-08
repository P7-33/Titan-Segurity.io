---
title: 'Deep Learning with Electronic Health Record (EHR) Systems'
date: 2019-09-26T03:52:00+01:00
draft: false
---

⚕️ Introduction

Walk into any machine learning conference and ask people about the applications of ML in healthcare and most will respond with the

[canonical example](https://arxiv.org/abs/1711.05225)

of using computer vision to diagnose diseases from medical scans (followed by a prolonged

[debate](https://twitter.com/AndrewYNg/status/930938692310482944)

about “should radiologists be worried about their jobs”). But there exists another source of data, beyond imaging studies, that can change the way we approach health: the electronic health record (EHR).

Data in EHR systems

EHR systems can have data from a variety of different sources including billing data, patient demographics, medical history, lab results, sensor data, prescriptions, clinical notes, medical images, etc. Hospitals adopt EHR systems to store data for every patient encounter, mainly for billing and insurance-related administrative purposes, but we can leverage these records to capture trends and draw conclusions.

**Note**: Be cautious about using data that was primarily created for insurance purposes. Often, it's not truly reflective of patient's condition but rather encompassing for billing / profit. Luckily, there are clinical reports, like radiology, diagnostic imaging, pathology reports, etc., that are intended for physician use and are more reflective of true patient conditions. Unfortunately, most of this data is not readily available in APIs because it's largely unstructured. This is a ripe space for ML to take raw, unstructured data and produce structured, computable data.

Types of data in EHR systems. \[

[source](https://goku.me)

\]

Application themes

While the number of

[potential applications](https://arxiv.org/abs/1706.03446)

from leveraging EHRs is bountiful, the current goals are around increasing clinical efficiency by minimizing medical misdiagnosis and augmenting the physician’s capabilities. There are so many different ways that machine learning is aiding in fulfilling these goals but the main themes of applications are

**representation learning**

,

**information extraction**

and

**clinical predictions**

. We will also cover several emerging themes that are gaining traction.

🔬 Representation learning

If you look inside an EHR system for a particular patient, you’ll find a record for each encounter. Each encounter will have details on the patient such as diagnosis or administered medications as a list of codes (ex.

[I10](https://www.icd10data.com/ICD10CM/Codes/I00-I99/I10-I16/I10-/I10)

for primary hypertension). These codes were initially developed for administrative purposes where each one represents a specific diagnosis, medication, procedure, etc. In order to use these codes as inputs into our models, we need a way of representing them.

Different types of medical codes. \[

[source](https://arxiv.org/abs/1706.03446)

\]

Traditional approaches involved representing these codes via

[one-hot encoding](https://chrisalbon.com/images/machine_learning_flashcards/One-Hot_Encoding_print.png)

. This approach failed to capture the meaningful representations between the different codes and also caused a computational dimensionality issue since there over a 100,000 different codes.

Application themes

One approach towards meaningful representations is to learn distributed embeddings via techniques like

[skip-gram](https://arxiv.org/abs/1310.4546)

. This is commonly employed in natural language processing to learn representations for words in a sentence. The skip-gram technique learns vector representations of words that can predict the neighboring words (context), which in turn captures the relationships between the words. However, unlike sentences, which are an ordered sequence of words, medical codes in a patient encounter do not have an intrinsic order to them. Therefore, it’s non-trivial to form (target, context) pairs required for the skip-gram technique.

[Choi et al.](https://arxiv.org/abs/1310.4546)

approached this issue by defining the (target, context) pairs at the patient encounter level rather than at the medical code level. Unlike a sequence of medical codes, the patient encounters (comprised of medical codes) do have an order to them. By representing each patient encounter with a binary vector for the codes present, we can feed it into a two-layer neural network that will predict the binary vector for neighboring visits.

Using skip-gram technique to learn distributed embeddings for medical codes. \[

[source](https://arxiv.org/abs/1602.05568)

\]

Once the embeddings are learned, we can represent the medical codes as inputs into our deep learning models for supervised tasks. But how do we know that the representations we learned are trustworthy?

**Interpretability**

Choi et al. applied a **non-negative constraint** on the code embeddings weight matrix by measuring loss for the skip-gram technique using W'c = ReLU(Wc) instead of Wc. This allowed them to inspect every ith embedding dimension and get the top k medical codes in that dimension. These codes should be highly correlated and the clusters should confirm established code groups from knowledge bases.

Top k codes from ith dimension of the embedding weight matrix. \[

[source](https://arxiv.org/abs/1602.05568)

\]

There are also several other techniques to learn meaningful representations for the medical codes and which one you choose depends on the data. You can use techniques like

[GloVe](https://nlp.stanford.edu/pubs/glove.pdf)

,

[CBOW](https://arxiv.org/abs/1301.3781)

or

[stacked autoencoders](https://www.nature.com/articles/srep26094)

to learn the embeddings. There are even

[advanced](https://arxiv.org/abs/1611.07012)

implementations where representations are learned with an attention model based on knowledge ontologies (great for infrequent codes).

**Tips**

You can use embeddings in three different ways:

1.  Completely skip learning embeddings and train the entire model for a supervised task with a randomly initialized embedding matrix end-to-end (can cause overfitting).
2.  Freeze the learned embeddings and train the rest of the model.
3.  Use the learned embeddings and train everything end-to-end.

Contextualized embeddings

**\[Updated 2019\]**

There has also been quite a bit of work in 2019 dealing with text representation. The traditional method of one-hot encoded representations evolved into word embeddings, which gave way for efficient representations that accounted for the relationship of the words to each other. You can use biomedical specific

[word and character level embeddings](http://bio.nlplab.org/)

, which were trained on large

[PubMed datasets](https://www.ncbi.nlm.nih.gov/pmc/tools/openftlist/)

, to represent your text. However, these representations did not account well for context. For example, the world

_discharge_

would have the same embedding whether it was used in the context of an emergency room discharge or excretions. To address this limitation, researchers leveraged

[BERT](https://arxiv.org/abs/1810.04805)

\- bidirectional encoder representations from

[Transformers](https://arxiv.org/abs/1706.03762)

. These representations are conditionally learned from bidirectionally looking at unlabeled text at all layers. After training, a pre-trained BERT model can be fine-tuned with one or a few output layers to produce contextualized embeddings for a myriad of applications. Researchers have since released publically available

[clinical BERT embeddings](https://github.com/EmilyAlsentzer/clinicalBERT)

(and

[BioBERT](https://github.com/dmis-lab/biobert)

) to represent text for downstream applications like named entity recognition (NER), relationship extraction and QA tasks.

![](https://practicalai.me/static/img/blog/ehr/bert.png)

Pretraining and finetunning with BERT. \[

[source](https://arxiv.org/abs/1810.04805)

\]

A small side note on all the recent representation techniques. Our focus shouldn't just be on the performance gain they provide. Especially in the clinical setting, having an accurate and contextualized representation for a concept is crucial. It's not just about overall performance, but also about the model's ability to adapt to the nuances of individual inputs.

⚒️ Information extraction

EHR systems not only hold patient information and codes but also things like physician’s notes, ambulance records, admission/discharge details, medication steps, etc. The difficult part is extracting information from the text. Traditional approaches include manual extraction which is costly especially when trained physicians are involved in the process. And you might be wondering why a simple automated lookup won’t suffice? But lookups don’t fare well when entities (ie.

[abbreviations](https://arxiv.org/abs/1804.04225)

) could mean different things depending on the context and the same entity can be expressed with a diverse vocabulary. There are several useful non-ML techniques, like

[Valx](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5573874/)

for getting lab test names and the corresponding measurement values and the

[NegEx](https://code.google.com/archive/p/negex/)

system for negation tagging, to name a few. However, there are several aspects of information extraction that can greatly benefit from deep learning.

Entity recognition

Deep learning approaches begin with representing the words in a sentence as a sequence of tokens. Then we can apply an embedding layer, feed it into a bidirectional (to account for surrounding context) gated RNN component and use a softmax on top of that to classify each token’s entity class.

Common deep learning approach for information extraction. \[

[source](https://arxiv.org/abs/1606.07953)

\]

However, this approach requires large datasets with annotated entities. To overcome this limitation,

[Xing et al.](https://arxiv.org/abs/1711.07908)

use language modeling (as a transfer learning approach) to aid in biomedical named entity recognition (NER). First, they use bidirectional language modeling (on

[PubMed abstracts](https://www.ncbi.nlm.nih.gov/pmc/tools/openftlist/)

) as a transfer learning approach to pretrain the NER model’s weights. They believed that this auxiliary task will prevent overfitting and improve convergence speed (helped F1 score about ~2% compared to baseline of randomly initialized weights on four benchmark datasets) on the main supervised task while using less data. They then used the pre-trained embeddings and LSTM weights for the supervised NER task and trained it end-to-end.

NER model architecture using pre-trained weights from language modeling. \[

[source](https://arxiv.org/abs/1711.07908)

\]

So now that we know how to extract entities and also represent them with meaningful representations, let’s see how we can leverage everything for a supervised task.

👩‍⚕️ Clinical predictions

Recall that EHR data for a patient is a sequence of encounters composed of medical codes, clinical notes, etc. Now that we have a way of meaningfully representing the inputs, we can leverage them for supervised tasks like predicting clinical outcomes. We’ll look at different use cases where different types of data are used to make predictions.

Codes and values

A typical patient encounter record in an EHR system will include a collection of medical codes, patient demographics, lab values etc. We can use this data as inputs to our model to predict an outcome like likelihood of a disease. There are two different ways of using this data to make predictions. The simple approach is to use a set of inputs to predict a static outcome like probability of heart disease.

[Choi et al.](https://arxiv.org/abs/1602.03686)

concatenated learned ICD code embeddings for a particular patient encounter to create a patient representation. They used this representation as the sole input into a model to predict the probability of heart failure.

The more involved approach is to process a sequence of inputs to make a prediction. Predictions could be made after each individual input or at the end of the entire sequence. Choi et al. developed

[Doctor AI](https://arxiv.org/abs/1511.05942)

, which uses ICD codes from one visit and the duration since the last visit to predict the next visit’s expected ICD codes and duration. They embed the input ICD codes (using embeddings learned from skip-gram) and concatenate the duration since last visit to feed it into a gated recurrent component. A softmax layer then uses the output to predict the subsequent visit’s diagnosis codes and time until the next visit.

Doctor AI’s architecture for predicting the subsequent visit ICD codes. \[

[source](https://arxiv.org/abs/1511.05942)

\]

Using this data, either as a single set of inputs or as a sequence of inputs, is fairly straight forward. However, there are plenty of other types of data that can add a lot of signal towards making predictions.

Clinical notes

So far we’ve seen examples of how structured data is used in making predictions. But there’s plenty of unstructured data that holds a lot of valuable information: physician notes, medical/procedure instructions, etc.

[Liu el al.](https://arxiv.org/abs/1808.04928)

explored using both CNN and RNN based structures for processing unstructured clinical notes to predict the onset of diseases within a prediction window.

**Tips**

1.  The prediction window based approach is very common for clinical prediction tasks. One tip that the authors provided was to leave a gap between the history window (where input data is collected) and the prediction window (where you see if the onset of the disease occurred or not). For example, they used a 12-month historical window, a 3-month gap and a 6-month prediction window in their study. This is done to prevent the model from “cheating” with information that’s generated just prior to the diagnosis time. We want to catch the onset of disease earlier on so our training data needs to reflect that requirement.
2.  The same patient’s data never appears in two separate datasets (train/val/test). Refer to this [blog post](http://www.fast.ai/2017/11/13/validation-sets/) for more details on constructing a proper validation/test set.

They first applied skip-gram to learn embeddings on an auxiliary dataset (abstracts from medical journals). They applied these embeddings on the input tokens and then used a CNN to apply 1D convolutions with various kernel sizes. It’s not enough just to use the notes to make clinical predictions, so they concatenated the max-pooled values with structured numerical data (demographics, lab values, etc.) to feed into FC layers for prediction. CNNs are a great option here because they can be applied to both char-level (for understanding abbreviations based on context) and word-level embeddings to find meaningful sub-structures with varying kernel sizes.

The authors also looked at using LSTMs for processing the word level embeddings. Here the embedded words are sequentially processed by a BiLSTM and then go through a max-pooling operation before being concatenated with the structured numerical data to be fed into FC layers for prediction. Though these recurrent structures are great for processing sequential data, they have a tough time preserving the gradient across 1000s of words. As a result, the authors processed the input tokens with CNNs and fed the max-pooled output into an RNN, which significantly reduced the sequence size that needed to be processed.

Combined CNN-RNN architecture to process clinical tokens. \[

[source](https://arxiv.org/abs/1808.04928)

\]

**Interpretability**

The authors wanted to know the influence of words or phrases towards the model’s prediction. They first tried a gradient based approach by measuring the gradient of the prediction with respect to each word’s embedding and calculate the norm. This approach resulted in very noisy results and not much interpretability.

Noisy results from the gradient based approach. \[

[source](https://arxiv.org/abs/1808.04928)

\]

Next, they tried a log-odds based approach where they looked at which n-grams affects the prediction. By seeing which n-grams activate neurons in the max-pooling or FC layer, we can find the most influential n-grams for the prediction that was made. This approach resulted in much more interpretable results compared to the gradient based approach.

Interpretable results from the log-odds based approach. \[

[source](https://arxiv.org/abs/1808.04928)

\]

Time-series data

One type of data that is increasing in size and has tremendous predictive value is time-series data. This type of data can come from sensors placed on medical devices, smartphones, etc. and they have the advantage of being continuously collected prior, during and after an event of interest occurs. Traditional methods for analyzing time-series data involved manual signal processing and using specific filters to extract features. Since the advent of deep learning, specifically convolutional neural networks, this manual preprocessing step is no longer required for meaningful feature engineering.

[Gotlibovych et al.](https://arxiv.org/abs/1807.10707)

(@

[Jawbone](https://twitter.com/jawbone)

) used time series data from EHR to detect atrial fibrillation (Afib is an irregular, rapid heartbeat that can increase your risk of stroke, heart failure, etc.) using raw PPG signals (a signal derived from using light to get the volumetric measurement of an organ). They used a convolutional-recurrent architecture to process the time-series inputs, which were a sequence of samples collected at regular time intervals. The inputs from a receptive field of fixed length are initially processed by a CNN. The CNN acts as digital signal filters that can extract useful signals from the raw time series data. The output from the CNN goes through a max-pool operation (for downsampling) which is then fed into an LSTM to account for previously processed signals. Finally, an FC layer with a sigmoid activation is used to determine the probability of Afib for a particular receptive field.

Convolutional-recurrent architecture to predict probability of Afib. \[

[source](https://arxiv.org/abs/1807.10707)

\]

Medical scans

Even though we slightly undermined image processing at the beginning of this post, there’s no denying that medical scans hold some of the most valuable clinical information. X-rays, CT, MRI and many other types of scans all require the expertise of a radiologist to accurately process the information. But after deep learning improved upon existing computer vision techniques, models were able to perform specific parts of a radiologist’s job really well. We’re not going to be looking at just how much of the expertise can be mapped with machine learning models but instead we’re going to focus on things to be wary of. Typically, a complex pre-trained CNN-based

[architecture](https://arxiv.org/abs/1602.07261)

is used to process the medical scans for diagnosis classification, tumor segmentation, etc. Great performance is achieved through a combination of complex models and large annotated datasets. But sometimes, your model may be performing really well by incorrectly focusing on confounding features (extraneous influencers in the data that aren’t accounted for).

[Zech et al.](https://arxiv.org/abs/1807.00431)

found that x-ray stickers, acting as confounding features, unintentionally influenced the classifications. They were using CNNs to process X-ray images to predict probability of pneumonia but found the confounding variables during the interpretability study. They found that the X-ray sticker on the scan was strongly correlated with where the x-ray was taken (poor region, wealthy region, etc.) which was strongly correlated with disease prevalence levels.

**Interpretability**

A great interpretability method when working with images is to use maximum activation. We can use activation maps to understand which regions of the input image were most influential towards the prediction. You’ll have to apply some normalization to highlight the most influential regions and get vivid results like below.

Using activation maps to capture confounding variables. \[

[source](https://arxiv.org/abs/1807.00431)

\]

The interpretability study revealed that the model was using the stickers as the most influential variable for making its prediction. Many people wonder why this is a problem but this type of prediction will create false positives in the poor regions and false negatives in the other regions. Confounding variables can also assume

[other forms](https://arxiv.org/abs/1705.08821)

like structured numerical variables (ie. socio-economic status, etc.), so it’s very important to use domain expertise and interpretability measures to capture them.

These are the four major types of data in EHR systems and a few of the common ways of handling them. A sound approach towards a clinical prediction task may involve using all of these different types of data together and you may have to come up with your own clever architectures to process them. But besides the work we’ve looked at so far, you can also draw inspiration from emerging themes.

📣 Emerging themes

Emerging themes don’t warrant their own sections just yet but they are noteworthy because they are quickly gaining traction in the research community. We will look at these topics really quickly but you can refer to the individual papers for more information.

Relationship extraction

Relation extraction is a subset of information extraction but there’s been quite a bit of new work on extracting new relationships that expand on existing knowledge bases. Clinical notes are filled with explicit relationships like Disease A causes symptoms B or Medicine X causes symptom Y. Lv et al. applied sparse autoencoders with a conditional random field (CRF) classifier to extract these explicit relationships with remarkable results. However, Zhang et al. took it one step further by extracting novel relationships via generative discovery. They use a conditional variational autoencoder (CVAE) to learn the latent space conditioned on the relationship type. After training, they can use density-based sampling to generate two entities based on an input relationship type, allowing them to find novel entity relationship pairs that expand existing knowledge bases.

Using a CVAE to conditionally generate entity relationship pairs. \[

[source](https://www.kdd.org/kdd2018/accepted-papers/view/on-the-generative-discovery-of-structured-medical-knowledge)

\]

Generative sampling

One of the issues with EHR data is the scarcity of data for particular diseases, procedures, etc. To tackle this issue, GANs are used to learn from patient records and generate samples to augment the training dataset. A GAN is composed of a generator and a discriminator (both are deep neural networks). The generator will try its best to make a sample by learning from a dataset and the discriminator will learn to predict if a given sample is generated by the generator or if it is from the original training dataset.

[Che et al.](https://arxiv.org/abs/1709.01648v1)

use GANs to augment their training dataset but recall that unlike VAEs, GANs generate samples based on the input and random noise. To address this limitation, the authors tweaked the generator with variation contrastive diverge in order to be able to generate samples that align with the same class as the input. With this tweak, the generated samples belong to a particular class and can be used to augment the training dataset.

![](https://practicalai.me/static/img/blog/ehr/gan.png)

GAN with a tweaked generator to generate samples conditioned on a class. \[

[source](https://arxiv.org/abs/1709.01648v1)

\]

Sometimes, however, GANs produce obvious outliers such as records with both male and female specific health codes. To eliminate these types of poorly simulated cases,

[Ravuri et al.](https://arxiv.org/abs/1804.08033)

(@

[CurAI](https://curai.com/)

) found a way to combine expert knowledge with EHR data to create simulated data for training. From EHR data, they generate medical cases with findings and diagnosis based on frequencies and likelihood from an established knowledge base. Generative sampling via semi-supervised learning is gaining traction because of the large data requirement for deep learning but the focus will be on incorporating existing EHR data and medical expertise.

Multitask learning

Multitask learning (MTL) has been shown to help with supervised tasks across many different domains, including

[natural language processing](https://arxiv.org/abs/1704.05742)

. The idea is to have your model predict for both the primary and auxiliary tasks. The auxiliary task is highly related to the primary task and the idea is that the model will learn things from the auxiliary task that will be useful for the primary task.

[Ding et al.](https://arxiv.org/abs/1808.03331v1)

have shown that MTL is both helpful and detrimental depending on your phenotype distribution.

Multitask learning architecture for phenotyping. \[

[source](https://arxiv.org/abs/1808.03331v1)

\]

They found that MTL is helpful for rare phenotypes but harmful for common phenotypes. The magnitude of benefit or harm increases as we add more auxiliary tasks. This is one of the very few examples of MTL in the clinical setting that I have found so there’s plenty of room for exploration and improvement here.

Recommendation systems

Recommendation systems are a great medium for delivering personalized interventions. However, an issue is that the outcome we are optimizing for is a delayed, long-term one.

[Mann et al.](https://arxiv.org/abs/1807.09387v1)

address this issue by factoring in intermediate signals. They use both the input state and the intermediate signals to predict the target y. They found that using intermediate signals, as opposed to just the initial state, significantly helped with performance on two recommendation based tasks.

Recommendation system that factors in intermediate signals. \[

[source](https://arxiv.org/abs/1807.09387v1)

\]

Both the input x and the intermediate signal z are used to predict y but backpropagation is only for the input channel. The trickiest aspect of this implementation is devising what the intermediate signals will be. We need to pick intermediate signals that are general enough that we see them from case to case (so we can use the model on new cases) but also specific enough for each case that they add meaningful value for the long term goal.

Counterfactual reasoning

One of the most interesting and necessary emerging ML health topics is counterfactual reasoning. All the supervised predictive modeling we’ve seen so far involves predicting outcomes based on a policy. We collect data from a window of time and then use that to predict the outcome at a later point in time. But patients can receive different treatments in between which can have an effect on the prediction. When the policy changes (ie. medications of varying quantities are administered at irregular times), our supervised models don’t generalize well.

[Schulam et al.](https://arxiv.org/abs/1703.10651)

used counterfactual gaussian processes (CGP) to measure outcomes that are insensitive to the action policies in our training data. CGPs can then map the trajectory of the outcome if an action a is taken from a defined set of actions. This allows us to ask the “what if” question which is useful for tasks like evaluating risk where we want to know how the patient will do without any treatment, or with two doses of medication X, etc.

![](https://practicalai.me/static/img/blog/ehr/cgp.png)

CGPs aid in mapping the trajectory of outcomes based on an action. \[

[source](https://arxiv.org/abs/1703.10651)

\]

Using CGP allows us to define the causal effect of an action since we know what would’ve happened had it not occured. This type of reasoning is highly interpretable and offers great value to physicians.

🏥 Industry applications

We are starting to see a massive

[increase](https://blog.ycombinator.com/there-are-now-141-bio-companies-funded-by-yc/)

in bio/health companies and many of them are even starting to leverage machine learning

_properly_

. But there are a few things to think about before machine learning is widely accepted in healthcare. As we’ve seen so far, deep learning methods have offered amazing results for clinical predictions but the lack of interpretability makes them brittle and untrustworthy. The deep learning applications that are having small success are the ones that are augmenting physician’s existing capabilities instead of trying to replace them. For example, using information extraction to transfer raw, unstructured notes into structured, computable schema or offering a ranked list of diagnosis from a patient’s symptoms. All of these augmenting features provide extra, relevant information and allow the medical expert to retain complete decision making power. Applications that follow this theme of influence are the ones that are going to be widely adopted.

Approach

**\[Updated 2019\]** With all the ML progress in healthcare, we need to be intentional about following a proper approach so we can separate hype from reality and, more importantly, safely transition research to the clinical setting.

Sobering tweet from Professor Saria on the need to separate hype from reality. \[

[source](https://twitter.com/suchisaria/status/1176932346324508673)

\]

When designing your deep learning models for clinical applications, there are many things to consider. One of the best papers I've seen these last few years is from the Google health group on how they used

[multi-modal learning for diagnosis of skin disease](https://ai.googleblog.com/2019/09/using-deep-learning-to-inform.html)

. You can read the specific paper

[here](https://arxiv.org/abs/1909.05382)

but let's breakdown the generalizable approach they took.

1.  **Really understand the problem and how it's currently addressed.**  
    Don't try to predict something just because it's cool or possible. This type of goal is acceptable for the purpose of publishing, but when you want to create products to help people, especially in the clinical setting, you need to consider the utility it will bring. In this paper, the researchers use patient metadata and images of their skin to predict specific skin condition. They could've resorted to just identifying the most likely disorder but they took the time to understand that physicians create a differential diagnosis (list of potential disorders) which they then use to conduct more tests to identify the exact condition. The objective function was carefully crafted while keeping this in mind. The more of a decision the algorithm makes, the more interpretability it needs to offer.
    
    *   **Don't restrict yourself to how things are currently done.**  
        This sounds like the opposite advice of #1 but now we're talking about the modeling phase. Think outside the box on what information to leverage to answer your ultimate question. In this paper, dermatologist typically use the skin condition itself to create their differential diagnosis and it's hard for them to keep track of the other features (ex. patient's history, family history, etc.) even when it's all on file. However, with a deep learning model, we can learn to leverage all of these multimodal features to gather signals from all the available input features.
        
        Proper approach using data, machine learning and a reference standard. \[
        
        [source](https://arxiv.org/abs/1909.05382)
        
        \]
        
    
2.  **Be intentional and thorough when creating your ground truths.**  
    One of the advantages/disadvantages of machine learning is that your model will learn to fit to your ground truth values. You must spend the time to design the proper values to optimize and be deliberate in your method for collecting them. In this paper, due to the variability in diagnosis even among professional dermatologists, the researchers aggregated ground truth labels from a group of 40 certified dermatologists. This allows our models to leverage the knowledge from an entire team of physicians to augment any one physician's decision.

Even with an approach like this there are still possibilities for a tool with such high utility to fail in the clinical setting. Many groups are starting to develop the proper testing and evaluation frameworks for ML tools but we still have quite a ways to go. I look forward to sharing the progress next year.

  
  
from Hacker News https://ift.tt/2mLytaN