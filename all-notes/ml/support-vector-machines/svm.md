# SVM

* Support vector machines
* Classification as well as regression
* Can also be used for multiclass classification
* In logistic regression we used to draw a decision boundary, and then check the probability of the instance to be on either side of the line
* In SVM, we try to draw a straight line and then calculate margin and then we try to find a support vector
* If the dataset is available in 2dimension, then we can draw a 1-dimension (n - 1) structure which will be able to create a separation
* Hyper plane(n -1) with supporting vectors at the side
* Distance between hyperplane and supporting vector is margin
* Supporting vector – Parallel to the hyperplane, in such a way that it will touch the 1st dataset in either side
* Best line will be with the maximum distance
* For the new dataset, it will check distance from the hyperplane/margin to predict the class
*

    <figure><img src="../../../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>
* Pseudo code:
  * Take training dataset
  * Find number of lines which can be used for separation and margin
  * Tune the line and margin
* Whenever we draw margin, it should create maximum separation
*

    <figure><img src="../../../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>
* Incase of regression, the only difference will be margin, it will calculate what will be the error for the margin
* We keep those combination of line and margin, in which the error will be minimum
* SVM works well with non linear data also using kernel trick
* If the dimension of the data is very high or we are not able to create separations then kernel trick can be used
* If data is n dimension then try to represent it in n + 1 dimension
* For this we will be needing new coordinates, so if data is in 2 dimension then we know its x and y
* So z2 = x2 + y2, using this we will be able to calculate 3rd coordinate
* We will be able to understand shape better in higher dimension
*

    <figure><img src="../../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>
* Converting lower into higher dimension is part of data transformation
