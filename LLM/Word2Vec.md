#llm

# Introduction

>word2vec aims to represent words or vocabularies as a dense, low dimensional vector values. Words with similar meanings will be close to each other in the vector space


Word2vec is one of the techniques on representing words into vectors, nowadays there are other, better methods, but understanding word2vec gives a good intuition on how to construct word embeddings, etc.


Imagine that we're taking a personality test, and we score each personality traits based on how that personality suits you.
If we plot those personality traits, more traits will represent more information regarding that person.

![[Pasted image 20241213115731.png]]

==Some of the traits are hidden when plotted to get used to not knowing what each dimension represents, but still being able to get value from the vector representation==

This way, we can "compare" different people based on how similar they are in personality, by comparing the vector values of each person, and finding the cosine similarity.

![[Pasted image 20241213115909.png]]


![[Pasted image 20241213115917.png]]


We can and should add more dimensions to capture more information about different traits of each person, with the downside of not being able to plot and visualize as easy as plotting 2 dimensional vectors.
good news though, cosine similarity still works with higher dimensions

![[Pasted image 20241213120134.png]]


So in conclusion:
- We can represent people as vector of numbers
- We can calculate how similar vectors are to each other


# Word embeddings

we will look at an example of trained word-vector (or word embeddings), and start looking at their properties

==word embedding for the word "king"==

``[ 0.50451 , 0.68607 , -0.59517 , -0.022801, 0.60046 , -0.13498 , -0.08813 , 0.47377 , -0.61798 , -0.31012 , -0.076666, 1.493 , -0.034189, -0.98173 , 0.68229 , 0.81722 , -0.51874 , -0.31503 , -0.55809 , 0.66421 , 0.1961 , -0.13495 , -0.11476 , -0.30344 , 0.41177 , -2.223 , -1.0756 , -1.0783 , -0.34354 , 0.33505 , 1.9927 , -0.04234 , -0.64319 , 0.71125 , 0.49159 , 0.16754 , 0.34344 , -0.25663 , -0.8523 , 0.1661 , 0.40102 , 1.1685 , -1.0137 , -0.21585 , -0.15155 , 0.78321 , -0.91241 , -1.6106 , -0.64426 , -0.51042 ]``

we can color code this

![[Pasted image 20241213120533.png]]

And let's compare this word to other words.

![[Pasted image 20241213120613.png]]


"Man" and "woman" are much more similar than either of them to "king"
These vectors capture quite a bit of the information or association of these words relative to each other as well

Some more comparison:
![[Pasted image 20241213120815.png]]


A few things to point out:

1. There’s a straight red column through all of these different words. They’re similar along that dimension (and we don’t know what each dimensions codes for)
2. You can see how “woman” and “girl” are similar to each other in a lot of places. The same with “man” and “boy”
3. “boy” and “girl” also have places where they are similar to each other, but different from “woman” or “man”. Could these be coding for a vague conception of youth? possible.
4. All but the last word are words representing people. I added an object (water) to show the differences between categories. You can, for example, see that blue column going all the way down and stopping before the embedding for “water”.
5. There are clear places where “king” and “queen” are similar to each other and distinct from all the others. Could these be coding for a vague concept of royalty?



## Analogies

One of the incredible property of embeddings is the concept of analogies. We can add or subtract word embeddings and arrive at a meaningful result.
One formula "king" - "man" + "woman" results in:

![[Pasted image 20241213121302.png]]



# Language Modeling

One of the most popular example of NLP application that we use almost daily, is a next word prediction feature in our smartphone keyboard.

This task can be addressed by a *language model*. A language model takes a list of words, and attempt to predict the word that follows them.

The model takes in the input words, and list out a list of suggestions for possible words that can come next.

![[Pasted image 20241213125909.png]]


Early neural network models will work in three steps:
- The model will look up the embeddings for each of the input words
- The model will then calculate predictions for the next possible words based on those embeddings
- The model will then project to output vocabulary, and it will possibly take the


## Language Model Training

Good thing about training Language models, we have an abundance of text dataset (Books, articles, etc).

Words get their embeddings by us looking at which other words they tend to appear next to, these are the mechanics of that:
- Get lots of data (Wikipedia articles, books, etc)
- We have a window (of example three words), that we slide against all of that text
- The sliding window generates training samples for our model

At the start, the window  is on the first three words of the sentence:

![[Pasted image 20241213132242.png]]


We take the first two words to be features, and third to be a label

![[Pasted image 20241213132444.png]]


We then slide our window to the next position, and create the next dataset sample for the three words

We then continue until we have a plethora of pairs of words and a label. And soon after we have words that tend to appear after different pairs of words

![[Pasted image 20241213133736.png]]

Typically models tend to be trained while we're sliding the window, but it's clearer to logically separate the "dataset generation" phase from the training phase.
Aside from neural-network based approaches to language modeling, a technique called [[N-Grams]] was commonly used to train language models.

# Looking both ways

If we want to fill in the last word of a given input text, for example like:

Jay was hit by a ___

The word we would probably guess are words like `bus` or `car`. But what if we add another word after the blank, something like:

Jay was hit by a ___ bus

This completely changes what the word should be in the blank. Words like `red` or `big` is more likely to go into the blank. So we can conclude that words before and after a specific word carry informational value. So accounting for both directions lead to better word embeddings.
Let's see how we can adjust the way we're training the model to account for this


# Skipgrams

When we are generating the data like before, instead of looking two words before the target word or the label, we also look at two words after it.

![[Pasted image 20241213135118.png]]

If we do this, the dataset we're virtually building and training the model against would look like:
![[Pasted image 20241213135142.png]]


This is called a **continuous bag of words** architecture, and is described in one of the word2vec papers.

There is another architecture that also tended to show great results does things a bit differently.
Instead of guessing a word based on it's context (the words before and after it), this other architecture tries to guess the neighboring words using the current word. We can think of the window it slides against the training text like this

![[Pasted image 20241213135917.png]]

This creates four separate samples in our training dataset 

![[Pasted image 20241213135953.png]]

This method is called the **skipgram** architecture, we can visualize the window as doing the following:

- The sliding window will start with the first five words, with the middle word being the input, and the neighboring words becoming the possible neighboring words
	![[Pasted image 20241213141344.png]]
- Then we slide our window to the next position, generating the next four examples
	![[Pasted image 20241213141411.png]]
- After multiple times shifting, we have a lot more examples now:
	![[Pasted image 20241213141444.png]]

## Training Process

Now we will revisit the training process with the dataset we have gathered from the **skipgram** method before. Going through each data sample, we feed the input word into the untrained model. At this point, because the model is untrained, it's most likely that the model will output the wrong word which is to be expected

![[Pasted image 20241213142313.png]]


The model will then output a prediction vector, with probability assigned to each word in it's vocabulary. We know what the correct word it should've guessed, the label/output cell in the row we're currently using to train the model. 

To calculate how far off the model was, we'll subtract the two vectors in an error vector:

![[Pasted image 20241213142434.png]]

We'll then feed the error vector to the model to update it's parameters, it's a little more likely to guess the proper word 'thou' when it gets 'not' as an input

![[Pasted image 20241213142525.png]]

We then proceed to the next sample in the dataset, and the next, until we've covered all the samples in the dataset. One loop of going through the whole dataset, equals one *epoch* of training. We'll train over and over again for a number of epochs. After then we'd have a trained model, and we can extract the embedding matrix from it and use it for any other application


# Negative Sampling

*To be continued*