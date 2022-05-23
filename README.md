# TestBankAILab

Identify Patterns of Sentence Structure by Machine Learning

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#overview">Overview</a></li>
    <li><a href="#data-collection">Data Collection</a></li>
    <li><a href="#data-cleaning">Data Cleaning</a></li>
    <li><a href="#eda">EDA</a></li>
      <ol>
        <li>
          <a href="#data-overview">Data Overview</a>
        </li>
        <li>
          <a href="#distributions-of-sme-selections">Distributions of SME Selection</a>
        </li>
        <li>
          <a href="#pos-tagging">Part of Speech(POS) Tagging</a>
        </li>
        <li>
          <a href="#named-entity-recognition">Named Entity Recognition(NER)</a>
        </li>
        <li>
          <a href="#post-editing-distribution">Post Edited Distribution</a>
        </li>
      </ol>
    <li><a href="#model-architechture">Model Architechture</a></li>
      <ol>
        <li>
          <a href="#cnn">CNN</a>
        </li>
        <li>
          <a href="#lstm">LSTM</a>
        </li>
      </ol>
    <li><a href="#model-performance">Model Performance</a></li>
    <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>


<!-- OVERVIEW -->
## Overview
Automatic Item Generation (AIG) are increasingly required and used to process large topics of information and scale the
demand for computerized testing. Recent work in Artificial Intelligence for AIG a.k.a Natural Question Generation
qualitatively state that they are short in syntactic, semantic, and contextual relevance although on small datasets. We
confirm this deficiency over large datasets quantitatively. Additionally, we find that human evaluation by Subject matter
experts (SMEs) conservatively reject at least ~9% portion of AI Test questions in our experiment over large diverse dataset
topics. Here we present analytical study of the differences, and this motivates our two phased post processing AI daisy
chain machine learning (ML) models for selection &amp; editing of pre AI generated questions using state of art techniques.
Finally, we identify &amp; propose the first selection step in the daisy chain using ML with 90+% accuracy and provide analytical
guidance for development of second editing step.

<!-- data-collection -->
## Data Collection
In order to perform a wider and larger experiment to validate our first claim we chose five
large books as the seed dataset. Numerous AI test questions have automatically been generated using these books. 
The proprietary BenchmarkAI method for NQG is based on Item generation techniques, 10 namely, “With weak theory, a
combination of outcomes from research, theory, and experience provide the guidelines
necessary for identifying and manipulating the elements in a model that yield generated
items.” It's suitable for broad content domains where few theoretical descriptions exist on
the knowledge and skills required to solve test items. The results of BenchmarkAI
questions are evaluated by human SMEs to identify quality questions. For our second
claim we devise an analytical method and let the SME edit and fix the selected questions
to improve the quality of selected questions. We then present the pattern of edits in terms
of structure and syntax. For our third claim we propose a daisy chain architecture to first
phase post-process the AI test bank questions.

  - Note: The data that support the findings of this study are available from the corresponding author, CM, upon reasonable request.
    Request Email: hsu.yuwei@northeastern.edu
 
<!-- data-cleaning -->
## Data Cleaning

```
# Make it lowercase and remove unnecessary punctuation
def clean_text(text):
    '''Make text lowercase, remove text in square brackets,remove links,remove punctuation
    and remove words containing numbers.'''
    text = str(text).lower()
    text = re.sub('&nbsp', ' ', text) #error in 'saved.question'
    text = re.sub('\[.*?\]', '', text)
    text = re.sub('https?://\S+|www\.\S+', '', text)
    text = re.sub('<.*?>+', '', text)
    text = re.sub('[%s]' % re.escape(string.punctuation), '', text)
    text = re.sub('\n', '', text)
    text = re.sub('\w*\d\w*', '', text)
    return text
```

```
# Remove stopwords
 def remove_stopwords(text):
    text = ' '.join(word for word in text.split(' ') if word not in stop_words)
    return text
```


