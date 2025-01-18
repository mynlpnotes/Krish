# 🟢 Pooling Layer

* <mark style="color:purple;background-color:purple;">**Pooling is used to reduce dimension**</mark>
* <mark style="color:purple;background-color:purple;">**It picks the most prominent feature**</mark>
* Suppose we perform convolution on R channel with stride of 2 and kernel of 3X3
* After convolution output is of size 5X5
* How can we reduce more?
* Suppose we take pooling of 2X2 and then we perform convolution
* Suppose we apply max pool -> then we get output as 100, 100, 200
*

    <figure><img src="../../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Types of Pooling:**

1. Max Pooling
2. Min Pooling
3. Average pooling
