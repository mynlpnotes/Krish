# Sigmoid Activation

* Transforms value between 0 and 1
* Used in hidden layer
*   Derivative is in range of 0 and 0.25

    <figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

**Cons:**

* When the input is away from the coordinate origin, the gradient of the function becomes very small, almost zero,  In backpropagation we use chain rule to calculate differentials of each weight w, so the differential of the chain is very small, which leads to vanishing gradient problem
* Slower
* This is not zero centered function output (since its not passing through 0) - In ML we do standard scalar so it becomes 0 centered, so if data is 0 centered and function is also 0 centered then it will result in effecient weight update

Pros:

* Smooth gradient, prevent jumps in output values
* Output between 0 and 1, normalizing the output of each neuron

