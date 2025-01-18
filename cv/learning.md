# 🟠 Learning

* yactual is 3 here
* ypred is 0.38 (w1 = 0.5 and w2 = 0.1) -> This is known as forward pass
* We calculate loss, for simplicity we using $$(y - ypred)^2$$
* <mark style="color:purple;background-color:purple;">**Based on the loss we calculate gradient of learnable parameters**</mark>
*

    <figure><img src="../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Gradient means if we change w1 by a very small value then how will our loss change**</mark>
* <mark style="color:purple;background-color:purple;">**Backpropagation will provide us gradients and the direction as well**</mark>
*

    <figure><img src="../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Optimizer updates the learnable parameters based on their calculated gradients**</mark>
*   <mark style="color:purple;background-color:purple;">**Learning rate influences how much of a gradient you want**</mark>

    <figure><img src="../.gitbook/assets/image (8) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
