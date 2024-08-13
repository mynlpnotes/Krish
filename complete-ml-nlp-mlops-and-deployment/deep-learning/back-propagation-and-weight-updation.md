# Back Propagation and Weight updation

**Loss Function:**

* Regression: MSE, MAE, Huber loss
* Classification: Binary cross entropy, Categorical cross entropy



**Backpropagation:**

* &#x20;If there is multi class classification, then we can use multiple neurons in the output
* Updation of weigts will happen in backward propogation
*

    <figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

**Weight updation formula:**

* We want to reach global minima
* Derivative means we are trying to find the slope, depending on whether its positive or negative we increase or decrease the weight
*   We also have learning rate,

    <figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

Optimizer:

* To minimize loss function we use optimizer
* Here this is gradient descent optimizer

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>
