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


