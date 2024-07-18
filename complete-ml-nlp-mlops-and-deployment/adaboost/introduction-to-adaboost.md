# Introduction to Adaboost

* &#x20;If we train a DT to its complete depth, then it leads to overfitting
* In RF we had multiple DT so it has low bias and low variance
* In boosting we have multiple models sequentially
* Whatever records have been wrongly classified will be next tree and so on
* If we combine all weak learner then we get strong learner
* Weak learner means it hasn't learnt much from the training dataset
*

    <figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>
* &#x20;In Adaboost we assign weights to the weak learner
*

    <figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>
* Decision tree stump means we will be creating a decision tree whose depth will be just 1
* Since its having just 1 level so its a weak learner
* It will lead to underfitting (Train accuracy is low, and test accuracy can be low or more) -> High bias and low variance
* When we combine multiple DT stump then it will lead to low bias and high variance
