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