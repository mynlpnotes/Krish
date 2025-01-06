# 🔴 Back Propagation Example

* &#x20;Below is a simple NN with 2 input and 1 output
*   X1 = 0.5, X2 = 0.2, y = 2

    <figure><img src="../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>
* **Weight initialization:**
  * w11 = 0.1, w12 = 0.2, w21 = 0.4, w22 = 0.3
  * w01 = 0.5, w02 = 0.6
  * b1 = 0.1, b2 = 0.2, b0 = 0.3
* **Forward Pass 1:**
  *

      <figure><img src="../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>
  *

      <figure><img src="../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure>
* Loss Calculation:
  *

      <figure><img src="../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure>
* **Back Propagation:**
  * We will calculate the gradients to update weights and biases
  * We will calculate derivate of loss w.r.t ypred
  *

      <figure><img src="../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>
  * Gradients of w01, w02, b0
  *

      <figure><img src="../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>
  *

      <figure><img src="../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>
  *

      <figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
  *

      <figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Calculating gradients of z1 and z2
  *

      <figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
  *

      <figure><img src="../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Calculating gradients of w11, w21, b1, w12, w22, b2
  *

      <figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
  *

      <figure><img src="../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
