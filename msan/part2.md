# Notes

## Part 2

### Resources

 - [Wiki](http://forums.fast.ai/t/wiki-lesson-2/7452)

### Wiki

 - AMIs for AWS
 - Downloading repo
 - Updating repo
 - Updating conda environment

### Niceties
 
 - Some users will have to update Crestle install 


### Part 1 Review

 - Trained model on data
 - Data structure, e.g. train/cats, valid/cats, train/dogs, valid/dogs

### Learning rate

 - Example finding minimum
 - plot loss vs learning rate (log scale)
 - Find lowest, reduce by 1 order of magnitude
 - Lower learning rate might be more robust / less overfit to training set
 
### Model training

 - Introduction to overfitting
 - **Data augmentation:** increase number of effective samples, decrease number of epochs
 - `learn.precompute=False` will disable pre-compute, making data augmentation worthwhile
 - **Learning rate annealing:** Decrease learning rate and gradient decreases. Pick a learning rate, wait for loss to level out, reduce learning rate by order of magnitude
   - Cosine is common choice for annealing function
   - Restart: Jump up to higher learning rate at regular area, to hop out of local minima. Usually reset on every epoch
   - Cycle mult: Increases the period of successive restart
 - Test time augmentation: Perform random data augmentations, average guesses

 - Models and temp files are saved, it might be worth clearing cache occasionally

### Unfreezing

 - If using pre-trained model, can un-freeze layers as needed. Usually start w/ later (more specialized) layers
 - Can set learning rates by layer. 
 - **Differential learning rates:** For pre-trained model, larger learning rates for later layers

### Metrics

 - Confusion matrix

### Review

 - Enable data augmentation, and precompute=True
 - Use lr_find() to find highest learning rate where loss is still clearly improving
 - Train last layer from precomputed activations for 1-2 epochs
 - Train last layer with data augmentation (i.e. precompute=False) for 2-3 epochs with cycle_len=1
 - Unfreeze all layers
 - Set earlier layers to 3x-10x lower learning rate than next higher layer
 - Use lr_find() again
 - Train full network with cycle_mult=2 until over-fitting

### Dog breed

 - Sample Kaggle competition
 - Kaggle CLI to download data
 - Format data folders
 - View histogram of image heights
 - Test w/ smaller images to get feedback more quickly. Start w/ batches of 64
 - If train validation lower than test validaton, underfitting. Set to a longer cycle length, to allow for better train time fitting
 - Precompute: Cache results for frozen, earlier layers

### Architectures

 - Resnet34
 - Resnext50
### Libraries

 - Fast.ai & PyTorch vs Keras & TF