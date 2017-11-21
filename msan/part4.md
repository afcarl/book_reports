# Notes

## Part 4

### Resources

 - [Wiki](http://forums.fast.ai/t/wiki-lesson-4/)
 - Differential learning rates
 - Links
 - SGD w/ restarts

### Planning

 - This lesson: high level
 - Future lessons: Diving into glue code


### Notes

Drop out

 - Intro to dropout layers
 - W/ max pooling, outputs aren't changed very much
 - Set of dropped out activations varied for each mini-batch
 - Inference doesn't get dropout, train only
 - PyTorch normalizes remaining activations, so net weight to next layer is the same
 - Default p=.25 for first layer, .5 for inner layers


Architecture
 - Linear: Should have first linear layer early in model
 - Relu shouldn't be used in last hidden layer. Softmax would mess up
 - Softmax: Should have negative values as input. Might want to use linear lear before softmax
 - Dropout: Good as early (second) hidden layer, particularly after linear

Variable types

 - Continuous, discrete
 - Different lists for categorical and continuous variables
 - Suggestion of using year / month / day as continuous
 - No recommendation for binning
 - Change categorical to pandas categorical
 - Change continuous to flat32
 - Default to categorical variables
 - Seasonality: Can replace date w/ day of week, day of month, year, encoding, month end, month start, quarter end, quarter start
   - Should have column w/ appropriate seasonality frequency

Data transformation

 - Should scale everything to 0 to 1
 - Deal w/ nulls

Validation sets

 - Predict next two weeks of data sales


Metrics

 - Know your metrics


Categoricals

 - Embedding for categoricals
 - Heuristic for embedding
   - Variable and variable cardinality
   - Always have UNK in embedding
   - Dimmensionality: Cardinality / 2, but not larger than 50
   - Embedding initializiation: Random / pre-trained
   - OHE causes individual levels to be associated w/ only 1 weight

## NLP

 - Less mature than CV

Language modelling: Setup

 - Predict next word
 - lang_model-arxiv.ipynb
 - Build language model first, use that for NLP tasks
 - Tips for language generation not covered
 - Demark different parts of text w/ tags (e.g. `<TITLE> title <SUMMARY> summary sentences`)
 - No stemming or lemmatizing
 - bptt: ?

Libraries

 - torchtext: PyTorch's text module
 - Field: Torch's text input wrapper, w/ some preprocessing steps

Language model: Model

 - Embedding sizes in [50, 600]
 - Use Adam optimizer w/ betas = (.7, .99)
 - Many dropouts
 - Use clip, to avoid runaway / issues w/ high learning rate

Pre-trained embedding layers

 - Heuristic was pre-trained embedding didn't help alot

Collaborative filtering

## Next time

 - Fundamentals
 - Layers