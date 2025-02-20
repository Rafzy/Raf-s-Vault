
# Introduction

Seq2seq models -> deep learning models

How a seq2seq model works:
It takes a sequence of words, and outputs another sequence of items, so an example would be neural machine translation, where it takes a sequence of words in one language, and outputs a sequence of words in another language.


# Under the hood

Seq2seq is a model that uses an [[Encoder-Decoder]] architecture

- **Encoder**
	Encoder processes each item in the input, compiles them, and outputs a vector that represents the sequence (Called the **context**)

- **Decoder**
	Receives the context sent by the encoder, and produces the output sequence item by item

- **Context**
	Context are in a form of vectors, in the case of machine translation. We can set the size of the context vector when we set up our model. It's the number of hidden units in encoder [[RNN]]

==Encoders and decoders tend to be both RNNs==


