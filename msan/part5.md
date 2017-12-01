# Notes

## Part 5

### Resources

 - [Wiki](http://forums.fast.ai/t/wiki-lesson-5/)
 - Towardsdatascience.com

### Collaborative filtering

 - w/ movie lens data set
   - UserID, movieID, rating, timestamp
 - Benchmark: Matrix factorization
   - Intro to matrix factorization
   - Latent factor description
   - QR factorization, w/ SGD
   - Embedding sizes: Large enough, not too large

User constants

 - Per user & per movie biases
 - Broadcasting: Add vector and matrix by duplicating vector

- Tip: Force units to re-scale to output scale. This way, units don't need to learn to scale output

 - Intro to calculus
   - Jacobian / Hessian matrices

 - Description of Stochastic Gradient Descent
 - Description of momentum: If gradient is in same direction for successive epochs, increase learning rate
 - Intro to Adam: Exponentially weighted moving average
 - Linear interpolation

### TODO

 - Read adam paper