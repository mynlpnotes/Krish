# ✈️ Data passing to RNN

**Sentiment Analysis:**

* Sentence: The food is good, Output: Positive
* This can be written as \<x11[^1] x12 x13 x14>
* At t = 1, we will pass x11
* We will first convert x11 into vector using word2vec or some other method in some dimensions
* And then this vector will be passed to the network
* At t = 2, we will pass x12 and so on
* Once forward propagation is done, then back-propagation will happen
*

    <figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

[^1]: 
