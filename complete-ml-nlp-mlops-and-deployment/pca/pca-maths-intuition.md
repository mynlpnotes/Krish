# PCA Maths Intuition

* Lets say PC1 is our principal component line
* Lets take point P1(x1, y1)
* P1 can be said to be a vector, and u is a unit vector
* For projecting P1 onto u, we will get P1'
* This can be calculated using formula
* Lets say u is given by x2, y2
* When we do dot project of P1 and u, we get P1'
* Like this we project all points
* And then we can find the variance of this points
* We giving notations in x for convenience
*

    <figure><img src="../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>
* Our main is here to find the best unit vector which will give us the maximum variance
* So this variance basically becomes our cost function
* We use eigen decomposition - eigen vectors and eigen values to find the unit vector
*

    <figure><img src="../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>
* &#x20;Steps in eigen decomposition

1. Covariance matrix between features
2. Eigen values and eigen vectors will be found from this covariance matrix
3. Highest Eigen vector means where eigen value is high means magnitude of eigen matrix -> This will capture the maximum variance

*

    <figure><img src="../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>
