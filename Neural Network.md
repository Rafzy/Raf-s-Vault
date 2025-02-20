#machinelearning
# Rough introduction

Neural network kind of simulates how the brain works, it's architecture is a collection of nodes and vertices that connects each node to all of the nodes in the following layer.

![[ChenRudin.jpg]]


what do the nodes and vertices represent? how does the value in each node change the following node through the vertices?

The first layer of the node usually represents the input for the model (for example pixels for an image). And each node contains a value called it's **activation** between 0 and 1. for example, if the input is an image, the activation value may represent how bright the pixel is. How the activation value represents the input or the output of the model will vary between applications depending on how the programmer implements the architecture.

Although there should be a standard procedure for common tasks like image processings, etc. 

The layer of each node is affected by the nodes preceding it. The pattern of the first layer will influence the next layer of nodes to fire up their activation values, and the pattern of that layer of node will affect the next, until it reaches the last layer where it will represent the probability of what the model predicts the output to be.

So basically, this architecture just slaps on a bunch of layers of nodes, and hope that the pattern affecting the next layer will end up predicting what the output is.

How does the layer of nodes affect the other?

---

each vertex that connects all of the nodes into one of the node in the next layer contains values called weights, 

![[Pasted image 20250219130600.png]]

the weights can be random at first, but the model can tweak these weights when it's training (more on this later)

Now we can sum up the total of the activation layer multiplied by each of the weight for the vertex, by doing this, we can extract certain informations from the input.

for example whether some bright pixels exists within a certain area, and how activated the node in the next layer represents how true that statement is.

because the activation value should be between 0 and 1, we put in the total sum of the nodes and the weights to an **activation function** one common example is a sigmoid function that squeezes any range of number to be between 0 and 1

The sigmoid function will only estimate **how positive** the weighted sum is

we can also add or subtract a constant called the **bias** if we want the function ==to only activate when the weighted sum is above or below some value== (bias for inactivity)

---

All of this happens for every node and vertices in all of the layers following the first one.

So, the model learning is just tweaking all these values (weights and biases) until it finds the right combination that it can correctly predict and do the task we want the model to do (predicting handwriting for example)

It's really hard to really guess what the weights are biases doing under the hood, although it's really beneficial to truly understand how the particular architecture used works and makes it possible to modify the architecture so it may perform better at specific tasks

we can use this notation to represent connections between nodes and vertices from one layer to another

![[Pasted image 20250219132622.png]]

$a^{(0)} \to$ preceding layer 
$a^{(1)} \to$ next layer

==even though each neuron does contain numbers, it's better to think of them as functions, that take in each values and weights from the layer before, and spits out a number between 0 and 1==

so the real question is <u>how actually does the mode learn?</u>
How does the model tweak each parameter so that it can correctly identify or predict whatever it's supposed to predict?

# Training (Gradient Descent)

So now we know what the model does under the hood when it's training, it tweaks all the parameters it has (weights and biases) so that the combination of  all of those parameters may predict what the model is supposed to predict.

but how does the model achieve that in a finite amount of time?

For the model to learn, we need to train them using **labeled data** data with the input along with labels denoting what the output should be, and when showing dozens of training data, the model will tweak those parameters until it can generalize beyond the training data.

We can test whether the model can generalize properly by showing it new unseen data called the **test data**.

Considering all this, we can conclude that when the model trains, our goal is to just essentially finding the minimum errors when training the model (wow calculus).

==remember that we can assume that each neuron acts as functions==

essentially, when we're 