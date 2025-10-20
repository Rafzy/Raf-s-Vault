Source:
https://transformer-circuits.pub/2025/attribution-graphs/methods.html

Publicly available circuit tracer:

# Summary

This paper introduces a novel technique for **Mechanistic Interpretability**, which aims to uncover the underlying computational mechanism of LLMs.

# Introduction

The goats anthropics found a way to trace the thinking process of language models, by tracing the individual steps in a **replacement model**. 

In *Mechanistic interpretability*, we aim to describe the black box nature of language models, anthropic's approach includes a 2 step process (first being identify *features*, the second is describing the processes or *circuits*)

The natural approach is to try to identify each neurons of the model as the building blocks of interpreting the features, but the problem is neurons are often *polysemantic*, meaning one neuron is related to many unrelated concepts. This is because models must represent more concepts than they have neurons 

Some recent sparse coding models can decompose model activations into sparse features.

Anthropic's research involves several key methodogical decisions.

1. **Transcoders instead of SAEs**
	Instead of SAEs (Sparse autoencoders), they extract features using a variant of transcoders.
2. **Cross Layer**
	They utilized cross-layer transcoders, in which each feature reads from the residual stream at one layer and contributes to the outputs of all subsequent MLP layers of the original model.
3. **Attribution Graph**
	 This article focuses on studying "attribution graphs". Attribution graphs can describe the "thinking steps" of a model for a target token. This approach is similar to [https://arxiv.org/pdf/2406.11944]
	 The nodes in the attribution graph represent several things (Active features, token embeddings from the prompt, reconstruction errors, and output logits). The edges of the graph represent linear effects between nodes
4. **Linear Attributes Between features**
	For a specific input, they made it so that the interactions between features are linear. So, they freeze attention patterns and normalization denominators, and use transcoders to achieve the linearity.
5. **Pruning**
	The features found are sparse, but there are still too many features active on a given prompt to reliably create an interpretable graph, so they prune graphs by identifying nodes and edges that contributes most to the model's output at a specific token position
6. **Interface**
	They also designed an interactive interface for exploring attribution graphs.
7. **Validation**
	Since the replacement model used may use different mechanisms compared to the underlying model, it's important we validate the mechanisms we find in attribution graphs. Since the replacement model only gives an approximation of how the original model works.
	They validate by taking the circuits found in the replacement model, and see if they hold for the original model
8. **Global Weights**
	This method also allows for the study of weights of the replacement model ("Global weights) directly, which underlie mechanisms across many prompts.

