
# Neural Networks & Neural Language Models

>Most LLMs are based on Transformers (GPT, Bert)

## Fully Connected Neural Network

Consists of three components:
- Input layer
- Hidden layer
- Output layer

Droupout -> Reducing the number of connected nodes

The thing with FCNN is that each input must be independent which is not true for most LLM tasks or inputs


## Time Series Model

Similar to Neural Network, but each node is affected by the next node and the past node.

Example: LSTM (Long Short Term Memory)


## Machine Translation (MT) Sequence to Sequence

For example we have a source and target (English to Italy)

English: I eat apple
Italy: something

Each word is attached with a weight, but as the input words become longer, the weight of the first input can become very saturated or insignificant

we can solve this by using [[Attenion]] which basically works by stacking every weight, so each weight can be easily accessible.


## Encoder and Decoder

The reason why they're called encoders and decoders, is because in encoder, we calculate the weight, and get the attention

In decoder, we "decode" the target based on the weights

