# Learning

* yactual is 3 here
* ypred is 0.38 (w1 = 0.5 and w2 = 0.1) -> This is known as forward pass
* We calculate loss, for simplicity we using $$(y - ypred)^2$$
* Based on the loss we calculate gradient of learnable parameters
*

    <figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
* Gradient means if we change w1 by a very small value then how will our loss change
* Backpropagation will provide us gradients and the direction as well
*

    <figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
* &#x20;Optimizer updates the learnable parameters based on their calculated gradients
*   Learning rate influences how much of a gradient you want

    <figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
