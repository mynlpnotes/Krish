# Types of ML techniques

1. **Supervised:**

* Suppose the task is to predict house price
* Dataset - Size of the house, No. of rooms, Price
* We divide this features into 2 categories
* Independent features - Size, No. of rooms
* Dependent features - Price
* <mark style="color:purple;background-color:purple;">**Regression: Dependent feature will be continuous**</mark>
* <mark style="color:purple;background-color:purple;">**Classification: Dependent feature will be categorical**</mark>
* <mark style="color:purple;background-color:purple;">**if there are only 2 categories then we call it as binary classification**</mark>
* <mark style="color:purple;background-color:purple;">**If there are more than 2 then its multi class classification**</mark>
* **Algorithm:**
* Linear Regression
* Ridge & Lasso&#x20;
* ElasticNet
* Logistic Regression - Classification
* Decision tree - Both classification and regression
* Random forest - Both classification and regression
* AdaBoost - Both classification and regression
* XGboost - Both classification and regression

2. **Unsupervised:**

* Example: Customer segmentation
* We do not know the output feature
* We don't need to predict
* We need to <mark style="color:purple;background-color:purple;">**find the similar group or clusters**</mark>

<figure><img src="../../.gitbook/assets/image (10) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

*
* K Means
* Hierarchical means
* DBScan

3. **Reinforcement:**

* Application will learn by itself by getting rewards

4. **Semi Supervised:**

* <mark style="color:purple;background-color:purple;">**Combination of supervised + unsupervised**</mark>
* Regression + Classification + Clustering
