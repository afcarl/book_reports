# [A Sensitivity Analysis of (and Practitioners’ Guide to) Convolutional Neural Networks for Sentence Classification](https://arxiv.org/abs/1510.03820)

## First pass

Meta
 - CNNs require architecture optimization / black magic
 - One layer CNNs examined
 - Meant to provide practical advice / best starting architecture
 
Models
 - 9 text -> categorical classification data sets studied
 - Averaged word embeddings (Word2vec and glove embeddings)
 - SVM for baseline
 - Single region (CNN kernel?) size metrics
 - Multiple region size metrics
 - Notes on activation / pooling hyperparameters
 - Notes on regularization

Conclusion

 - List of exacting recommendations for hyperparameters
 - Limits scope to single sentence classification

## Second pass

### Abstract

 - Provide practical guidance for single layer CNN architectures, and which hyperparams to tune

### 1: Introduction

 - DL has many more free params than SVM, logistic
 - Training can be very slow
 - Possible model architectures & hyperparam space can be large
   - Input word vector representation, filter region size(S), number of feature maps, activation function(s), pooling strategy, regularization (dropout/l2)

 - Optimization: Random & Bayesian optimization. Bayesian is not common in deployed systems
 - Goal: List parameters worth tuning, 'best' setting regardless of data set, reasonable ranges for hyper-parameters
 - Metrics: Mean accuracies are insufficient. 

### 2: Background and preliminaries

 - Pre-trained word vectors
   - Static: Fixed inputs
   - Non-static: WV trained for specific task
 - 'One-hot' vector inputs to CNNs (?)


CNN Architecture

 - A: Sentence matrix (s x d matrix): Rows are words in vector representation
   - d: Word vector dimm
   - s: Sentence length. 
 - Filters
   - Width: Set to word length (i.e. d)
   - Height: Variable, set to number of adjacent words
   - Region size: Filter height
 - w: Convolution's positional weights
 - o: Output from convolutional layer
 - c: Feature map, activation of o

 - Optimizations
   - Can use many filters w/ same size and different weights for different kinds of features
   - Pooling is performed to map variable length o to fix length vectors. 1 max pooling is common
   - Features are then concatenated
   - Pooling output is fed to a softmax for classification
 - Optimization
   - Can apply dropout or l2 just before softmax
   - Usual loss: categorical cross entropy loss
   - Optimization: SGD w/ back prop

### 3: Data sets

 - MR: Sentence polarity
 - SST-1: Stanford Sentiment Tree (sentences only)
 - SST-2: Subset from SST-1, containing 2 classes
 - Subj: Subjectivity data set
 - TREC: Question classification
 - CR: Customer review
 - MPQA: Opinion polarity
 - Opi: Opinosis data set (user reviews)
 - Irony: Reddit sentences, labelled ironic or not. Re-sampled due to class inbalance

## 4: Baseline models

## TODO

 - Read [Kim2014] Yoon Kim. 2014. Convolutional neural networks for sentence classification. arXiv preprint arXiv:1408.5882.




