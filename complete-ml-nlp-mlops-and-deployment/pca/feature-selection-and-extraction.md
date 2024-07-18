# Feature Selection and Extraction

Why Dimensionality Reduction?

* To prevent curse of dimensionality
* To improve the performance of the model
*   To visualize the data -> to understand the data

    * We can maximum visualize in 3d
    * If dataset is 100d then we can reduce dimension to 2d or 3d and then visualize



**Feature Selection:**

* Here we have if X increases then Y increases and vice versa
* Similarly we can if X increases then Y decreases and vice versa
* If we plot them then it will be linear
* We can quantify this relationship, then we can use covariance
* If its positive then its scenario 1, if its negative then its scenario 2
* If its 0 then there is no relationshop
* So if there is a covariance then we can say that its a important feature
* Correlation will be between -1 to +1
* The more it is towards +1 the more positively correlated it is&#x20;
* The more it is towards -1 the more negatively correlated it is&#x20;
*

    <figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>
* House size and fountain size are independent features
* Fountain size does not contribute to price of the house
* If we plot this features against price
* From this we understand house size is important
* Since fountain size is not important, we can drop the feature
*

    <figure><img src="../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

**Feature Extraction:**

* Here we want to reduce the number of features
* We cannot use feature selection, coz both the features are important
*   So here we perform feature extraction, we take this 2 dimension and apply some transformation to extract some new feature(House size)

    <figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>
