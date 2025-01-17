#nlp 

Joint probability modelling involves creating a statistical model that captures the probability distribution of both input data X, and output labels Y simultaneously ($P(X, Y)$), it represents the likelihood of observing a combination of input features and output labels


**Roles in Generative Models**
Generative models focus on understanding how the data is generated, so by modelling the $P(X, Y)$, the model can:
- Generate new data
  Create new samples that are similar to those in the training data
- Compute conditional probabilities
  Derive $P(Y|X)$ for classification or $P(X|Y)$ for tasks like data imputation

