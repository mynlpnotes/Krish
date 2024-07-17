# KNN Classification and Regression Intuition

* Can be used for classification as well as regression
* Can be used for binary categories as well as multiclass categories

**Steps:**

1. Initialize value of K - No. of neighbors -- This is a hyperparameter
2. Find K nearest neighbors for the test data
3. From those K values, how many neighbors belong to which category - The category to which maximum neighbours belong will be the output

*   &#x20;

    <figure><img src="../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>
* The nearest neighbors can be found using - Eucledian distance, Manhattan distance
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

**Regression:**

* &#x20;For new test data, we will find the 5 nearest neighbours
* We will take the average of the outputs of the neighbours
*   &#x20;

    <figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>



* &#x20;This process of calculating nearest neighbors is time consuming
* So we use variants of KNN like KD Tree , Ball Tree, we basically optimize this entire distance calculation
*

    <figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>
