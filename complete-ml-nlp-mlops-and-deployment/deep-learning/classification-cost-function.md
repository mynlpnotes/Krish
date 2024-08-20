# Classification Cost Function

* Cross entropy technique
* Binary classification -> Binary cross entropy
* Multi class classification -> Categorical cross entropy, Sparse categorical entropy

**Binary cross entropy:**

* We use log loss here -> Same as used in logistic regression
* Since this is binary classification problem, we use sigmoid in output layer
*
*

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

**Categorical Cross Entropy:**

* It will apply One hot encoding to all the output
*

    <figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

**Sparse categorical cross entropy:**

* The difference between categorical and sparse, is that here we don't focus on other categories
*

    <figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
