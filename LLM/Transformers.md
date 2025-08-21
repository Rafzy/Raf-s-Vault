> Transformers are basically glorified autocomplete AI model

Transformers are a specific implementation of neural networks, and is used in LLMs nowadays like ChatGPT.
Transformers can be used outside of LLMs as well, like a text-to-voice model, or text-to-image models.

The original transformer is introduced in 2017, from a paper called "Attention is all you need", which is originally invented for the specific use case of translation.
[https://arxiv.org/abs/1706.03762]

**The general data flow in a transformer**
Embedding -> Attention -> MLPs -> Unembedding

# Inside a transformer

Before processing the input and ultimately generating the output, the input is separated into several chunks (Called tokens).
Each of these tokens are associated with vector values, which somehow encode that word's meaning

Then these vectors are passed through an attention block. The attention block basically allows the vectors to talk to each other, and give context from one token to another. Because in text input, some words can mean differently depending on the context. the vectors then gets updated accordingly now with added context to their meaning.

Then these vectors goes through what's called a multilayer perceptron in which all vectors goes through the same process in parallel (Will be explored later)

After going through many repetition attention blocks and MLPs, we hope that the prediction for the next word is baked into the last vector of the sequence (Somehow)

# Needed background knowledge

## Word embedding

This is the step that associates each token into a vector value. This vector value directly correlates into the "meaning" of said token. This is explained more in [[Word2Vec]].
these word embedding is part of the total weights of the transformer, although a smaller part of the tons of total weights in transformers.

embedding utilizes what's called embedding matrix, which every column corresponds to a word's vector value.

Good note:
The dot product of two vectors corresponds to how well they align

Aside from encoding the meaning of the word, the vector must also contain the positional information of that word in the input. This is important for the attention block later.

The network can only process a fixed number of words at a time, specified by what's called the **Context window**. If the overall conversation exceeds the context window, the model might seem to lose track of the conversation it's holding

## Unembedding

I mentioned that the next predicted word ends up accumulated in the last vector of the context, We then use what's called an unembedding matrix that we multiply with the last vector to create a resulting vector, which values corresponds to every word that was available in the embedded word, and each value gets put through a softmax which makes it into a distribution 

The number of rows corresponds to the number of words in the vocabulary, and each row contains the same length as the embeddings length


## Softmax

Standardization technique, takes in vector values, and outputs a probability distribution (All adds up to 1, and all values are positive.)

![[image-169.png]]


**Temperature** -> The extent to which we give the lower values more weight, thus gives a more "distributed" distribution (If T is small, then the maximum value will dominate over the distribution). Higher temperature allows the model to "choose less likely words". Usually the max value for the temperature is set to 2, so the model doesn't spout bullshit if the temperature is too high

**Logits** -> The raw unembedded matrix before going into normalization


# Attention in transformers

We know that each token is associated with it a token as well. The token contains not only the literal meaning of the word, but also the semantic meaning as well. However, individual words by themselves aren't enough to carry out the whole meaning of the input sentence, sometimes words are affected by other words in the sentence to give it context.
Example: river "Bank" is different in meaning than regular "bank" (Money bank)

Attention mechanism aims to adjust these vector embeddings to contain richer more contextual meaning based on the other tokens as well.

Each token has another vector associated with it called the **Query vector** We can imagine this vector as a way for that token/word to ask a question to other tokens. For example a noun might ask "Are there any adjectives in front of me?".
To get this **Query Vector**, we multiply the embedding vector with what's called as the **Query Matrix** which values are all tunable parameters. 
We do this to all of the embeddings in the context, and so each token is also associated with a **Query Vector**.

Similar to query vectors, we also associate each embedding with **Key vectors**, which we can imagine as "Answering" the questions of the query vectors. Similarly, we get key vectors by multiplying each embedding with a **Key Matrix** which is also composed of tunable parameters.

We can imagine both Query and key vectors as mapping the embedding vectors into a smaller dimensional space, only carrying over information that's important for "Asking questions" and "Answering" them

We think of the keys as matching the queries whenever they closely align with each other.

We can do this by computing dot product for each possible key query pair.


![[image-170.png]]


we can see that the word "Fluffy" and "Blue" key vectors align well with the word "Creature" query matrix, same goes with "verdant" and "Forest".

The more "Positive" the dot product is, the more related they are to each other, and the more "Negative" the dot product is, the more unrelated they are

Then for each columns, we need them to be between 0 and 1, and for all of them to all add up to 1 (Use softmax!)

We then fill in the grids with the new normalized values, we call this grid the **Attention pattern**

During the training process, it's more efficient if we simultaneously ask the model to try to predict every possible next words for even for the subsequent words. This is useful because what's effectively before a single training example acts as many training examples

![[image-171.png]]

But from the perspective of our attention pattern, we never want the later words to affect earlier words, as to not give away the answer for what might come next. To do this, we somehow need to set these values as zero without affecting the softmax output

![[image-172.png]]

We can achieve this by, before applying softmax, we set those values into negative infinity, which after applying softmax will automatically be zero values. This approach is called **Masking**.

Also notice that the attention pattern's size will be the squared of the context size, this is why the context size might be the biggest bottleneck for a lot of application.

### Updating the embedding values

*Most straightforward way*
The most straightforward way to update the vector values is to use a third matrix called the **Value Matrix**. We multiply this value matrix to the embedding of the adjective word, and we obtain the **Value matrix**, this value matrix then we add to the embedding of the noun, thus updating the embedding value of the noun, now containing updated information from the adjective in front of it.

Note:
==Notice that the value vector must live in the same high dimensional space as the embedding vectors in order for this to work==

We can imagine value vectors as this:
"If this word is important in updating the meaning of another word, what exactly should be added to the embedding of that word for it to reflect the new meaning"

So, looking back at the attention pattern
We first multiply each embedding with the value matrix to then get multiple value matrix. Each value matrix will then be multiplied to the softmaxed dot product from the attention pattern. These will act as "weights" for the value matrix, depending on how relevant the associated value vector word is.

![[image-173.png]]

We then do this for each word, adding the weighted vector values to the embedding of each word.

![[image-174.png]]

After doing this for each embedding and updating each, we call this as executing **one head of attention**

## Cross attention

Cross attention is used when models work with two distinct data, like two texts with different language, or audio input of speech, and an ongoing transcription.

It works almost the same exact way, but the attention pattern is built with two of those distinct data instead of the same string of data.

![[image-175.png]]


# Multi-headed attention