<!-- EDA -->
## EDA

 <!-- data-overview -->
 #### Data Overview
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Numbers%20of%20Questions%20and%20Words.png" width = "650" title = "Dataset Overview">
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Textbook%20Distribution.png" width = "650" title = "Textbook Distribution">

 <!-- distributions-of-sme-selections -->
 #### Distributions of SME Selections 
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/SME%20Selections%20on%20Textbook.png" width = "650" title = "SME Selections">
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/QuestionLength.png" width = "650" title = "Question Length">
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/FrequentPhrase.png" width = "650" title = "Frequeny Phrase">

 <!-- pos-tagging -->
 #### POS tagging
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/POS%20Tagging.png" width = "650" title = "POS tagging">

 <!-- named-entity-recognition --> 
 #### Named Entity Recognition
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/NER.png" width = "650" title = "NER">

 <!-- Post-editing-Distribution -->
 #### Post Editing Distribution
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Post-editing.png" width = "650" title = "Post-editing Disttribution">
 
 
<!-- model-architechture -->
## Model Architechture

 <!-- cnn -->
 #### CNN
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/CNN.png" width = "650" title = "CNN">
 This figure showcases a CNN-based (Convolution Neural Network) selection model for
 selection of a NQG post-processing layer to delivery that a SME would consider high
 quality. The model is a sequential CNN model from keras with an initial embedding layer
 of dim 200 followed by a convolution layer and max pooling. There is a 10-neuron dense
 layer with a sigmoid output unit. The training loss under experiment is the binary cross
 entropy accuracy.
 
 <!-- lstm -->
 #### LSTM
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/LSTM.png" width = "650" title = "LSTM">
 This figure shows a LSTM-based selection model of NQG post-processing layer to achieve
 the same goal. The model is a keras sequential ANN with 128 size input embedding,
 followed by 128 size LSTM layer and sigmoid output unit. Training loss under experiment
 is once again binary cross entropy accuracy.

<!-- model-performance -->
## Model Performance

#### BLEU 
BLEU (bilingual evaluation understudy) is an algorithm for evaluating the quality of text
which has been machine-translated from one natural language to another. Quality is
considered to be the correspondence between a machine's output and that of a human:
"the closer a machine translation is to a professional human translation, the better it is"; –
this is the central idea behind BLEU. BLEUwas one of the first metrics to claim a high
correlation with human judgements of quality, and remains one of the most popular
automated and inexpensive metrics. But bleu metric is limited and a necessary but not
sufficient condition to SME acceptance. 

<img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Bleu.png" width = "650" title = "Bleu">
As per Table 3 our post
processing step identifies a small improvement in Bleu score of ~0.44 (2.4%) as well in
edit step, but we consider this as a lower floor due to the very nature of ignoring
syntactical and semantic correctness in bleu metric for select + edit step post processing.

#### Accuracy
We measure the test accuracy over couple of popular DNN techniques namely, LSTM
and CNN model. Here we compare prediction accuracies in ground truth questions 
(selected by SME in human evaluation) vs. those generated by DNN models in Table 4.

<img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Accuracy.png" width = "650" title = "Accuracy">


<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
[1] Yasunaga, Michihiro, et al. "Qa-gnn: Reasoning with language models and knowledge graphs
    for question answering." arXiv preprint arXiv:2104.06378. 2021.
    
[2] Yoon, Wonjin, et al. "Pre-trained language model for biomedical question answering." Joint
    European Conference on Machine Learning and Knowledge Discovery in Databases: Wurzburg,
    Germany, September 16-20, 2019. Cham Springer International Publishing, 2020.
    
[3] Abacha, Asma Ben, et al. "Overview of the vqa-med task at ImageCLEF 2020: Visual question
    answering and generation in the medical domain." CLEF Working Notes. 2020.

[4] Chen, Yu, Lingfei Wu, and Mohammed J. Zaki. "Reinforcement learning based graph-to-
    sequence model for natural question generation." arXiv preprint arXiv:1908.04942 2019.

[5] Sun, Yibo, et al. "Joint learning of question answering and question generation." IEEE
    Transactions on Knowledge and Data Engineering 32.5, 2019: pp. 971-982.

[6] Zhang, Shiyue, and Mohit Bansal. "Addressing semantic drift in question generation for semi-
    supervised question answering." arXiv preprint arXiv:1909.06356 (2019).

[7] Chan, Ying-Hong, and Yao-Chung Fan. "A recurrent BERT-based model for question
    generation." Proceedings of the 2nd Workshop on Machine Reading for Question Answering.
    2019

[8] Klein, Tassilo, and Moin Nabi. "Learning to answer by learning to ask: Getting the best of gpt-
    2 and bert worlds." arXiv preprint arXiv:1911.02365 (2019).

[9] Gierl, Mark J., et al. "A method for generating educational test items that are aligned to the
    common core state standards." Journal of Applied Testing Technology, vol 16.1, 2015, pp. 1-18.
    
[10] Gierl, Mark J., and Hollis Lai. "The role of item models in automatic item generation."
     International Journal of Testing 12.3, 2012, pp 273-298.
     
[11] Gierl, Mark J., and Hollis Lai. "Automatic item generation." Handbook of Test Development.
     Routledge, 2015, pp. 426-446.
