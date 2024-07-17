# Variants of Naive Bayes

1. **Bernoulli Naive Bayes:**

* Whenever features are following a Bernoulli distribution, then we need to use Bernoulli Naive Bayes
* Bernoulli means only 2 outcomes
* Output class can be binary or multi class
* When we convert features into 0 and 1, then it will have sparse representation (maximum 0s and few 1s)
*   For NLP problems we can use multinomial as well as bernoulli naives bayes as well

    <figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

2. **Multinomial Naive Bayes:**

* If input is in the form of text
*   Text will be converted into number using NLP techniques like BOW, Tf-Idf, word2vec

    <figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

3. **Gaussian Naive Bayes:**

* if the features are following Gaussian distribution&#x20;
* Features are numerical
*

    <figure><img src="../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>



* If the maximum features are having bernoulli distribution then we for bernoulli&#x20;
* if some of the features are continuous and some are having multiple categories then we for gaussian
