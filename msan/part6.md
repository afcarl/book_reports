# Notes

## Part 6

### Resources

 - [Wiki](http://forums.fast.ai/t/wiki-lesson-6/)

### Notes

 - Torch vectors vs numpy: Default to numpy, except for modeling and derivatives
 - On GPU vs on CPU: CPU for inference
 - Look at embedding extreme values to determine 'true meaning'
 - Entity embeddings of categorical Variables Guo and Berkahn
 - Can run PCA on embeddings, and then visualize points
 - Skipgrams: Another approach, specific for NLP. Used to train word2vec originally

SGD

 - Lesson 6 sgd notebook

RNNs

 - Lesson 6 RNN notebook
 - Purpose: Maintains stateful representation, w/ long term dependencies, variable length sequences
 - Hyperbolic tan good for hidden state to hidden state activation
 - Aggregate hidden (previous) state and current state. Can add or can concatenate


