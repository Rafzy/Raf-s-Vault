
# Low Rank key attention

The basis theory:
We can reduce the dimension of keys while keeping the attention quality while reducing the computational cost

Literature review:
[[2406.02542] Loki: Low-rank Keys for Efficient Sparse Attention](https://arxiv.org/abs/2406.02542)
[[1706.03762] Attention Is All You Need](https://arxiv.org/abs/1706.03762)
[[2006.04768] Linformer: Self-Attention with Linear Complexity](https://arxiv.org/abs/2006.04768)
[[2310.01082] Linear attention is (maybe) all you need (to understand transformer optimization)](https://arxiv.org/abs/2310.01082)
[Customizing the Inductive Biases of Softmax Attention using Structured Matrices | OpenReview](https://openreview.net/forum?id=Roc5O1ECEt&noteId=ixBhCzc186)


## Loki: Low-rank keys for efficient sparse attention

In this paper, they found out using PCA component analysis that 90% of the variation in key vectors data is captured by 80 dimensions out of the total 128 total dimension in key vectors. This means that only 80 dimensions out of 128 is "relevant".

This paper introduces a method where we exploit that intrinsic dimensionality by using PCA to reduce computational cost while keeping attention quality.


# Interpretability of AI

"How does AI think?"

Literature Review:
https://www.anthropic.com/research/tracing-thoughts-language-model
https://transformer-circuits.pub/2025/attribution-graphs/biology.html
https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html

# Testing memorization abilities on newer architectures

Literature review:
https://arxiv.org/pdf/2505.24832


## Attribution graph Github

https://github.com/safety-research/circuit-tracer


Interpretability of 