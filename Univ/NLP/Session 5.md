# Classification & Logistic

- Classification vs Generation
- Generation
	- Summarization
	- Chatbot
	- Expert System
- Classification
	- Sentiment analysis


## Generative and Discriminative Classifiers

- Naive bayes -> Generative Classifier
- Logistic Regression -> Discriminative Classifier
- A generative model would have the goal of understanding what dogs would look like and what cats look like
- A discriminative model, will try to distinguish the classes (Without learning much about them)
- Generative models are usually preferred because of it's flexibility


## Logistic Regression

>An instance of supervised classification in which we know the correct label y for each observation x

Logistic has two methods:
- Linear
- Non-linear

Three components used while training logistic regression:
- Activation Function -> Compress the data
- Optimizer
- Loss Function -> Compute the model's performance


# Gradient Descent

>Gradient descent is an optimization algorithm widely used in machine learning to minimize a loss function, which measures how well a model's predictions match the actual data. The primary goal is to find the set of model parameters (weights and biases) that minimize this loss function, thereby improving the model's accuracy.


**How Gradient Descent Works:**

1. **Initialization:** Start with initial guesses for the model parameters. These can be random or set to zero.
    
2. **Compute the Gradient:** Calculate the gradient (partial derivatives) of the loss function with respect to each parameter. The gradient vector points in the direction of the steepest increase of the loss function.
3. **Update Parameters:** Adjust the parameters in the opposite direction of the gradient. This is done by subtracting the product of the learning rate and the gradient from the current parameters:
4. **Iterate:** Repeat the computation of the gradient and parameter update until convergence, which occurs when changes in the loss function or parameters become negligible.
    

**Types of Gradient Descent:**

- **Batch Gradient Descent:** Uses the entire training dataset to compute the gradient. It's accurate but can be slow and computationally intensive for large datasets.
    
- **Stochastic Gradient Descent (SGD):** Uses one training example at a time to compute the gradient. It introduces randomness, which can help escape local minima but may lead to a noisier convergence.
    
- **Mini-Batch Gradient Descent:** A compromise between batch and stochastic methods, it uses a small subset (mini-batch) of the training data to compute the gradient. It's widely used due to its balance between efficiency and convergence stability.

# Regularization

> Regularization -> Penalize large weights

Two common ways to compute this regularization terms

- L2 Regularization (ridge regression) is a quadratic function of the weight values, named because the square of the L2 norm of the weight values. The L2 norm is the same as the Euclidean distance
- L1 Regularization (Lasso regression), Linear function of the weight values. Named after the L1 norm. The sum of the absolute values of the weights, or Manhattan distance


# Text Classification

Workflow
![[Pasted image 20241009101623.png]]

