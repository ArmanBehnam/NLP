# Dialogue

Dialogue is notoriously hard to evaluate. Past approaches have used human evaluation.

## Dialogue act classification

Dialogue act classification is the task of classifying an utterance with respect to the function it serves in a dialogue, i.e. the act the speaker is performing. Dialogue acts are a type of speech acts (for Speech Act Theory, see [Austin (1975)](http://www.hup.harvard.edu/catalog.php?isbn=9780674411524) and [Searle (1969)](https://www.cambridge.org/core/books/speech-acts/D2D7B03E472C8A390ED60B86E08640E7)).

### Switchboard corpus
The [Switchboard-1 corpus](https://catalog.ldc.upenn.edu/ldc97s62) is a telephone speech corpus, consisting of about 2,400 two-sided telephone conversation among 543 speakers with about 70 provided conversation topics. The dataset includes the audio files and the transcription files, as well as information about the speakers and the calls.

The Switchboard Dialogue Act Corpus (SwDA) [[download](https://web.stanford.edu/~jurafsky/swb1_dialogact_annot.tar.gz)] extends the Switchboard-1 corpus with tags from the [SWBD-DAMSL tagset](https://web.stanford.edu/~jurafsky/ws97/manual.august1.html), which is an augmentation to the Discourse Annotation and Markup System of Labeling (DAMSL) tagset. The 220 tags were reduced to 42 tags by clustering in order to improve the language model on the Switchboard corpus. A subset of the Switchboard-1 corpus consisting of 1155 conversations was used. The resulting tags include dialogue acts like statement-non-opinion, acknowledge, statement-opinion, agree/accept, etc.  
Annotated example:  
*Speaker:* A, *Dialogue Act:* Yes-No-Question, *Utterance:* So do you go to college right now?  

| Model           | Accuracy  |  Paper / Source | Code | 
| ------------- | :-----:| --- | --- |
| SGNN (Ravi et al., 2018) | 83.1 | [Self-Governing Neural Networks for On-Device Short Text Classification](https://www.aclweb.org/anthology/D18-1105.pdf)
| CASA (Raheja et al., 2019) | 82.9 | [Dialogue Act Classification with Context-Aware Self-Attention](https://www.aclweb.org/anthology/N19-1373.pdf)
| DAH-CRF (Li et al., 2019) | 82.3 | [A Dual-Attention Hierarchical Recurrent Neural Network for Dialogue Act Classification](https://www.aclweb.org/anthology/K19-1036.pdf)
| ALDMN (Wan et al., 2018) | 81.5 | [Improved Dynamic Memory Network for Dialogue Act Classification with Adversarial Training](https://arxiv.org/pdf/1811.05021.pdf)
| CRF-ASN (Chen et al., 2018) | 81.3 | [Dialogue Act Recognition via CRF-Attentive Structured Network](https://arxiv.org/abs/1711.05568) | |
| Bi-LSTM-CRF (Kumar et al., 2017) | 79.2 | [Dialogue Act Sequence Labeling using Hierarchical encoder with CRF](https://arxiv.org/abs/1709.04250) | [Link](https://github.com/YanWenqiang/HBLSTM-CRF) |
| RNN with 3 utterances in context (Bothe et al., 2018) | 77.34 | [A Context-based Approach for Dialogue Act Recognition using Simple Recurrent Neural Networks](https://arxiv.org/abs/1805.06280) | | 


### ICSI Meeting Recorder Dialog Act (MRDA) corpus
The [MRDA corpus](http://www1.icsi.berkeley.edu/Speech/mr/) [[download](http://www.icsi.berkeley.edu/~ees/dadb/icsi_mrda+hs_corpus_050512.tar.gz)] consists of about 75 hours of speech from 75 naturally-occurring meetings among 53 speakers. The tagset used for labeling is a modified version of the SWBD-DAMSL tagset. It is annotated with three types of information: marking of the dialogue act segment boundaries, marking of the dialogue acts and marking of correspondences between dialogue acts.   
Annotated example:  
*Time:* 2804-2810, *Speaker:* c6, *Dialogue Act:* s^bd, *Transcript:* i mean these are just discriminative.  
Multiple dialogue acts are separated by "^".

| Model           | Accuracy  |  Paper / Source | Code | 
| ------------- | :-----:| --- | --- | 
| DAH-CRF (Li et al., 2019) | 92.2 | [A Dual-Attention Hierarchical Recurrent Neural Network for Dialogue Act Classification](https://www.aclweb.org/anthology/K19-1036.pdf)
| CRF-ASN (Chen et al., 2018) | 91.7 | [Dialogue Act Recognition via CRF-Attentive Structured Network](https://arxiv.org/abs/1711.05568) | |
| CASA (Raheja et al., 2019) | 91.1 | [Dialogue Act Classification with Context-Aware Self-Attention](https://www.aclweb.org/anthology/N19-1373.pdf)
| Bi-LSTM-CRF (Kumar et al., 2017) | 90.9 | [Dialogue Act Sequence Labeling using Hierarchical encoder with CRF](https://arxiv.org/abs/1709.04250) | [Link](https://github.com/YanWenqiang/HBLSTM-CRF) |
| SGNN (Ravi et al., 2018) | 86.7 | [Self-Governing Neural Networks for On-Device Short Text Classification](https://www.aclweb.org/anthology/D18-1105.pdf)

## Dialogue state tracking

Dialogue state tacking consists of determining at each turn of a dialogue the
full representation of what the user wants at that point in the dialogue,
which contains a goal constraint, a set of requested slots, and the user's dialogue act.

### Second dialogue state tracking challenge

For goal-oriented dialogue, the dataset of the [second Dialogue Systems Technology Challenges](http://www.aclweb.org/anthology/W14-4337)
(DSTC2) is a common evaluation dataset. The DSTC2 focuses on the restaurant search domain. Models are
evaluated based on accuracy on both individual and joint slot tracking.

| Model           | Request | Area  |  Food  |  Price  |  Joint  |  Paper / Source |
| ------------- | :-----: | :-----:| :-----:| :-----:| :-----:| --- |
| Zhong et al. (2018) | 97.5 | - | - | - | 74.5| [Global-locally Self-attentive Dialogue State Tracker](https://arxiv.org/abs/1805.09655) |
| Liu et al. (2018) | - | 90 | 84 | 92 | 72 | [Dialogue Learning with Human Teaching and Feedback in End-to-End Trainable Task-Oriented Dialogue Systems](https://arxiv.org/abs/1804.06512) |
| Neural belief tracker (Mrkšić et al., 2017) | 96.5 | 90 | 84 | 94 | 73.4 | [Neural Belief Tracker: Data-Driven Dialogue State Tracking](https://arxiv.org/abs/1606.03777) |
| RNN (Henderson et al., 2014) | 95.7 | 92 | 86 | 86 | 69 | [Robust dialog state tracking using delexicalised recurrent neural networks and unsupervised gate](http://svr-ftp.eng.cam.ac.uk/~sjy/papers/htyo14.pdf) | 

### Wizard-of-Oz

The [WoZ 2.0 dataset](https://arxiv.org/pdf/1606.03777.pdf) is a newer dialogue state tracking dataset whose evaluation is detached from the noisy output of speech recognition systems. Similar to DSTC2, it covers the restaurant search domain and has identical evaluation.


| Model           | Request  |  Joint  |  Paper / Source |
| ------------- |  :-----:| :-----:| --- |
| Zhong et al. (2018) | 97.1 | 88.1 | [Global-locally Self-attentive Dialogue State Tracker](https://arxiv.org/abs/1805.09655) |
| Neural belief tracker (Mrkšić et al., 2017) | 96.5 | 84.4 | [Neural Belief Tracker: Data-Driven Dialogue State Tracking](https://arxiv.org/abs/1606.03777) |
| RNN (Henderson et al., 2014) | 87.1 | 70.8 | [Robust dialog state tracking using delexicalised recurrent neural networks and unsupervised gate](http://svr-ftp.eng.cam.ac.uk/~sjy/papers/htyo14.pdf) | 


### MultiWOZ

The [MultiWOZ dataset](https://arxiv.org/abs/1810.00278) is a fully-labeled collection of human-human written conversations spanning over multiple domains and topics. At a size of 10k dialogues, it is at least one order of magnitude larger than all previous annotated task-oriented corpora. The dialogue are set between a tourist and a clerk in the information. It spans over 7 domains.

#### Belief Tracking
<div class="datagrid" style="width:500px;">
<table>
<thead><tr><th></th><th colspan="2">MultiWOZ 2.0</th><th colspan="2">MultiWOZ 2.1</th></tr></thead>
<thead><tr><th>Model</th><th>Joint Accuracy</th><th>Slot</th><th>Joint Accuracy</th><th>Slot</th></tr></thead>
<tbody>
<tr><td><a href="https://www.aclweb.org/anthology/P18-2069">MDBT</a> (Ramadan et al., 2018) </td><td>15.57 </td><td>89.53</td><td></td><td></td></tr>
<tr><td><a href="https://arxiv.org/abs/1805.09655">GLAD</a> (Zhong et al., 2018)</td><td>35.57</td><td>95.44 </td><td></td><td></td></tr>
<tr><td><a href="https://arxiv.org/pdf/1812.00899.pdf">GCE</a> (Nouri and Hosseini-Asl, 2018)</td><td>36.27</td><td>98.42</td><td></td><td></td></tr>
<tr><td><a href="https://arxiv.org/pdf/1908.01946.pdf">Neural Reading</a> (Gao et al, 2019)</td><td>41.10</td><td></td><td></td><td></td></tr>

<tr><td><a href="https://arxiv.org/pdf/1907.00883.pdf">HyST</a> (Goel et al, 2019)</td><td>44.24</td><td></td><td></td><td></td></tr>
<tr><td><a href="https://www.aclweb.org/anthology/P19-1546/">SUMBT</a> (Lee et al, 2019)</td><td>46.65</td><td>96.44</td><td></td><td></td></tr>
<tr><td><a href="https://arxiv.org/pdf/1905.08743.pdf">TRADE</a> (Wu et al, 2019)</td><td>48.62</td><td>96.92</td><td>45.60</td><td></td></tr>
<tr><td><a href="https://arxiv.org/pdf/1909.00754.pdf">COMER</a> (Ren et al, 2019)</td><td>48.79</td><td></td><td></td><td></td></tr>
<tr><td><a href="https://arxiv.org/pdf/1911.06192.pdf">DSTQA</a> (Zhou et al, 2019)</td><td>51.44</td><td>97.24</td><td>51.17</td><td>97.21</td></tr>
<tr><td><a href="https://arxiv.org/pdf/1910.03544.pdf">DST-Picklist</a> (Zhang et al, 2019)</td><td></td><td></td><td>53.3</td><td></td></tr>
<tr><td><a href="https://www.aaai.org/Papers/AAAI/2020GB/AAAI-ChenL.10030.pdf">SST</a> (Chen et al. 2020)</td><td></td><td></td><td>55.23</td><td></td></tr>
<tr><td><a href="https://arxiv.org/abs/2005.02877">TripPy</a> (Heck et al. 2020)</td><td></td><td></td><td>55.3</td><td></td></tr>
<tr><td><a href="https://arxiv.org/pdf/2005.00796.pdf">SimpleTOD</a> (Hosseini-Asl et al. 2020)</td><td></td><td></td><td>55.72</td><td></td></tr>

</tbody>
</table>
</div>

#### Policy Optimization
<div class="datagrid" style="width:500px;">
<table>
<thead><tr><th>(INFORM	+ SUCCESS)*0.5 +	BLEU</th><th colspan="3">MultiWOZ 2.0</th><th colspan="3">MultiWOZ 2.1</th></tr></thead>
<thead><tr><th>Model</th><th>INFORM</th><th>SUCCESS</th><th>BLEU</th><th>INFORM</th><th>SUCCESS</th><th>BLEU</th></tr></thead>
<tbody>
 <tr><td><a href="https://arxiv.org/pdf/1907.05346.pdf">TokenMoE</a> (Pei et al. 2019)</td><td>75.30</td><td> 59.70</td><td> 16.81 </td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://pdfs.semanticscholar.org/47d0/1eb59cd37d16201fcae964bd1d2b49cfb55e.pdf">Baseline</a> (Budzianowski et al. 2018)</td><td>71.29</td><td> 60.96 </td><td> 18.8 </td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/pdf/1907.10016.pdf">Structured Fusion</a> (Mehri et al. 2019)</td><td>82.70</td><td>72.10</td><td> 16.34</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/abs/1902.08858">LaRL</a> (Zhao et al. 2019)</td><td>82.8</td><td>79.2</td><td> 12.8</td><td> </td><td> </td><td> </td></tr>
  <tr><td><a href="https://arxiv.org/pdf/2005.00796.pdf">SimpleTOD</a> (Hosseini-Asl et al. 2020)</td><td>88.9</td><td>67.1</td><td> 16.9</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/pdf/1911.08151.pdf">MoGNet</a> (Pei et al. 2019)</td><td>85.3</td><td>73.30</td><td> 20.13</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/pdf/1905.12866.pdf">HDSA</a> (Chen et al. 2019)</td><td>82.9</td><td>68.9</td><td> 23.6</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/abs/1910.03756">ARDM</a> (Wu et al. 2019)</td><td>87.4</td><td>72.8</td><td> 20.6</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/pdf/1911.10484.pdf">DAMD</a> (Zhang et al. 2019)</td><td>89.2</td><td>77.9</td><td> 18.6</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/pdf/2005.05298.pdf">SOLOIST</a> (Peng et al. 2020)</td><td>89.60</td><td> 79.30</td><td> 18.3</td><td> </td><td> </td><td> </td></tr>
<tr><td><a href="https://arxiv.org/pdf/2004.12363.pdf">MarCo</a> (Wang et al. 2020)</td><td>92.30</td><td> 78.60</td><td> 20.02</td><td> 92.50</td><td> 77.80</td><td> 19.54</td></tr>
<tfoot> </tfoot>
</tbody>
</table>
</div>

#### Natural Language Generation
<div class="datagrid" style="width:500px;"><table>
<thead><tr><th>Model</th><th>SER</th><th>BLEU</th></tr></thead>
<tbody>
<tr><td><a href="https://pdfs.semanticscholar.org/47d0/1eb59cd37d16201fcae964bd1d2b49cfb55e.pdf">Baseline</a> (Budzianowski et al. 2018)</td><td>2.99 </td><td> 0.632</td></tr>
</tbody>
</table>
</div>

#### End-to-End Modelling
<div class="datagrid" style="width:500px;">
<table>
<thead><tr><th>(INFORM	+ SUCCESS)*0.5 +	BLEU</th><th colspan="3">MultiWOZ 2.0</th><th colspan="3">MultiWOZ 2.1</th></tr></thead>
<thead><tr><th>Model</th><th>INFORM</th><th>SUCCESS</th><th>BLEU</th><th>INFORM</th><th>SUCCESS</th><th>BLEU</th></tr></thead>
<tbody>
<tr><td><a href="https://arxiv.org/pdf/1911.10484.pdf">DAMD</a> (Zhang et al. 2019)</td><td>76.3</td><td>60.4</td><td> 18.6</td><td> </td><td> </td><td> </td></tr>
 <tr><td><a href="https://arxiv.org/pdf/2005.00796.pdf">SimpleTOD</a> (Hosseini-Asl et al. 2020)</td><td>84.4</td><td>70.1</td><td> 15.01</td><td> </td><td></td><td></td></tr>
 <tr><td><a href="https://arxiv.org/pdf/2005.05298.pdf">SOLOIST</a> (Peng et al. 2020)</td><td>85.50</td><td>72.90</td><td> 16.54</td><td> </td><td></td><td> </td></tr>

<tfoot> </tfoot>
</tbody>
</table>
</div>

## Retrieval-based Chatbots
These systems take as input a context and a list of possible responses and rank the responses, returning the highest ranking one.

### Ubuntu IRC Data

There are several corpra based on the [Ubuntu IRC Channel Logs](https://irclogs.ubuntu.com):

- [Uthus and Aha (2013)](), available [here](https://daviduthus.org/UCC/), the first dataset to use the resource, but not for retrieval-based chatbot research.
- UDC v1, [Lowe et al. (2015)](https://arxiv.org/abs/1506.08909), available [here](http://dataset.cs.mcgill.ca/ubuntu-corpus-1.0/), the first version of the Ubuntu Dialogue Corpus.
- UDC v2, [Lowe et al. (2017)](http://dad.uni-bielefeld.de/index.php/dad/article/view/3698), available [here](https://arxiv.org/abs/1506.08909), the second version of the Ubuntu Dialogue Corpus.
- DSTC 7, [Gunasekara et al. (2019)](http://workshop.colips.org/dstc7/papers/dstc7_task1_final_report.pdf), available [here](https://ibm.github.io/dstc-noesis/public/index.html), the data from DSTC 7 track 1.
- DSTC 8, [Gunasekara et al. (2020)](http://jkk.name/pub/dstc20task2.pdf), available [here](https://github.com/dstc8-track2/NOESIS-II/), the data from DSTC 8 track 2.

Each version of the dataset contains a set of dialogues from the IRC channel, extracted by automatically disentangling conversations occurring simultaneously. See below for results on the disentanglement process.

The exact tasks used vary slightly, but all consider variations of Recall_N@K, which means how often the true answer is in the top K options when there are N total candidates.

| Data   | Model           |  R_100@1    |  R_100@10   |  R_100@50   |  MRR        |  Paper / Source |
| ------ | -------------   | :---------: | :---------: | :---------: | :---------: |---------------|
| DSTC 8 (main) | Wu et. al., (2020) | 76.1 | 97.9 | - | 84.8 | Enhancing Response Selection with Advanced Context Modeling and Post-training |
| DSTC 8 (subtask 2) | Wu et. al., (2020) | 70.6 | 95.7 | - | 79.9 | Enhancing Response Selection with Advanced Context Modeling and Post-training |
| DSTC 7 | Seq-Att-Network (Chen and Wang, 2019) | 64.5 | 90.2 | 99.4 | 73.5 | [Sequential Attention-based Network for Noetic End-to-End Response Selection](http://workshop.colips.org/dstc7/papers/07.pdf) |

| Data   | Model           | R_2@1       |  R_10@1      |  Paper / Source |
| ------ | -------------   | :---------: | :---------: |---------------|
| UDC v2 | DAM (Zhou et al. 2018) | 93.8 | 76.7 | [Multi-Turn Response Selection for Chatbots with Deep Attention Matching Network](http://www.aclweb.org/anthology/P18-1103) |
| UDC v2  | SMN (Wu et al. 2017) | 92.3 | 72.3 | [Sequential Matching Network: A New Architecture for Multi-turn Response Selection in Retrieval-Based Chatbots](https://arxiv.org/pdf/1612.01627.pdf) |
| UDC v2  | Multi-View (Zhou et al. 2017) | 90.8 | 66.2 | [Multi-view Response Selection for Human-Computer Conversation](https://aclweb.org/anthology/D16-1036) |
| UDC v2  | Bi-LSTM (Kadlec et al. 2015) | 89.5 | 63.0 | [Improved Deep Learning Baselines for Ubuntu Corpus Dialogs](https://arxiv.org/pdf/1510.03753.pdf) |

Additional results can be found in the DSTC task reports linked above.

### Reddit Corpus
The [Reddit Corpus](https://arxiv.org/abs/1904.06472) contains 726 million multi-turn dialogues from the Reddit board. Reddit  is an American social news aggregation website, where users can post links, and take partin discussions on these post. The task of Reddit Corpus is to select the correct response from 100 candidates (others are negatively sampled) by considering previous conversation history.  Models are evaluated with the Recall 1 at 100 metric (the 1-of-100 ranking accuracy). You can find more details at [here](https://github.com/PolyAI-LDN/conversational-datasets).

| Model           |   R_1@100   |  Paper / Source |
| -------------   |   :---------:|---------------|
| PolyAI Encoder (Henderson et al. 2019) |  61.3 | [A Repository of Conversational Dataset](https://arxiv.org/pdf/1904.06472.pdf) |
| USE (Cer et al. 2018) | 47.7 | [Universal Sentence Encoder](https://arxiv.org/abs/1803.11175) |
| BERT (Devlin et al. 2017) | 24.0 | [BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding](https://arxiv.org/abs/1810.04805) |
| ELMO (Peters et al. 2018) | 19.3 | [Deep contextualized word representations](https://arxiv.org/abs/1802.05365) |

### Advising Corpus
The [Advising Corpus](http://workshop.colips.org/dstc7/papers/dstc7_task1_final_report.pdf), available [here](https://ibm.github.io/dstc-noesis/public/index.html), contains a collection of conversations between a student and an advisor at the University of Michigan. They were released as part of DSTC 7 track 1 and used again in DSTC 8 track 2.

| Model           |  R_100@1    |  R_100@10   |  R_100@50   |  MRR        |  Paper / Source |
| -------------   | :---------: | :---------: | :---------: | :---------: |---------------|
| Yang et. al., (2020) | 56.4 | 87.8 | - | 67.7 | Transformer-based Semantic Matching Model for Noetic Response Selection |
| Seq-Att-Network (Chen and Wang, 2019) | 21.4 | 63.0 | 94.8 | 33.9 | [Sequential Attention-based Network for Noetic End-to-End Response Selection](http://workshop.colips.org/dstc7/papers/07.pdf)


## Generative-based Chatbots
The main task of generative-based chatbot is to generate consistent and engaging response given the context.
### Personalized Chit-chat

The task of persinalized chit-chat dialogue generation is first proposed by [PersonaChat](https://arxiv.org/pdf/1801.07243.pdf). The motivation is to enhance the engagingness and consistency of chit-chat bots via endowing explicit personas to agents. Here the `persona` is defined as several profile natural language sentences like "I weight 300 pounds.". NIPS 2018 has hold a competition [The Conversational Intelligence Challenge 2 (ConvAI2)](http://convai.io/) based on the dataset. The Evaluation metric is F1, Hits@1 and ppl. F1 evaluates on the word-level, and Hits@1 represents the probability of the real next utterance ranking the highest according to the model, while ppl is perplexity for language modeling. The following results are reported on dev set (test set is still hidden), almost of them are borrowed from [ConvAI2 Leaderboard](https://github.com/DeepPavlov/convai/blob/master/leaderboards.md).

| Model           | F1 | Hits@1 | ppl | Paper / Source | Code |
| -------------   | :---------: | :---------:| :--------: | ---------------| ------------- |
| P^2 Bot (Liu et al. 2020) | 19.77 | 81.9 | 15.12 | [You Impress Me: Dialogue Generation via Mutual Persona Perception](https://arxiv.org/pdf/2004.05388.pdf) | [Code](https://github.com/SivilTaram/Persona-Dialogue-Generation) |
| TransferTransfo (Thomas et al. 2019) | 19.09 | 82.1 | 17.51 | [TransferTransfo: A Transfer Learning Approach for Neural Network Based Conversational Agents](https://arxiv.org/pdf/1901.08149.pdf) | [Code](https://github.com/huggingface/transfer-learning-conv-ai) |
| Lost In Conversation | 17.79 | - | 17.3 | [NIPS 2018 Workshop Presentation](http://convai.io/NeurIPSParticipantSlides.pptx) | [Code](https://github.com/atselousov/transformer_chatbot) |
| Seq2Seq + Attention (Dzmitry et al. 2014) | 16.18 | 12.6 | 29.8 | [Neural Machine Translation by Jointly Learning to Align and Translate](https://arxiv.org/pdf/1409.0473.pdf) | [Code](https://github.com/facebookresearch/ParlAI/tree/master/projects/convai2/baselines/seq2seq) |
| KV Profile Memory (Zhang et al. 2018) | 11.9 | 55.2 | - | [Personalizing Dialogue Agents: I have a dog, do you have pets too?](https://arxiv.org/pdf/1801.07243.pdf) | [Code](https://github.com/facebookresearch/ParlAI/tree/master/projects/convai2/baselines/kvmemnn)

## Disentanglement

As noted for the Ubuntu data above, sometimes multiple conversations are mixed together in a single channel. Work on conversation disentanglement aims to separate out conversations. There are two main resources for the task.

This can be formultated as a clustering problem, with no clear best metric. Several metrics are considered:

- Variation of Information
- F-1 over 1-1 matched clusters using max-flow
- Precision, Recall, and F-score on exact match for clusters
- Local overlap
- Another form of F-1 defined by [Shen et al. (2006)](https://dl.acm.org/citation.cfm?doid=1148170.1148180)

### Ubuntu IRC

Manually labeled by [Kummerfeld et al. (2019)](https://www.aclweb.org/anthology/P19-1374), this data is available [here](https://jkk.name/irc-disentanglement/).

| Model                                            | VI   | 1-1  | Precision | Recall | F-Score | Paper / Source | Code      |
| ------------------------------------------------ | :--: | :--: | :-------: | :----: | :-----: | ---------------| --------- |
| BERT + BiLSTM                                    | 93.3 |    - |      44.3 |   49.6 |    46.8 | Pre-Trained and Attention-Based Neural Networks for Building Noetic Task-Oriented Dialogue Systems | - |
| FF ensemble: Vote      (Kummerfeld et al., 2019) | 91.5 | 76.0 |      36.3 |   39.7 |    38.0 | [A Large-Scale Corpus for Conversation Disentanglement](https://www.aclweb.org/anthology/P19-1374/) | [Code](https://jkk.name/irc-disentanglement) |
| Feedforward            (Kummerfeld et al., 2019) | 91.3 | 75.6 |      34.6 |   38.0 |    36.2 | [A Large-Scale Corpus for Conversation Disentanglement](https://www.aclweb.org/anthology/P19-1374/) | [Code](https://jkk.name/irc-disentanglement) |
| FF ensemble: Intersect (Kummerfeld et al., 2019) | 69.3 | 26.6 |      67.0 |   21.1 |    32.1 | [A Large-Scale Corpus for Conversation Disentanglement](https://www.aclweb.org/anthology/P19-1374/) | [Code](https://jkk.name/irc-disentanglement) |
| Linear               (Elsner and Charniak, 2008) | 82.1 | 51.4 |      12.1 |   21.5 |    15.5 | [You Talking to Me? A Corpus and Algorithm for Conversation Disentanglement](https://www.aclweb.org/anthology/P08-1095/) | [Code](https://www.asc.ohio-state.edu/elsner.14/resources/chat-distr.tgz) |
| Heuristic            (Lowe et al., 2015)         | 80.6 | 53.7 |      10.8 |    7.6 |     8.9 | [Training End-to-End Dialogue Systems with the Ubuntu Dialogue Corpus](http://dad.uni-bielefeld.de/index.php/dad/article/view/3698) | [Code](https://github.com/npow/ubuntu-corpus) |

### Linux IRC

This data has been manually annotated three times:

- By [Elsner and Charniak (2008)](https://www.aclweb.org/anthology/P08-1095), available [here](https://www.asc.ohio-state.edu/elsner.14/resources/chat-distr.tgz).
- A portion by [Mehri and Carenini (2017)](https://aclweb.org/anthology/I17-1062/), available [here](http://shikib.com/td_annotations).
- By [Kummerfeld et al. (2019)](https://www.aclweb.org/anthology/P19-1374), available [here](https://jkk.name/irc-disentanglement/).

| Data | Model           | 1-1        | Local | Shen F-1 | Paper / Source | Code          |
| ---- | -------------   | :---------:| :---: | :------: | ---------------| ------------- |
| Kummerfeld | Linear     (Elsner and Charniak, 2008) | 59.7 | 80.8 | 63.0 | [You Talking to Me? A Corpus and Algorithm for Conversation Disentanglement](https://www.aclweb.org/anthology/P08-1095/) | [Code](https://www.asc.ohio-state.edu/elsner.14/resources/chat-distr.tgz) |
| Kummerfeld | Feedforward (Kummerfeld et al., 2019)  | 57.7 | 80.3 | 59.8 | [A Large-Scale Corpus for Conversation Disentanglement](https://www.aclweb.org/anthology/P19-1374/) | [Code](https://jkk.name/irc-disentanglement) |
| Kummerfeld | Heuristic   (Lowe et al., 2015)        | 43.4 | 67.9 | 50.7 | [Training End-to-End Dialogue Systems with the Ubuntu Dialogue Corpus](http://dad.uni-bielefeld.de/index.php/dad/article/view/3698) | [Code](https://github.com/npow/ubuntu-corpus) |
| Elsner | Linear     (Elsner and Charniak, 2008)     | 53.1 | 81.9 | 55.1 | [You Talking to Me? A Corpus and Algorithm for Conversation Disentanglement](https://www.aclweb.org/anthology/P08-1095/) | [Code](https://www.asc.ohio-state.edu/elsner.14/resources/chat-distr.tgz) |
| Elsner | Feedforward (Kummerfeld et al., 2019)      | 52.1 | 77.8 | 53.8 | [A Large-Scale Corpus for Conversation Disentanglement](https://www.aclweb.org/anthology/P19-1374/) | [Code](https://jkk.name/irc-disentanglement) |
| Elsner | Wang and Oard (2009) | 47.0 | 75.1 | 52.8 | [Context-based Message Expansion for Disentanglement of Interleaved Text Conversations](https://www.aclweb.org/anthology/N09-1023/) | - |
| Elsner | Heuristic   (Lowe et al., 2015)            | 45.1 | 73.8 | 51.8 | [Training End-to-End Dialogue Systems with the Ubuntu Dialogue Corpus](http://dad.uni-bielefeld.de/index.php/dad/article/view/3698) | [Code](https://github.com/npow/ubuntu-corpus) |
