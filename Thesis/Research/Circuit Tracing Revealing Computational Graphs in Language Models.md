Source:
https://transformer-circuits.pub/2025/attribution-graphs/methods.html

# Summary

This paper introduces a novel technique for **Mechanistic Interpretability**, which aims to uncover the underlying computational mechanism of LLMs.

# Introduction

The goats anthropics found a way to trace the thinking process of language models, by tracing the individual steps in a **replacement model**. 

In *Mechanistic interpretability*, we aim to describe the black box nature of language models, anthropic's approach includes a 2 step process (first being identify *features*, the second is describing the processes or *circuits*)

The natural approach is to try to identify each neurons of the model as the building blocks of interpreting the features, but the problem is neurons are often *polysemantic*, meaning one neuron is related to many unrelated concepts. This is because models must represent more concepts than they have neurons 

Some recent sparse coding models can decompose model activations into sparse features.

Anthropic's research involves several key methodogical decisions.

1. **Transcoders instead of SAEs**
	They extracted the features using a variant of transcoders. They use this as a proxy for the original model.

2. **Cross Layer**
	They utilized cross layer transcoders, this is big

3. **Attribution Graph**
	