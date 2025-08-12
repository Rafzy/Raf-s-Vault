==force activating neurons for certain inputs==
finding deterministic patterns in LLM logits conditioned on certain inputs

abstract ideas
- testing LLM memorization abilities
- native tool usage in LLMs
- LLMs for creative works


# Force activating neurons for certain inputsppar

From anthropic research paper

"When certain inputs are active, it activates certain groups of neurons"

We want to find certain patterns of how llms think by dissecting the llm.
We check neurons that isn't activated for certain inputs, and add it to the loss function, but then the loss gets rlly sparse


# Finding deterministic patterns in LLM logits conditioned on certain inputs

Find the limit of top k logits in the normal distribution


## Testing LLM memorization abilities

How does the neuron structure and size determine it's memorization ability, and how do we quantize that


## Native tool usage in LLMs

In regular nn, each neuron layer passes through the output to the next layer until it reaches the output layer


## LLMs for creative works

End goal: we're trying to make an LLM more creative.

We just modify the top K, the more it increases the more variance we have



