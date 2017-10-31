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

