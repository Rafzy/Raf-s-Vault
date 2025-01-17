#nlp

# Syntactic vs Semantics

> Syntactic and Semantics represent two fundamental layers of language understanding in which machine tries to replicate when processing human language

## Syntactic (Syntax)

Syntax refers to the rules that govern the structure of a sentence, and adhering to that rule determines the grammatically correctness of a sentence. So, adhering to the correct syntax means you are using the correct grammars of a sentence. 

 **Syntactic analysis techniques**
- Part-of-speech tagging: assigning grammatical categories (Noun, verb, adjective, etc) to each word in a sentence
- Syntactic parsing: Analyzing sentences to reveal their grammatical structure, represented as a parse tree, this type of syntactic parsing is divided into two categories:
	- Constituency parsing
	  Includes breaking down sentences into sub-phrases or constituents, typically outputs a parse tree, which represents the hierarchical structure of the sentence
	- Dependency parsing
	  Focuses on the binary grammatical relationships between words in a sentence. Each word (except for the root) depends on another word, forming a dependency parse tree.
- Context-free Grammar: 
  CFG represents the syntactic structures with rules that generate all valid sentences in a language.

**Applications**:
- POS Tagging
- Grammar correction
- Machine Translation (Technically combination of syntactic and semantics)

**Problems encountered by Syntactic Analysis**
- Ambiguity
  Because syntactic analysis doesn't understand the underlying meaning behind the words, it may struggle with ambiguity, like words with "double meaning"
- Language specific rules
  Different languages have different structures and rules when it comes to grammar, so it may struggle with multi language parsing
- Complex sentences
  Sentences nested clauses may challenge a syntax parser, more complex algorithm may be needed

## Semantics

Deals with the meaning conveyed <u>behind</u> the words, phrases, or sentences. It focuses on understanding and interpreting the intended message or information in the text.

Key aspects:
- **Word sense disambiguation**
  Determining which meaning of a word is used in a context ("bank" as in financial institution or riverbank)
- **Named entity recognition**
  Identifying and classifying entities in text into predefined categories, like people, organizations, locations, etc. Basically what does an entity name refer to, is it an individual, a group, etc.
- **Semantic Role Labeling**
  Assigning roles to words or phrases in a sentence to understand who did what to whom
- **Coreference Resolution**
  Determining when different words refer to the same entity ("Alice said she would come" - "she" refers to "Alice")
- **Sentiment analysis**
  Detecting the emotional tone behind a body of text.

Semantic Analysis often integrates *lexical semantics* and *vector semantics*.

### Lexical Semantics

>Studies the meanings of words and their relationships of one another within a language, focuses on understanding words individually

**Key concepts:**
- Synonyms (Different words same meaning)
- Antonyms (Words with opposite meanings)
- Polysemy (Single word having multiple meaning)
- Hyponym & Hypernym 
	- Hyponym: Word whose meaning is included in another word ("Rose" is a hyponym of "Flower")
	- Hypernym: A general term that encompasses more specific words ("Vehicle" is a hypernym of "Car")
- Lexical relations (Associations that are formed through a network of related meanings)


| Pros                                                           | Cons                                         |
| -------------------------------------------------------------- | -------------------------------------------- |
| Provides a detailed understanding of word relationships        | Requires extensive linguistic resources      |
| Useful for tasks needing fine-grained-word level understanding | Does not capture context, meanings are fixed |
| Allows creation of word networks for knowledge representation  | Difficult to scale                           |

### Vector Semantics

>Represents words, phrases, or sentences as a vector in a multi dimensional space. This approach captures meaning based on statistical associations from large text corpora

**Key concepts:**
- Word Embeddings
	Techniques like Word2Vec transform words into vector based on co-occurrences in text. Words that have similar meaning will have a closer vector distance
	Example: "King" and "Queen" in the vector space are closer to each other, and share a similar directional relationship with "man" and "woman"

- Contextualized Embeddings
	Models like BERT and GPT use transformers to generate embeddings based on <u>context</u>. Each occurrence of a word in a sentence has a unique vector representation, accounting for context-dependent meanings

- Distributional Semantics
	This approach is based on the distributional hypothesis, which states that words used in similar context tend to have similar meaning
	Distributional semantics is powerful for capturing semantic similarity and can be applied to sentences and documents, enabling NLP models to assess text similarity

![[Pasted image 20241031190455.png]]

(Thanks kennard lol)


## Interplay between Syntax and Semantics

Syntax provides structural framework in a sentence, while semantics fills it with meaning.

**Applications**:
- Machine Translation
  Translation requires understanding grammatical accuracy as well as semantics to preserve the actual meaning across languages
- Speed Recognition and Generation
  Syntax ensures sentences are well-formed, and semantics make sure they make sense


