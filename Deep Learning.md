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

initially, when we train the model, we give it randomized parameters, and of course, as we would expect the model would print out trash output.

To basically tell the model how far off it is from the correct output (ground truth), we use what's called as **loss function** which basically calculates how wrong the model is from the ground truth. (Most common is Mean Squared Error)

---

==why can't we simply just subtract the model's output with the ground truth?==

while that is the simplest approach to measuring how far off the model is to the correct output, it may not be ideal for specific problems, like regression problems where outliers are critical, MAE or MSE are used because they penalize errors more heavily

Or for classification, cross-entropy loss is more preferable because it measures the divergence the predicted output and true class labels, aligning with probability theory

---

So what we do then is take the average loss of all the training data and it will shoot out how wrong the model is in average. (the average loss function for all of the training data point is then called the cost function.)

> but just telling the model how bad it is won't help anything (hear that dad), the model has to be able to know how to change the parameter so that the loss gets minimized

Let's imagine the loss function as a simple function (one input and one output).

In calculus, we should be able to find the global minimum easily by using differential calculus, but for a function as complex as this, it's not as easy since the graph may be more complex that a simple polynomial function. 

![[Pasted image 20250220115011.png]]

So, a more flexible tactic is starting out with any point in the graph, and we can decide which step we should make so that the output is lower, to put it simply, we find the **slope** of that point in the function, if the slope is positive, we go to the left, and we go right if the slope is negative.

One cons of this is that we may be stuck in a local minimum instead of the global minimum since we can fall down to any of the valley in the graph depending on where we start out

![[Pasted image 20250220115231.png]]


this idea can carry over in a more complex space, for example if we bump up the complexity of the function into taking two inputs instead of one, and this idea still holds true (think of a ball that's rolling down a hill)

in multivariable calculus, there's a concept called the gradient of steepest increase where finding the gradient gives us the direction which direction to increase the function. taking the negative of this gradient will show us the direction to quickly decrease the function

![[Pasted image 20250220115731.png]]

so we can do this even for highly complex functions of the loss function with thousands of inputs

![[Pasted image 20250220121144.png]]

As we know, nudging the weights and biases so that the loss function is as minimum as possible means that the model will be able to predict more accurately.

The algorithm for computing the gradient efficiently is called **backpropagation** which will be covered later.

So to conclude, what it means by the model learning is just ==minimizing the loss function ==

And the process of minimizing said loss function is called **Gradient Descent**

We can also imagine the process of gradient descent as telling us which connection in the model carries more weight when it's changed compared to the others, and in which direction it should be nudged while training

![[Pasted image 20250220121756.png]]


> which basically tells us that there may be some parameter where the change carries more bang for your buck when we nudge it in the right direction

 Actual depiction of hallucination in deep learning
![[Pasted image 20250220123819.png]]





revision: the model changes all the weights and biases based on the **cost function** which is the average loss of all the training examples. So the model has to go through each example before modifying the parameters for each step.

# Backpropagation (How the model learns)

>How does the loss functions adjust the weights and biases for every single step for the training data?

Let's imagine the initial training of the model where the weights and biases, and effectively the output is also random.

and for this example, let's look at **one training example instead of a whole step**

after obtaining the output, we'll look at the final layer and we'll get the loss function for that one data point, and we'll see how much the output deviate from the actual answer (how much a neuron that's not supposed to be activated should be decreased, and how much a neuron that's supposed to be activated should increase)

remember that we can't directly change the activation neurons, but it's useful to keep track of how we want those neurons to change so that it looks a bit closer to what the actual output should be 

![[Pasted image 20250220170414.png]]


let's focus on the one neuron whose activation we want to increase.


remember that the activation value for that neuron is the result of the total sum of all the activation of the neurons before multiplied by the weighted sum plus the bias, which then gets inputted into an activation function

so to increase the resulting neuron, we can do three things:
- increase $b$
- increase $w_{i}$ (the weights)
- change $a_{i}$ 


consider when we want to increase the weights, and we can imagine that increasing the weights that connects the previous layer with brighter neurons (higher activation function) will have more impact when we want to increase the activation of the resulting neuron.

![[Pasted image 20250220170930.png]]

remember that in gradient descent, the resulting gradient vector not only tells us which direction the weight should be nudged, but also which weight or bias that will bring us the most impact when we do nudge them (based on the scale of how much it should be nudged)

this somewhat is reminiscent of the phrase:

> neurons that fire together, wire together



we can also change the neurons before it to affect the resulting neuron's activation, in this case we can increase the neurons that are connected to positive weights, and decreasing the neurons that are connected to negative weights


![[Pasted image 20250220171527.png]]


remember that we cannot directly influence the activations of the previous layer, but again it's useful to keep note of **how** we want them to be changed

and remember that we're looking at a single result of the final layer, namely representing 2. There are other neurons that we want to be dimmer, and changing the neurons and weights to affect the "2" neuron will also affect the other neurons, and so the model will have to find the right balance of tweaks. 

to achieve this, the "desire" (how it wants the previous neurons or weights to change) of the output 2 neuron will be added to the "desire" of the other neurons

![[Pasted image 20250220171922.png]]this is where the idea of propagating backwards appear, after adding all the desires of the last layer, we get a list of nudges for the second to last layer, and we can repeat the same process to the previous layer, going backwards.

and remember that this is only the result of one training example of how it wants to nudge the parameters, we will also have to listen to the other training examples

so we go through all of the training examples, each with it's own list of nudges for all of the weights, and we'll average them all to get the final list of nudges.

![[Pasted image 20250220172310.png]]


and so, the final list of the average of all the nudges for each of the training example, **is the negative gradient we discussed before.** (or at least something proportional to it)


it's computationally expensive to add up every training example's influence every step, so here is what's done

- shuffle the training examples
- divide them into mini batches
- compute a gradient descent step for one mini batch

==this is not the fastest path to the lowest loss function, but it's computationally effective==
==and this technique is called **stochastic gradient descent**== 


# Backpropagation calculus

>Yeah we bout to get mathematical

Let's imagine a very simple neural network, where each layer has only 1 neuron each
this structure is comprised of three weights and biases, and four neurons

**![[Pasted image 20250223202448.png]]**

How sensitive are the weights and biases to the cost function

