# 🟢 RNN forward propagation with time

Dataset:

* The food is good ⇒ 1
* The food is bad  ⇒ 0
* The food is not good ⇒ 0
* Lets say we use OHE for encoding here
* D1 = \[\[1 0 0 0 0] \[0 1 0 0 0] \[0 0 1 0 0]]
* <mark style="color:purple;background-color:purple;">**For passing a single word at a time, we will be needing 5 neurons in input**</mark>
* Neurons will be connected to all the neuron in the hidden layer
*   <mark style="color:purple;background-color:purple;">**At t=2, output of each neuron of hidden layer will be passed to itself and also to all the neurons of the hidden layer**</mark>

    <figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
