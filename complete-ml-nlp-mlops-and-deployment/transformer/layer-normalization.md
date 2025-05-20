# Layer Normalization

*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* After multi head attention there is add and normalize step
* Residual: Vector which are got after getting positional encoding
* They provide additional signal to layer normalization
* &#x20;Before passing multi head attention to feed forward, we will apply layer normalization
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Normalization:

* Batch normalization
* Layer normalization



* Lets say we have a NN with 2 inputs, 2 hidden and 1 output neuron
* Lets say we have features as house size and no. of rooms as input features and price is output
* Before giving this input to NN, we do standard scaling normalization
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In DL, we do min max scaling
* All the inputs of image will be between 0 and 255
* We convert all this between 0 and 1
* We usually do this for input scaling

**Advantages:**

1. **Improved training stability:**

* Our input data can be having different distribution
* When we convert into information where all the data is centered around 0
* When we do back propagation, we will not face vanishing or exploding gradient problem

2. **Faster convergence:**

* Since all the data is 0 centered, when we apply back propagation there will be stables updates
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*
