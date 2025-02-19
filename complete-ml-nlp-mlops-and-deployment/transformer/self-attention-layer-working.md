# 🟠 Self attention layer working

* Also known as scaled-dot product attention, is a crucial mechanism in the transformer architecture that <mark style="color:purple;background-color:purple;">**allows the model to weigh the importance of different tokens in the input sequence relative to the other**</mark>
* &#x20;The cat sat ⇒ this will be converted into vectors
* <mark style="color:purple;background-color:purple;">**When Embedding vectors are passed through self attention layer, the output obtained here will be another vector and this vector is our contextual embedding**</mark>
* Embedding layer gives us fixed vector for a word
* This are called contextual embedding because here we are going to take importance of different input tokens for generation
*

    <figure><img src="../../.gitbook/assets/image (543).png" alt=""><figcaption></figcaption></figure>
* Inputs: Queries, Keys and Values&#x20;
* <mark style="color:purple;background-color:purple;">**Model will be computing Q, K and V**</mark>

<mark style="color:purple;background-color:purple;">**Query Vector:**</mark>

* <mark style="color:purple;background-color:purple;">**Represents the token for which we are calculating the attention**</mark>
* <mark style="color:purple;background-color:purple;">**They help determine the importance of other tokens in the context of the current token**</mark>
* Importance:
  * Focus determination:
    * Queries help the model decide which parts of the sequence to focus on for each specific token. By calculating the dot product between a query vector and all key vectors, the model accesses how much attention to give to each token relative to the current token
  * Contextual Understanding:
    * Contribute to understanding the relationship between the current token and rest of the sequence, which is essential for capturing dependencies and context

<mark style="color:purple;background-color:purple;">**Key Vector:**</mark>

* <mark style="color:purple;background-color:purple;">**Represents all the tokens in the sequence and are used to compare with the query vectors to calculate attention scores**</mark>
* Importance:
  * Relevance measurement:
    * Keys are compared with queries to measure the relevance or compatibility of each token with the current token. This comparison helps in determining how much attention each token should receive
  * Information retrieval:
    * Keys play a critical in retrieving the most relevant information from the sequence by providing a basis for the attention mechanism to compute similarity scores

<mark style="color:purple;background-color:purple;">**Value Vector:**</mark>

* <mark style="color:purple;background-color:purple;">**Holds the actual information that will be aggregated to form the output of the attention mechanisms**</mark>
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

* <mark style="color:purple;background-color:purple;">**We create Q,K and V by multiplying the embeddings by learned weight matrices**</mark> $$W_Q, W_K, W_V$$
* We will do dot operation and CAT and $$W_Q$$ to get Q and so on for V and K
*   We will initialize weights and then using back propagation it will be learned

    <figure><img src="../../.gitbook/assets/image (539).png" alt=""><figcaption></figcaption></figure>
* &#x20;We are initializing weights as I here
*

    <figure><img src="../../.gitbook/assets/image (540).png" alt=""><figcaption></figcaption></figure>

3. Compute Attention Scores:

*

    <figure><img src="../../.gitbook/assets/image (542).png" alt=""><figcaption></figcaption></figure>

4. Scaling:

* <mark style="color:purple;background-color:purple;">**We take up the scores and scale down by dividing the scores by**</mark> $$sqrt$$$$\sqrt{d_k}$$
* <mark style="color:purple;background-color:purple;">**Scaling in the attention mechanism is crucial to prevent the dot product from growing too large ⇒ To ensure stable gradients during training**</mark>
* if $$d_k$$ is large
  * Gradient exploding
  * Softmax saturation
* Example:
  * Q = \[ 2 3 4 1] K1 = \[1 0 1 0] K2 = \[0 1 0 1]
* Dot product without scaling:
  * $$Q.K^T_1$$ = 6
  * $$Q.K^T_2$$ = 4
  * Score \[6, 4] ⇒  Scaling not applied
  * Softmax (\[ 6 4])  = \[0.88, 0.12]
  * This value means that most of the attention weight is assigned to the first key vector and very little to the second vector
  * When we apply softmax to 6,4 then there is lot of difference between output
  *   When we do back propagation then the small value will cause vanishing gradient problem

      <figure><img src="../../.gitbook/assets/image (9) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Dot product with scaling:
  *   Here the attention weights are more balanced compared to the unscaled case

      <figure><img src="../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Importance:
  * <mark style="color:purple;background-color:purple;">**If we dont apply scaling and then during backpropagation the gradients of softmax will be very small and can cause vanishing gradient problem, however if we apply scaling before softmax then gradient wont be too small**</mark>
  * Scaling prevents extremely large dot products, which helps in stabilizing the gradients during back propagation, making the training process more stable and effecient
  * By scaling the dot products, the softmax function produces more balanced attention weights
*

    <figure><img src="../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>

5. Apply softmax:

*   Initially we had given 4 dimension vectors, so the final output vector should also be 4 dimensional vector, so we apply step 6

    <figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>

6. Weighted sum of values:

* <mark style="color:purple;background-color:purple;">**We multiply the attention weights by corresponding values vector**</mark>&#x20;
*

    <figure><img src="../../.gitbook/assets/image (13) (1) (1).png" alt=""><figcaption></figcaption></figure>
* The was having embedding as \[1 0 1 0] ⇒ After passing through self attention ⇒ \[1.2669, 0.9999, 1.2669, 0.9999]
*

    <figure><img src="../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption></figcaption></figure>
