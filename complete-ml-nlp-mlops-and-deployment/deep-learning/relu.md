# Relu

* Output will be max of 0 or Z
* Derivative will be either 0 or 1
* If z is -ve its derivative will be 0, if its +ve then it will be 1
* If its 1 then weight updation will occur, if its 0&#x20;
* If its 0 then it creates a dead neuron
*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Pros:

* Solves vanishing gradient problem
* Calculations are fast
* Much faster than sigmoid or tanh

Cons:

* Dead neuron
* Not Zero centric