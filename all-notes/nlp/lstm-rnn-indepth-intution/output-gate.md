# 🟢 Output Gate

* <mark style="color:purple;background-color:purple;">**Whatever information we have after forgetting and adding we will be having Ct (Long term memory)**</mark>
* <mark style="color:purple;background-color:purple;">**We applt tanh on Ct**</mark>
* <mark style="color:purple;background-color:purple;">**The tanh function ensures that the hidden state values remain within a reasonable range (-1 to 1).**</mark>
* <mark style="color:purple;background-color:purple;">**This prevents exploding activations and ensures smooth gradient flow.**</mark>
* <mark style="color:purple;background-color:purple;">**And then apply pointwise operation of this value with sigmoid output**</mark>
* <mark style="color:purple;background-color:purple;">**Whatever the output we get from here, will be retained in Ht (Short term memory)**</mark>
* <mark style="color:purple;background-color:purple;">**This Ct and Ht will be passed to the next time stamp**</mark>
* <mark style="color:purple;background-color:purple;">**Weight Wi, Wc and Wo needs to be updated using back propagation**</mark>
* <mark style="color:red;background-color:purple;">**Applying tanh ensures that only a scaled version of the memory is passed, avoiding abrupt or excessive updates.**</mark>
*   <mark style="color:purple;background-color:purple;">**Ht is same as output**</mark>

    <figure><img src="../../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>
