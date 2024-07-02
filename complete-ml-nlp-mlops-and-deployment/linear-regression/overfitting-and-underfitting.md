# Overfitting and Underfitting

* Suppose we have 1000 datapoints
* Features: Size of house, No. of bedrooms, Price
* We need to split the data into 2 parts -> Training dataset(70%) and Test dataset(30%)
* Test data will never be shown to the model during training
* Training data is further split -> Train and Validation
* Train is used to train the model
* Validation data is used for hyper parameter tuning of the model
*

    <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
* Good accuracy on train -> Low bias&#x20;
* Bad accuracy on Test -> High variance
* Model is overfitting
* Low accuracy on train -> High bias
* Low accuracy on test -> High variance
* Model is underfitting
* Our aim should be to get generalized model
*

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
