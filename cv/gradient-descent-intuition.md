# 🟠 Gradient Descent Intuition

* &#x20;We have input X1 and output O1
* Based on weight and biases we are getting output as 1.6, but actual value is 2
* Based on actual and outcome, we calculate loss
* Lets say when weight is -5 loss is on left side
* We will keep updating weight and calculate loss
* We want to minimize the loss
*

    <figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
* Above we had plot in 2D, if we want to plot w.r.t w and b then we will have to use 3D
* Loss of w2b2 is lower than w1b1
* Global minima: The point at which loss will be minimum
* The job of optimizer is to find this global minima,
*   There can be multiple local minima, but there will be a single global minima

    <figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;We want the loss to decrease little by little till it reaches global minima
* If current weight is -3, and we increase or decrease by -0.5 and see the loss
* So we should get the direction based on current weight and bias by giving a small nudge
* This is known as walking down the hill
* Learning rate determines how much to change weights / biases
* If learning rate is high then we might not reach global minima, as it may oscillate
* Adaptive learning rate means as we reach global minima we will decrease learning rate
*   Constant learning rate means learning rate will be constant through out

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
