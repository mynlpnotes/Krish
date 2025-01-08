# Self attention layer working

* Also known as scaled-dot product attention, is a crucial mechanism in the transformer architecture that allows the model to weigh the importance of different tokens in the input sequence relative to the other
* &#x20;The cat sat ⇒ this will be converted into vectors
* When this vectors are passed through self attention layer, the output obtained here will be another vector and this vector is our contextual embedding
* Embedding layer gives us fixed vector for a word
* This are called contextual embedding because here we are going to take importance of different input tokens for generation
*

    <figure><img src="../../.gitbook/assets/image (163).png" alt=""><figcaption></figcaption></figure>
* Inputs: Queries, Keys and Values&#x20;
* Model will be computing Q, K and V

Query Vector:

* Represents the token for which we are calculating the attention
* They help determine the importance of other tokens in the context of the current token
* Importance:
  * Focus determination:
    * Queries help the model decide which parts of the sequence to focus on for each specific token. By calculating the dot product between a query vector and all key vectors, the model accesses how much attention to give to each token relative to the current token
  * Contextual Understanding:
    * Contribute to understanding the relationship between the current token and rest of the sequence, which is essential for capturing dependencies and context

Key Vector:

* Represents all the tokens in the sequence and are used to compare with the query vectors to calculate attention scores
* Importance:
  * Relevance measurement:
    * Keys are compared with queries to measure the relevance or compatibility of each token with the current token. This comparison helps in determining how much attention each token should receive
  * Information retrieval:
    * Keys play a critical in retrieving the most relevant information from the sequence by providing a basis for the attention mechanism to compute similarity scores

Value Vector:

* Holds the actual information that will be aggregated to form the output of the attention mechanisms
* Importance:
  * Information aggregation:&#x20;
    * Contain the data that will be weighted by the attention scores
    * The weighted sum of values forms the output of self attention mechanism, which is then passed to the next layers in the network
  * Context preservation:
    * By weighing the values according to the attention scores, the model preserves and aggregates relevant context from the entire sequence, which is crucial for tasks like translation, summarization, and more

Input sequence: \["The", "cat","sat"]

Embedding size: 4

Q,K,V ⇒ Dimension - 4

1. Token embedding:

* $$E_{The}$$ = \[1 0 1 0]
* $$E_{Sat}$$ = \[1 1 1 1]
* $$E_{Cat}$$ = \[0 1 0 1]

2. Linear Transformation:

* We create Q,K and V by multiplying the embeddings by learned weight matrices $$W_Q, W_K, W_V$$
* We will do dot operation and CAT and $$W_Q$$ to get Q and so on for V and K
*   We will initialize weights and then using back propagation it will be learned

    <figure><img src="../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>
* &#x20;We are initializing weights as I here
*

    <figure><img src="../../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>

3. Compute Attention Scores:

*

    <figure><img src="../../.gitbook/assets/image (162).png" alt=""><figcaption></figcaption></figure>

4. Scaling:

* We take up the scores and scale down by dividing the scores by $$f(x) = x * e^{2 pi i \xi x}$$
