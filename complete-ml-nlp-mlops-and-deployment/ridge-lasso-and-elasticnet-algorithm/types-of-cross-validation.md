# Types of Cross Validation

* Training is used to train the model and for hyper parameter tuning
* Training data is split into Train and Validation
* Using this validation data we hyper tune the model
* Test data is used to check the performance of the model
* To split into train and validation we use cross validation
* If we change random\_state we will be getting different train and validation
* For each split we might get different accuracy
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



1. **Leave one out cross validation:**

* For 1st experiment we will putting 1st record in validation data, it will be trained on remaining data and validated on 1st record
* For 2nd experiment we will be putting 2nd record in validation and so on
* Since we taking only 1 record we will have to lot of iterations
* As the data size increases, complexity of training the model also increases
* Leads to overfitting -- w.r.t to our training data our accuracy is high, since validation is very small then the accuracy will keep on increasing
* Not used
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

2. **Leave P out CV:**

* Instead of 1 record, we can set P = 10, 20 and so on

3. **K - fold CV:**

* &#x20;We decide value of K
* Validation size = No. of records / K
* In the 1st experiment, 1st set of records will be validation and remaining will be train
* For 2nd experiment we will be taking 2nd set of records and so on
* We will taking average of the accuracy of all the folds
* We also note the minimum and maximum accuracy as well
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

4. **Stratified K fold CV:**

* The problem with K fold is that if we are having a classification problem, then there is high possibility then in validation we might be getting records of the same class
* The no. of possible outputs will be evenly distributed in each fold
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

4. **Time series CV:**

* Product sentiment analysis
* Suppose initially reviews are bad, but then later it improves
* Cross validation will happen based on days
* Day 1 Day 2 ..... Day N
* We divide our dataset based on days
* We put the 1st number of records in train in sequence and remaining we put in validation
* It is used mainly in time series application
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
