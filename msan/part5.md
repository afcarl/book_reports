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