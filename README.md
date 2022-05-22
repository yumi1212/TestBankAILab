# TestBankAILab

POST PROCESSING SELECTION OF AUTOMATIC ITEM GENERATION IN 
QUESTIONING TO ENSURE HUMAN LIKE QUALITY WITH MACHINE LEARNING

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#overview">Overview</a></li>
    <li><a href="#eda">EDA</a></li>
      <ol>
        <li>
          <a href="#data-overview">Data Overview</a>
        </li>
        <li>
          <a href="#distributions-of-sme-selections">Distributions of SME Selection</a>
        </li>
        <li>
          <a href="#pos-tagging">POS Tagging</a>
        </li>
        <li>
          <a href="#Named-Entity-Recognition">Named Entity Recognition</a>
        </li>
        <li>
          <a href="#Post-editing-Distribution">Post Edited Distribution</a>
        </li>
      </ol>
    <li><a href="#Modeling">Modeling</a></li>
      <ol>
        <li>
          <a href="#CNN">CNN</a>
        </li>
        <li>
          <a href="#LSTM">LSTM</a>
        </li>
      </ol>
    <li><a href="#Result">Result</a></li>
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

 <!-- Named-Entity-Recognition --> 
 #### Named Entity Recognition
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/NER.png" width = "650" title = "NER">

 <!-- Post-editing-Distribution -->
 #### Post Editing Distribution
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Post-editing.png" width = "650" title = "Post-editing Disttribution">
 
 
<!-- Modeling -->
## Modeling

 <!-- CNN -->
 #### CNN
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/CNN.png" width = "650" title = "CNN">
 
 <!-- LSTM -->
 #### LSTM
 <img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/LSTM.png" width = "650" title = "LSTM">
 
<!-- Result -->
## Result
#### BLEU 
#### Accuracy
<img src = "https://github.com/yumi1212/TestBankAILab/blob/main/Plots/Accuracy.png" width = "650" title = "LSTM">


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
