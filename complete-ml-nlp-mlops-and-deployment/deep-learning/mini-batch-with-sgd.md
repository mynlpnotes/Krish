# Mini Batch with SGD

* Since we have noise in SGD we use this
* Here we also use batch size
* If we have 100k data points, then in EPOCH1
* Lets say batch size is 1000 records
* So in every iteration we take 1000 records and there will 100 iterations
* For this 1000 data points we will find the cost function
* And using SGD optimizer we will update the weights
* This we will do for 100 iterations
* By brining the batch size we are reducing number of iterations as well as noise
*
*

    <figure><img src="../../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

Advantage:

* Better convergence speed compared to SGD
* Noise will be less when compared to SGD
* Effecient resource usage

Disadvantage:

* Noise still exists
*
