---
hidden: true
---

# 🟢 RNN forward propagation with time

* Input x11 will be multiplied with weight and bias will be added and we will get O1
* For transfer of O1 to next timestamp again there will be a weight
* We will be calculating O4
* If its binary classification problem then we will be using sigmoid
* If multi class then we will be using softmax
* We will calculate loss, and then we will do back propagation to reduce the loss
* <mark style="color:purple;background-color:purple;">**O1 = f(x11.w + b1)**</mark>
* <mark style="color:purple;background-color:purple;">**O2 = f(x12.w + O1.w" + b1)**</mark>
* <mark style="color:purple;background-color:purple;">**O3 = f(x13.w + O2.w" + b1)**</mark>
*

    <figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
