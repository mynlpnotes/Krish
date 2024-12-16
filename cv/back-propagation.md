# Back Propagation

* Responsible for computing gradients of the loss w.r.t each weight and bias in the network
* Once the gradient have been calculated via backpropagation, gradient descent uses these gradients to update weights and biases in the network
* $$new\ weight = old\ weight - learning rate * \frac{dL}{dw}$$
* Without back propagation, we wouldn't know how to calculate the gradients for each w and b in the network
* Without gradient descent, even if we know gradients, we wouldn't have and efficient way to update the parameters and minimize the loss
