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

Abstract

 - Provide practical guidance for single layer CNN architectures, and which hyperparams to tune

Introduction

 - DL has many more free params than SVM, logistic
 - Training can be very slow
 - Possible model architectures & hyperparam space can be large
   - Input word vector representation, filter region size(S), number of feature maps, activation function(s), pooling strategy, regularization (dropout/l2)


## TODO

 - Read [Kim2014] Yoon Kim. 2014. Convolutional neural networks for sentence classification. arXiv preprint arXiv:1408.5882.




