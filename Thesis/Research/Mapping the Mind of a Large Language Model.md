
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

## Scaling Up

Dictionary learning was successfully applied to smaller "toy" language models, revealing coherent features for simple concepts like uppercase text, DNA sequences, and programming syntax (Mostly still concrete features).

The main challenge is scaling up this technique to large AI language models (Like a legitimate production grade model), and anthropics successfully overcame this challenge by applying a scaling law philosophy.

They extracted millions of features from the middle layer of claude 3.0 Sonnet, providing a "rough conceptual map" of it's internal states

## Nature of Identified Features

- Features can be concrete or abstract
- Multimodal and multilingual (For example, the feature for "golden gate bridge" activates in both english mentions and other languages, and it also activates for images of the bridge)
- Conceptual organization: The internal organization of these concepts within the AI somewhat corresponds to humans notion of similarity, for example features "Close" to "Golden gate bridge" includes alcatraz island and the 1906 Earthquake. This "similarity" in features may explain an LLM's ability to make analogies and metaphors


## Measuring features "Closeness"

We can somewhat measure the "closeness" of this features based on which neurons appear in their activation patterns. This allows us to identify features that are conceptually related within the AI model's internal organization

More examples:
Features near an "inner conflict" concept were found to relate to relationship breakups, conflicting allegiances, logical inconsistencies, and the phrase "catch-22"

