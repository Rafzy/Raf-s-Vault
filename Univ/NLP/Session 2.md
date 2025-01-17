#nlp 
# N-Grams

> A sequence of N words (A 2 gram is a two word sequence like "please turn" or "your homework", and a 3 gram is a three word sequence, and so on)

The N gram model allows a computer to "autocomplete" a sentence by just the first few words


Example using a min-corpus of three sentences

\<s> I am Sam \</s>
\<s> Sam I am \</s>
\<s> I do not like green eggs and ham \</s>

The bigram probabilities from the corpus:
$P(I | <s>) = \frac{2}{3} = 0.67$ <- The probabilty of I at the start of the sentence
$P(am | I) = \frac{2}{3} = 0.67$ <- The probability of am appearing given I appears
$P(Sam|am) = \frac{1}{2} = 0.5$
$P(</s> | Sam) = \frac{1}{2} = 0.5$

Basically the same as probability like last time, just this time we add in start and end tags of a corpus <- WTF is this past me, write shit down properly next time bruh

Notes:
==$P(AB|B) = P(A|B)$==


## Perplexity

The perplexity (PP For short hehe) of a language model on a test set is the inverse probability of the test set, normalized by the number of words. It is a metric used by NLP to evaluate the performance of a language model. It measures how well a probabilistic model predicts a sample and is commonly used with models like N-gram models, neural language models, etc

$$
PP(W) = P(W_{1}W_{2}\dots W_{N})^{\frac{-1}{N}}
$$

## Unknown words

- We sometimes have to deal with words we haven't seen yet, which are called Unknown words or out of vocabulary (OOV) words. The percentage of OOV open words that appear in the test set is called the OOV rate.


## Generalizations and zeroes

- Sometimes we will encounter phrases we do not have in our training set, the model will incorrectly predict those phrases as zero probability in the test set.
- Those zeroes are a problem for two reason:
	- We are underestimating the probability of all sorts of words that might occur
	- If the probability of any word in the test set is 0, the entire probability of the test set is 0.


## The Penn treebank part-of-speech target

![[{A031A2C3-F144-452A-825B-739D0E1BDF01}.png]]


## Part of speech tagging

>The process of assigning a part of speech or other synthatic class marker to each word in a corpus
