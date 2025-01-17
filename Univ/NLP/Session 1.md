#nlp

# Introduction

>NLP is a field in artificial intelligence that focuses in the interaction with humans through natural language. The goal for NLP is for computers to understand, interpret, and generate human language that is coherent, meaningful, and useful

types of nlp tasks
- classification (Deduce an already available text that the model will give a label to) -> IMDB, Amazon, Yelp, spam detection, rating on e-commerce
- Generation (Output actual strings of coherent text) -> ChatGPT, recommendation system, Personal Assistance

<u>Average NLP pipeline:</u>
**Input -> (pre-processing) -> Pool -> Output**
- Input -> Textbook, social media, novel, wikipedia, etc
- Pool -> Statistical based, Neural based

<u>Pre-processing</u>
1. [[Tokenization]] -> Breaks down pieces of text into smaller units called tokens
2. [[Casefoldings]] ->  Process of converting all characters to having the same uniform casings
3. [[Stemming/Lemmatization]] -> Convert words into their base form (Running -> run, ate -> eat, etc)
4. [[Stopword removal]] -> identifies and removes frequently occuring words that are considered to have little value to the context of the text

## Important Buzzwords

1. Corpu(s)/(a) -> Body of text
2. Token -> Small parts of a sentence/word
3. Synthetic -> Refers to how the sentence is grammatically
	- Ex: The car rides a donkey 
	  The sentence above is synthetically correct, but semantically doesn't make sense
4. Semantic -> Refers to the <u>meaning</u> of the sentence
	- Ex: Food good me happy
	  The sentence above semantically makes sense, but incorrect synthetically



# Encoders Decoders

>Encoders and decoders are fundamental components in NLP, especially in sequence to sequence models like machine translation


1. **Encoders**
	Encoder processes the input data and converts it into a <u>compact</u> representation. This representation usually takes a form of fixed-size vector representation that captures the semantic and synthetic information of the input sequence Ex; Bert
	
	There are several types of encoders available:
	1. Recurrent Neural Networks
	2. Convolutional Neural Networks
	3. Transformers
	   
2. **Decoders**
	Neural network modules that generate output sequences from the fixed size vector representation produced by the encoderes