# Gradient Descent Optimizers

* Optimizer is responsible to reduce the loss in backward propagation
* The formula for weight update will change for every optimizer
*

    <figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>
* &#x20;If dataset has 1000 data points
* We calculate cost function for all the 1000 data points
* Using GD we will be doing gradient descent and weights will be updated
* 1 forward and 1 backward propagation is known as EPOCH
* This will be repeated for all the EPOCH
*

    <figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>
* In GD, 1 EPOCH = 1 iteration
* If we break into 10 iteration, then in 1st iteration we will pass 100 records and so on
* And this 10 iteration will form 1 EPOCH
* But in GD we don't do this

**Advantage:**

* Convergence will happen

**Disadvantage:**

* Huge resource -> GPU, RAM -> Resource intensive

