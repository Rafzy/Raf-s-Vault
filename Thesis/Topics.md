

==force activating neurons for certain inputs==
finding deterministic patterns in LLM logits conditioned on certain inputs

abstract ideas
- testing LLM memorization abilities
- native tool usage in LLMs
- LLMs for creative works


# Force activating neurons for certain inputs

From anthropic research paper

"When certain inputs are active, it activates certain groups of neurons"

We want to find certain patterns of how llms think by dissecting the llm.
We check neurons that isn't activated for certain inputs, and add it to the loss function, but then the loss gets rlly sparse

We want to force certain neurons to activate given certain inputs.

end goal: Make the LLM think a certain way (Not through fine tuning)

Ko ocin's notes:
- If certain inputs are expected to activate certain neurons, then those neurons will activate regardless of the input.
- Inputs are arbitrary
- Neural network affects all the nodes of a layer instead of directly a node, nodes that are deactivated don't contribute in the first place
- The output of this approach isn't as significant
- Might work, but to what extent, we don't know


# Finding deterministic patterns in LLM logits conditioned on certain inputs

Find the limit of top k logits in the normal distribution


## Testing LLM memorization abilities

How does the neuron structure and size determine it's memorization ability, and how do we quantize that

Given a small LLM, we give specific information as much as possible.
How good is the memorization ability conditioned on certain data, and the compression ability on those data

Notes:
- Nice idea, but we have to think about how we approach this

## Native tool usage in LLMs

In regular nn, each neuron layer passes through the output to the next layer until it reaches the output layer

Give the LLM an interface to some outside tool. 

Notes:
- Evaluating the label from a certain layer isn't a good idea
- The tool needs to understand how the underlying model works, meanwhile the model is a black box


## LLMs for creative works

End goal: we're trying to make an LLM more creative.

We just modify the top K, the more it increases the more variance we have




Ko ocin's concern:
- HOW?


