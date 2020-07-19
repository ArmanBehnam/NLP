# Part-of-speech tagging

Part-of-speech tagging (POS tagging) is the task of tagging a word in a text with its part of speech.
A part of speech is a category of words with similar grammatical properties. Common English
parts of speech are noun, verb, adjective, adverb, pronoun, preposition, conjunction, etc.

Example: 

| Vinken | , | 61 | years | old |
| --- | ---| --- | --- | --- |
| NNP | , | CD | NNS | JJ |

### Penn Treebank

A standard dataset for POS tagging is the Wall Street Journal (WSJ) portion of the Penn Treebank, containing 45 
different POS tags. Sections 0-18 are used for training, sections 19-21 for development, and sections 
22-24 for testing. Models are evaluated based on accuracy.

| Model           | Accuracy  |  Paper / Source | Code |
| ------------- | :-----:| --- | --- |
| Meta BiLSTM (Bohnet et al., 2018) | 97.96 | [Morphosyntactic Tagging with a Meta-BiLSTM Model over Context Sensitive Token Encodings](https://arxiv.org/abs/1805.08237) | |
| Flair embeddings (Akbik et al., 2018) | 97.85 | [Contextual String Embeddings for Sequence Labeling](http://aclweb.org/anthology/C18-1139) | [Flair framework](https://github.com/zalandoresearch/flair) |
| Char Bi-LSTM (Ling et al., 2015) | 97.78 | [Finding Function in Form: Compositional Character Models for Open Vocabulary Word Representation](https://www.aclweb.org/anthology/D/D15/D15-1176.pdf) | |
| Adversarial Bi-LSTM (Yasunaga et al., 2018) | 97.59 | [Robust Multilingual Part-of-Speech Tagging via Adversarial Training](https://arxiv.org/abs/1711.04903) | |
| BiLSTM-CRF + IntNet (Xin et al., 2018) | 97.58 | [Learning Better Internal Structure of Words for Sequence Labeling](https://www.aclweb.org/anthology/D18-1279) | |
| Yang et al. (2017) | 97.55 | [Transfer Learning for Sequence Tagging with Hierarchical Recurrent Networks](https://arxiv.org/abs/1703.06345) | |
| Ma and Hovy (2016) | 97.55 | [End-to-end Sequence Labeling via Bi-directional LSTM-CNNs-CRF](https://arxiv.org/abs/1603.01354) | |
| LM-LSTM-CRF (Liu et al., 2018)| 97.53 | [Empowering Character-aware Sequence Labeling with Task-Aware Neural Language Model](https://arxiv.org/pdf/1709.04109.pdf) | |
| NCRF++ (Yang and Zhang, 2018)| 97.49 | [NCRF++: An Open-source Neural Sequence Labeling Toolkit](http://www.aclweb.org/anthology/P18-4013) | [NCRF++](https://github.com/jiesutd/NCRFpp) |
| Feed Forward (Vaswani et a. 2016) | 97.4 | [Supertagging with LSTMs](https://aclweb.org/anthology/N/N16/N16-1027.pdf) | |
| Bi-LSTM (Ling et al., 2017) | 97.36 | [Finding Function in Form: Compositional Character Models for Open Vocabulary Word Representation](https://www.aclweb.org/anthology/D/D15/D15-1176.pdf) | | 
| Bi-LSTM (Plank et al., 2016) | 97.22 | [Multilingual Part-of-Speech Tagging with Bidirectional Long Short-Term Memory Models and Auxiliary Loss](https://arxiv.org/abs/1604.05529) | |


### Social media

The [Ritter (2011)](https://www.aclweb.org/anthology/D11-1141) dataset has become the benchmark for social media part-of-speech tagging. This is comprised of  some 50K tokens of English social media sampled in late 2011, and is tagged using an extended version of the PTB tagset.

| Model | Accuracy | Paper |
| --- | --- | ---|
| FastText + CNN + CRF | 90.53 | [Twitter word embeddings (Godin et al. 2019 (Chapter 3))](https://fredericgodin.com/research/twitter-word-embeddings/) | 
| CMU | 90.0 ± 0.5 | [Improved Part-of-Speech Tagging for Online Conversational Text with Word Clusters](http://www.cs.cmu.edu/~ark/TweetNLP/owoputi+etal.naacl13.pdf) | 
| GATE  | 88.69 | [Twitter Part-of-Speech Tagging for All: Overcoming Sparse and Noisy Data](https://www.aclweb.org/anthology/R13-1026) | 

### UD

[Universal Dependencies (UD)](http://universaldependencies.org/) is a framework for 
cross-linguistic grammatical annotation, which contains more than 100 treebanks in over 60 languages.
Models are typically evaluated based on the average test accuracy across 21 high-resource languages (♦ evaluated on 17 languages).

| Model           | Avg accuracy  |  Paper / Source |
| ------------- | :-----:| --- |
| Multilingual BERT and BPEmb (Heinzerling and Strube, 2019) | 96.77 | [Sequence Tagging with Contextual and Non-Contextual Subword Representations: A Multilingual Evaluation](https://arxiv.org/abs/1906.01569) |
| Adversarial Bi-LSTM (Yasunaga et al., 2018) | 96.65 | [Robust Multilingual Part-of-Speech Tagging via Adversarial Training](https://arxiv.org/abs/1711.04903) | 
| MultiBPEmb (Heinzerling and Strube, 2019) | 96.62 | [Sequence Tagging with Contextual and Non-Contextual Subword Representations: A Multilingual Evaluation](https://arxiv.org/abs/1906.01569) |
| Bi-LSTM (Plank et al., 2016) | 96.40 | [Multilingual Part-of-Speech Tagging with Bidirectional Long Short-Term Memory Models and Auxiliary Loss](https://arxiv.org/abs/1604.05529) |
| Joint Bi-LSTM (Nguyen et al., 2017)♦ | 95.55 | [A Novel Neural Network Model for Joint POS Tagging and Graph-based Dependency Parsing](https://arxiv.org/abs/1705.05952) |

[Go back to the README](../README.md)
