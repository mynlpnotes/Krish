# Vanishing Gradient Problem and Sigmoid

* This is 2 layered NN with sigmoid as activation function
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Sigmoid:

* It squeezes output between 0 and 1
* If we want to update w1 then we will be using derivative and expand it using chain rule
* The output of sigmoid is between 0 and 1, and if we take its derivative then it will be 0 and 0.25
* Weights are also initialized smaller values between 0 and 1
* So a smaller value will be multiplied with weights
* So for w1, we will be multiplying so many smaller values, and it will be multiplied with small learning rate, so the change in w1 will be very very small
* If weights are not getting updated then we are not moving towards convergence
* This is known as vanishing gradient problem
* In a Deep NN, where we will be having more layers then we will be having this problem
* To solve this reasearchers started exploring other activation function = tanh, relu, pre relu, swiss
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>
