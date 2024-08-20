# Word2Vec intuition

* 2013
* Uses a neural network model to learn word associations from a large corpus of text
* Once trained, such a model can detect synonymous words or suggest additional words for a partial sentence
* As the name applies, word2vec represents each distinct word with a particular list of numbers called a vector
* Lets say, we have a vocabulary -> boy, girl, king, queen, apple, mango
* Features -> Gender, Royal, Age, Food ......300 features
* Every word will have 300 dimension vector
* We can have any number of dimensions
* The feature representation used are not known
* If we do KING - BOY + QUEEN = GIRL
* This is how we will be getting relationship between the vectors
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Cosine Similarity:**

* &#x20;Distance = 1 - cosine similarity
* Cosine similarity is the cos of the angle between the 2 vectors
* Since distance is 0.29 then it means they are similar
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
