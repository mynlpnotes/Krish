# 🟢 Working of NN - 1

* We divide the data into train, validation and test
* Train is used to train the model
* Validation is used to check model performance
* Test is used to test on real world data
* Here we are having 4 hidden layers
* Moving from left to right is known as Forward Pass
* If wrong prediction, then with the help of back propagation, we will update the weights that caused the output
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**We want to create generalized model and not have overfitting**</mark>
* <mark style="color:purple;background-color:purple;">**To prevent overfiting, we use dropout**</mark>
* <mark style="color:purple;background-color:purple;">**Dropout will randomly block and make neuron inactive during training**</mark>
*
