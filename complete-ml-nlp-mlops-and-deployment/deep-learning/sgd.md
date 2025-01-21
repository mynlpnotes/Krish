# SGD

* In SGD, we pass single record in each iteration
* We calculate loss function, and then do backward propagation
*

    <figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

**Advantage:**

* Solves resource issue

**Disadvantage:**

* Time complexity increases
* Convergence takes time
* Noise gets introduced -> Since we are updating the weights based on a single record so it wont be a smooth convergence
*

    <figure><img src="../../.gitbook/assets/image (508).png" alt=""><figcaption></figcaption></figure>
