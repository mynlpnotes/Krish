# LSTM RNN Architecture

* Xt is input
* 3 import gates:
  * Forget gate
  * Input gate and candidate memory
  * Output gate
* Ht-1 is hidden state of previous time stamp
* In tanh, we will be applying tanh function to each element of the vector
* Xt and Ht-1 are combined together and then they are sent to each gate
* Memory cell is for long term memory
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