# NLP Models

Models in the field of NLP are generally categorized into **generative** and **discriminative** models. These distinction pinpoints how different algorithms approach language tasks, and for selecting the appropriate model for a specific application

## Generative Models

Generative model aims to capture the joint probability distribution $P(X, Y)$ of the input data X and the output labels Y. With this, the model can generate new data instances that resemble the training data. This means the model can produce or **generate** new text, sequences, or entire documents.

Characteristics:
- [[Joint probability modeling]]
  The model "models" how the data is generated, including both input and output
- **Data generation**
  Capable of generating new, plausible data points similar to the training data. So more training data equals more variation in lexicons that the model can generate.
- Use of bayes theorem
  Can compute the conditional probability $P(Y|X)$ by applying bayes theorem

**Examples**:
- Naive bayes classifier
- Bayesian Network
- Hidden markov model
- Latent Dirichlet Allocation
- Variational Autoencoders
- Language Models

**Applications**:
- Text Generation
- Machine Translation
- Speech recognition?
- Topic modelling


## Discriminative Models

Discriminative models focus on modelling the conditional probability $P(Y|X)$ directly. They are designed to predict the output labels Y given input data X without understanding how the data was generated. 


**Key characteristics:**
- Conditional probability modelling
  Directly models the relationship between inputs and outputs
- Prediction focused
  Aims to find decision boundaries that separate different classes
- Often higher accuracy in classification tasks
  By focusing on $P(Y|X)$, they can often achieve better performance in discriminative tasks

**Examples:**
- Logistic Regression
- Support Vector Machines (SVMs)
- Conditional Random Fields (CRFs)
- Neural Networks
- Maximum Entropy Models

**Applications:**
- Text classification
- Named entity recognition
- Sentiment analysis
- Question answering
- Dependency parsing


# Text pre-processing

Pre-processing data is an essential step not just in the field of nlp, but in most fields of AI. Particularly in NLP, preprocessing involves transforming raw text data into clean and normalized data, suited for analysis and modelling.

Preprocessing aims to reduce noise, handle inconsistencies, etc, so that the model can extract meaningful patterns.

## Goals In Pre-processing

- Reduce Noise
  Text data extracted from real world very often contains irrelevant information that doesn't help with giving the model additional information, like HTML tags, advertisements, user signature, etc
- Standardization
  Text data can vary a lot, like different formats, spelling, structures, etc. With pre-processing we can standardize this data so we feed the model with data that is more uniform
- Improved Model performance
  If we feed the model with clean, standardized data, the model performance may improve drastically, proving why pre-processing step is essential.


## Pre-processing steps

- **Tokenization**
	Tokenization breaks down text into smaller units called tokens (This token can be words, sentences, or subwords)
	- Word tokenization
	- Sentence tokenization
	- Subword tokenization
- **Case Folding**
	Preprocessing step in NLP to standardize data by converting the text into the same case (To lower : bert-based uncase, or uppercase : bert-based cased)
- Stemming/Lemmatization
	Lemmatization and stemming are used to reduce words into their base/root form.
	- Stemming
	  Stemming includes reducing words to their base form by removing suffixes or prefixes. It uses a simple set of rules to strip common word endings, this may lead to non-words
	- Lemmatizing
	  Process of reducing words into their base or dictionary form (Lemma) while considering the context and part of speech. Lemmatization usually result in actual words that can be found in dictionaries
- Stopword removal
	Pre-processing in NLP that involves removing common words that do not carry significant meaning and not useful for text analysis. These words include terms like "The", "is", "in", "at", "on", "and", etc.
- Vectorizing
	Transforming each words into their numerical forms



# TF-IDF

> Short for Term Frequency-Inverse Document Frequency, it shows how important a word is within a document


1. Term Frequency
	Measures on how frequently a term appears in a document
	<u>Formula</u>:
$$
TF(t, d) = \frac{N(t)}{T(d)}
$$
	N -> Number of times t appears
	d -> Total number of terms in document d

2. Inverse Document Frequency
	Measures how important a corpus is across all documents in the corpus
	<u>Formula</u>:
$$
IDF(t, D) = \log\left( \frac{N}{|\{d ∈ D : t ∈ d\}|} \right)
$$
	N -> total number of documents in the corpus D
	$|\{d ∈ D : t ∈d \}|$-> is the number of documents where term t appears

3. TF-IDF Formula
	Basically multiply each IDF to the percentage
	<u>Formula</u>:
$$
TF-IDF(t, d, D) = TF(t, d) . IDF(t, D)
$$


# Naive Bayes

![[image.webp]]


![[image 1.webp]]



# Bigrams

By definition, bigrams are a 