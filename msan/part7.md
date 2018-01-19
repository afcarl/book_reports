# Notes

## Part 7

### Resources

 - [Wiki](http://forums.fast.ai/t/wiki-lesson-7/)

### Notes

Review of RNN

 - First hidden state is zero vectors or identity matrix
 - Very deep RNNs can have diminishing gradients, particularly for earlier layers
 - Back prop through time: Through away history of operations after every update
 - More gradient layers cause issues with large / small gradients
 - End of each epoch might be a different batch size (not enough observations for full batch). This means that hidden needs to be re-initialized w/ correct size
 - Tanh activation avoids gradient explosion (tanh has range in (-1,1))
 - GRU cell: Avoids exploding gradients: 
   - Reset gate:  Multiply previous hidden values by reset gate ( sigmoid of (weight * [previous weights, current weights])). Controls how much of hidden state is remembered
   - Update gate: Linear interpolation of previous state and current state
 - Cosine annealing callback: Works on layer optimizer, to modify learning rate for layer optimizer

Models from scratch

 - Lesson7-cifar10
 - Creating augmentations, padding, select random 32 x 32 spot from padded image
 - Stride 2 convolution: Compute every kth (2nd) convolution. Functionally similar to pooling
 - Fully convolutional: All convolutional layers, except for output layer
 - Batch norm: Normalize based on batches. Helpful for deeper networks
   - Have multiplier and additive value as a learnable parameter
   - Batch norm should be turned off if not in training
   - Can use batch norm instead of normalizing numericals
 - Boosing intro
 - Resnet as boosting
   - Resnet forward: Input + some actionation of input
 - Class activation maps: Matrix showing high activation cells in input


 - Transformer architecture for machine translation

### TODO 
 
 - colah understanding neural networks
 - wildml lstm
 - Resnet

