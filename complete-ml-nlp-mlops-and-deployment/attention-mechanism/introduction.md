# Introduction

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

* Cannot use proximity to understand/gain info from the sentence
* We may think Roopali is a person, but if we read entire sentence then she is a cow
* We can think annoying is related to roopali, can, be , but, she, is
* Our focus is needs to be in roopali, she, cow, annoying
* If we pass this to normal RNN, then it will be difficult to understand where to focus more
* We convert text into tokens, t1 t2…..
* Then we convert them into vectors
* If we want to give importance to any vector, then we can come up with some mechanism of weight w1, w2…..
* This will result into new vector y1, y2….
* This will be trainable weights
* This y1, y2.. will be able to give more contextual information
* We need to train in such a way that w1, w4, w6 and w10 should be more
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
* In both the sentences, both the bank are having different meaning, which we get after reading the entire sentence
* If sentence has bank and river then it means we are talking about a water body
* If sentence has state, bank, india then it means we are talking about a financial institution
* Since both the banks have different meaning, so it should be encoded differently
* Also attention should be given differently
* So we multiply it with attention weights – W1, W2….
* This weights are trainable
*

    <figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
* We first encode the sentence – V1
* Then apply re-weigh mechanism
* This will contain better context information
* We do dot product
*

    <figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
* When we do dot product of 2 vectors, we get scalar – W11, W12….
* After that we normalize them such that W11 +  W12 + W13 + W14 = 1
* Similarly we do for V2.V1 also….
* In Re-weighing, we multiply this weights with V1, V2.... so as to get Y1, Y2....
