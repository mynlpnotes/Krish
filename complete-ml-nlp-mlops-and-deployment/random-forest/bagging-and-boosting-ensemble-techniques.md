# Bagging & Boosting Ensemble Techniques

* Ensemble techniques helps us to combine multiple algorithms together, probably train model and get some kind of output
* Used for classification as well as regression
* Performs good for imbalanced dataset also
* We don't need to do standard scalar&#x20;
* All the algorithms use DT as base learner or weak learner

**Bagging:**

* Random forest
* We have multiple base learners (Same or different ML algorithm)
* We give some sample of dataset to M1
* Another sample to M2 and so on
* So every model get trained with different set of data
* New test data for prediction and every model will do some prediction
* The final output will be done using majority voting&#x20;
* In case of regression, final output will be average of all outputs
* All base learners are getting trained parallely
*

    <figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>



**Boosting:**

* AdaBoost, Gradient Boosting, XGBoost
* Here we have weak learners
* All models are connected sequentially
* When we combine all weak learners, we get a strong learner
* We give entire dataset to M1
* For wrongly predicted records of M1 along with few more records will be passed to M2
* Similarly for M3 and so on
* For new test data, each model will give its prediction
* Here also we can do majority voting OR average for regression
*

    <figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

