#learn

# 3Blue1Brown's Video

Reference:
https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=CfZltQbE06uCBmYC

## Transformers





## Attention Mechanism

>what does attention mechanism actually do?

Attention mechanism allows for all of the embeddings in a text to communicate with each other, which may give extra semantic or syntactic information to a word, and it calculates what it needs to add to the generic embedding which moves it to a more specific direction of that word that contains more information specific to the context


Let's take a simple example of embeddings communicating with each other, like a noun being modified by the adjectives in front of it
for this to work, let's imagine the noun having to ask: "are there any adjectives in front of me?"
And the adjectives in front of the nouns (if any) would be able to answer that question "Yes, i am an adjective!"
(keep in mind that in the initial word embeddings, they also contain information regarding the position each of the words in some way).

We can do this by using what's called a **Query Vector** which is typically much smaller than the embedding vector.
To get this vector, we multiply a **Query Matrix** which also contains parameters that the model can tune in training, with the embedding matrix. We then do this for each token, which results with each token having and embedding vector, as well as a query vector.

![[Pasted image 20250310170757.png]] 


We can imagine that this query matrix multiplied with the embedding, is able to create a vector that somehow encodes the notion of it being a noun, and it is looking for an adjective. 

(This might not be the exact thing the model is doing under the hood, since it's really hard to track what the parameters inside the query matrix is doing while being multiplied with the embedding vector, but it's good to take a guess of what it's doing)

After that, we utilize another vector called the **Key Vector**, similar to query vector, we multiply a **Key Matrix** which also contains parameters to each embedding, resulting in key vectors for each token. We can then imagine these key vectors potentially answering the Query vectors, and that somehow the Key matrix encodes the notion of tokens being adjectives at certain positions etc.

The attention mechanism will then "match" the query vectors and key vectors, with both of them being more aligned means that the key of a certain token is properly answering the query of another token (we achieve this by calculating the dot product of each combinations of keys and queries)

![[Pasted image 20250310171533.png]]


![[Pasted image 20250310171600.png]]

