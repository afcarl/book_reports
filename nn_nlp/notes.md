#[Neural Network Methods in Natural Language Processing (Synthesis Lectures on Human Language Technologies)](https://www.amazon.com/Language-Processing-Synthesis-Lectures-Technologies/dp/1627052984/ref=sr_1_1?ie=UTF8&qid=1508800401&sr=8-1&keywords=neural+network+methods+for+natural+language+processing)

 - Author: by Yoav Goldberg

## Preface

 - Meant as intro to field
 - Assumes CS / ML background
 - Not for advanced readers

## Chapter 1: Introduction

Notation
 
 - Pretty standard matrix / vector notation
 - Vectors are row-wise

## Chapter 2: Learning basics and linear models

 - Supervised learning
 - Train / test / validate
 - Binary / multiclass (argmax multiclass)
 - Log linear binary classification: Scale output from [-inf, inf] to [0,1], using sigmoid function
 - SGD

## Chapter 3: From linear models to multi-layer perceptron 

 - Linear models can't handle non-linear relationships
 - Can use the kernel trick
 - Can use a non-linear activation at end of linear model 

## Chapter 4: Feed Forward Neural Networks

 - Intro to NN
 - Common activation functions (sigmoid, relu, tanh, hard tanh)
 - Regularization (L1, L2) and dropout 
 - Embeddings (intro)

## Chapter 5 

Gradient

 - Graphs as DAGs
 - Forward computation
 - Backprop

Software

 - Static graph construction: Computation graph created and compiled before training
 - Dynamic graph construction: Computation graph created for each training sample

Practical advice

 - Initialization: 
   - xavier initialization is common for tanh. U[A,B], where A,B are functions of input and output dimm
   - He et al approach is common for ReLu
   - Restart: Can run same graph with different rand. initializations, select best one

 - Vanishing & exploding gradients
   - Can threshold large gradients
 - Saturation & Dead Neurons
   - Saturation: Use normalization
   - Dead neurons: Reduce learning rate
   - Batch normalization: Normalize activations in each training batch
 - Minibatches
   - Can speed up on GPU

TODO

 - Dive deeper into backprop

## Chapter 6: Features for Textual Data

 - Atomic units:
   - Words
   - Texts
   - Paired texts
   - Word in context
   - Relationship between two words

 - Common Feature
   - Words: Lemmas & stems, lexical resources (hashmap lookup for each word. E.g. wordnet words to cognitive synonyms)
   - Texts: Bag of words, weighting (e.g. TF-IDF), ngrams
   - Words in context: Window, position
   - Inferred properties (e.g. part of speech, syntax, anaphora (pronoun resolution))
   - Distributions features (e.g. embeddings, co-occurence, clustering)

TODO

 - Look into [wordnet](https://wordnet.princeton.edu/)

## Chapter 7: Case studies of NLP Features

 - Language identification: Bag of letter-bigrams. Related task: encoding detection
 - Topic classification: Pre-defined topics: Bag of words, possibly with pre-processing and TF-IDF
 - Authorship classification: bag of {function word, pronoun}, bag of POS tags (and POS N-grams) and function words (e.g. on, of, he)
 - Adv: Named entity resolution, preposition disambituation, arc factored parsing
 
## Chapter 8: From Textual Features to Inputs

Encoding categorical variables

 - One hot encoding
 - Dense encodings
 
 Aggregating dense vector windows
 
  - Sum
  - Sum w/ positional weighting (further from center word weighted lower)
  - Concatenate
  - CBOW: Avg of embedding vectors
  - Weighted CBOW; Weighted CBOW (E.g. w/ TF-IDF)
 
Dense lookup
 
 - Can effectively use OHE to 'select' word from Embedding matrix. Basically masking
  
Unknown words

 - Can use special symbol (e.g. `UNK`)
 - Word signatures: (e.g. `___ing*`, `*NUM*`), to capture some information
 - Word dropout: Random inversely proportional to word's frequency.
 - Word dropout for regularization: Randomly, no proportionality to word frequency  
 
 
Misc

 - Interaction terms unnecessary. Function is non-linear
 - Can train positionally dependent word embeddings. Exploding train time
 - Embedding dimensionality: 50-hundreds is common, no rule of thumb
 - Can treat output layer as a backwards embedding for output labels. 
 
Case study: POS tagging  