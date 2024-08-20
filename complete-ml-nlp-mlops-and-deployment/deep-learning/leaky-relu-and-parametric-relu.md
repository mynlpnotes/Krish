# Leaky Relu and Parametric Relu

* If we use alpha then its parametric relu, if we use constant value like 0.01 then its leaky relu
* Here even for -ve value we will get some output, so its derivative will also be not 0
* This solves dead relu issue
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Pros:

* Removes dead relu issue

Cons:

* Not Zero centric
