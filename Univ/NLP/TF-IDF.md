
> Short for Term Frequency-Inverse Document Frequency, it shows how important a word is within a document


1. Term Frequency
	Measures on how frequently a term appears in a document
	Formula:
$$
TF(t, d) = \frac{N(t)}{T(d)}
$$
	N -> Number of times t appears
	d -> Total number of terms in document d

2. Inverse Document Frequency
	Measures how important a corpus is across all documents in the corpus
$$
IDF(t, D) = \log\left( \frac{N}{|\{d ∈ D : t ∈ d\}|} \right)
$$
	N -> total number of documents in the corpus D
	$|\{d ∈ D : t ∈d \}|$-> is the number of documents where term t appears

3. TF-IDF Formula
	Basically multiply each IDF to the percentage
$$
TF-IDF(t, d, D) = TF(t, d) . IDF(t, D)
$$


