# 🟢 Forget Gate

*

    <figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
* Lets say x11 x12 x13 x14 is input text and y15 is the next word
* Every word will be converted into vector
* <mark style="color:purple;background-color:purple;">**Lets say input dimension is 4, dimension of ht-1 be 3**</mark>
* <mark style="color:purple;background-color:purple;">**Then ct-1 will also be 3 dimension**</mark>
* <mark style="color:purple;background-color:purple;">**We will be combining ht-1 and xt and passed to NN (It can have any number of neurons)**</mark>
* <mark style="color:purple;background-color:purple;">**Sigmoid activation is getting applied to each neurons**</mark>
* <mark style="color:purple;background-color:purple;">**This will given us ft**</mark>
* <mark style="color:purple;background-color:purple;">**There will be (1,7) inputs**</mark>
* <mark style="color:purple;background-color:purple;">**So there will be 7X3 weights**</mark>
* <mark style="color:purple;background-color:purple;">**And there will be 1X3 output ⇒ ft**</mark>
* <mark style="color:purple;background-color:purple;">**After that there is a pointwise operation with Ct-1**</mark>
*

    <figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
* If Ct-1 = \[6 8 0] and ft = \[0 0 0] ⇒ Then it means complete sentence context has been changed
* If ft = \[1 1 1] ⇒ No change in context
*   If ft = \[0.5 1 0.5] ⇒ So context will be removed

    <figure><img src="../../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

**Conclusion:**

* Based on the context, forget gate will let go some information or will not let go some information \[Forgetting]
