# Random Forest Classification and Regression

* &#x20;Lets say the size of dataset is d and we have m features
* All the base models will be decision trees
* **Row sampling with replacement** + Feature sampling will be done for passing data to each of the models
* For new test data, all the DT will give their outputs
* Here we will do majority voting classifier
* Similarly w.r.t regression, we basically calculate the average of all the models output
*

    <figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

**Why should we use RF instead of DT?**

* Time complexity of RF will be more compared to DT, still RF will be referred because
* DT can have overfitting - Low bias and high variance
* A generalized model should have low bias and low variance
* Since RF has multiple DT and each DT has different set of data and features
* And as majority voting is done so it will have good accuracy for test data
*

    <figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
