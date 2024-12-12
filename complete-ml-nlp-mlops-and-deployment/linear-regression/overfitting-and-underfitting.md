# Overfitting and Underfitting

* Suppose we have 1000 datapoints
* Features: Size of house, No. of bedrooms, Price
* We need to split the data into 2 parts -> Training dataset(70%) and Test dataset(30%)
* Test data will never be shown to the model during training
* <mark style="color:purple;background-color:purple;">**Training data is further split -> Train and Validation**</mark>
* <mark style="color:purple;background-color:purple;">**Train is used to train the model**</mark>
* <mark style="color:purple;background-color:purple;">**Validation data is used for hyper parameter tuning of the model**</mark>
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Good accuracy on train -> Low bias**</mark>&#x20;
* <mark style="color:purple;background-color:purple;">**Bad accuracy on Test -> High variance**</mark>
* <mark style="color:purple;background-color:purple;">**Model is overfitting**</mark>
* <mark style="color:purple;background-color:purple;">**Low accuracy on train -> High bias**</mark>
* <mark style="color:purple;background-color:purple;">**Low accuracy on test -> High variance**</mark>
* <mark style="color:purple;background-color:purple;">**Model is underfitting**</mark>
* <mark style="color:purple;background-color:purple;">**Our aim should be to get generalized model -> Low bias, low variance**</mark>
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
