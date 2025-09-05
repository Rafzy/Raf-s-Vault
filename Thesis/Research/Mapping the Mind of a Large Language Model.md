
Source:
[https://www.anthropic.com/research/mapping-mind-language-model]

# Summary

This research aims to better understand the inner workings of AI models, namely LLM models. This research marks the first detailed look inside a modern, production-grade language model

## The Core Problem

AI models have an inherent "Black box" nature to it, where we don't really understand the inner "thoughts" of an AI model, this is especially true for bigger, more complex models like LLMs.

Because of this, it's difficult to trust models to be safe, reliable, and won't produce harmful, biased, or untruthful responses

 Our first instinct might be to examine neuron activations, but doing so isn't as helpful because concepts is represented across many neurons, and each neuron can be involved in representing many concepts.

## The solution: Dictionary Learning

General 

Anthropic utilized a technique called [[Dictionary Learning]] which involves ==Matching patterns of neuron activations== called "features", to human interpretable concepts, by isolating neuron activations that recur in different contexts.

This allows an internal state of the model to be represented in terms of a few active features instead of many active neurons.



