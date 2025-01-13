# Output Gate

* Whatever information we have after forgetting and adding we will be having Ct (Long term memory)
* We applt tanh on Ct
* And then apply pointwise operation of this value with sigmoid output
* Whatever the output we get from here, will be retained in Ht (Short term memory)
* This Ct and Ht will be passed to the next time stamp
* Weight Wi, Wc and Wo needs to be updated using back propagation
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>
