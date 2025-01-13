# 🟢 Cost Function

<mark style="color:purple;background-color:purple;">**Loss function is for a single instance, whereas cost function is for the entire dataset**</mark>

* Suppose this is last layer of NN
* Suppose input image is of 1
* Since this is multiclass classification, softmax will be used here
* We are having the probability for each class here
* We will use max to get the index of the maximum value
* The actual value here is that 1 should have probability as 1 and remaining as 0
* Cost will be calculated as
* This cost will be calculated to optimizer so that it tries to reduce it
* Loss function is MSE
*   Cost function is total loss across the data

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
