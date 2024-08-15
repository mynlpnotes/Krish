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
* Weight updation will start from reverse direction
* We want to reach global minima, so that after that we don't need to update any weights
* Derivative means we are trying to find the slope, depending on whether its positive or negative we increase or decrease the weight
* We also have learning rate
* If its very small 0.001 then weight updation will happen slowly
* Learning rate decides the step size towards global minima

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

**Optimizer:**

* To minimize loss function we use optimizer
* Here this is gradient descent optimizer, there are different optimizers
* We have to reach global minima
* W.r.t initial weights we get some loss
* Derivative means we are trying to a tangent/slope
* We need to see the right side of the line
* Whenever its pointing downwards then we will be getting -ve slope
* So in this case, weight will increase
* If w is on the other side of global minima, if we calculate slope, then it will be +ve
* So weight will reduce
* Slope at global minima will be 0

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>
