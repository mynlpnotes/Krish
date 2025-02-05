# Vanishing Gradient Problem

* The problem relates to updating wrec (weight recurring) – the weight that is used to connect the hidden layers to themselves in the unrolled temporal loop.
* &#x20;For instance, to get from xt-3 to xt-2 we multiply xt-3 by wrec. Then, to get from xt-2 to xt-1 we again multiply xt-2 by wrec. So, we multiply with the same exact weight multiple times, and this is where the problem arises: when you multiply something by a small number, your value decreases very quickly.
* The vanishing gradient problem refers to the issue where gradients diminish exponentially as they are backpropagated through time in RNNs.
* As the gradients propagate backward, they may become very small, especially if the activation function's derivative approaches zero.
* Consequently, these vanishing gradients have little to no impact on updating the weights of earlier time steps, particularly in long sequences.
