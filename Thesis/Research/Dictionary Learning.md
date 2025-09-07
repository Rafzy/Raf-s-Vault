
> A technique to understand and interpret internal representations of language models

Dictionary learning attempts to find a set of "basis features" or "dictionary elements", that when combined can reconstruct the model's internal activations.

A model's neurons might represent many concepts simultaneously in a tangled way, but we can learn a larger, overcomplete library where each element corresponds to a more interpretable concept.

# How it works

## Sparse Autoencoders (SAEs)

The most common approach to dictionary learning, sparse autoencoders are trained to intermediate activations of an LLM. These autoencoders have:
- An encoder -> Maps activations to a sparse, high dimensional representation
- A decoder -> Reconstructs the original activations from this sparse code

The crucial element is to enforce sparsity, meaning that only a few dictionary elements should be active for any given input, so that each dictionary element captures a specific, meaningful feature.
(For example: A dictionary corresponds to the concept of bridges, golden gate bridge would activate, crossing, etc)
The dictionary typically has many more elements than the original activation dimension (Can be 10-100x larger), allowing it to disentangle mixed representations

## What for 

Dictionary learning is useful for **Interpretability**
So far dictionary learning helps researchers identify what concepts an LLM has learned. 
Dictionary elements may correspond to:
- Specific syntactic patterns
- Semantic concepts
- Behavioral patterns

## Recent applications of this

- Map out features in Claude and other models
- Identify safety-relevant features (like deception or harmful content)
- Enable more precise **model editing or steering**


## Dictionary

The dictionary is essentially a matrix
- Each column is one "element" or "feature"
- Each element is a vector of the same dimension as the **layer we're analyzing**

Dictionaries can represent either concrete features like "Words in quotation marks", "References to jakarta", etc, or more abstract features like "Discussing something negative about a person", "Uncertainty expressions", etc

