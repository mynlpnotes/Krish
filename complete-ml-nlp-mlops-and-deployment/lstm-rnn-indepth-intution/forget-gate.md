# Forget Gate

*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Lets say x11 x12 x13 x14 is input text and y15 is the next word
* Every word will be converted into vector
* Lets say input dimension is 4, dimension of ht-1 be 3
* Then ct-1 will also be 3 dimension
* We will be combining ht-1 and xt and passed to NN (It can have any number of neurons)
* Sigmoid activation is getting applied to each neurons
* This will given us ft
* There will be (1,7) inputs
* So there will be 7X3 weights
* And there will be 1X3 output ⇒ ft
* After that there is a pointwise operation with Ct-1
*

    <figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
* If Ct-1 = \[6 8 0] and ft = \[0 0 0] ⇒ Then it means complete sentence context has been changed
* If ft = \[1 1 1] ⇒ No change in context
*   If ft = \[0.5 1 0.5] ⇒ So context will be removed

    <figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Conclusion:**

* Based on the context, forget gate will let go some information or will not let go some information \[Forgetting]
