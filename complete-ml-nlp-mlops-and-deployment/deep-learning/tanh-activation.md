# Tanh Activation

* &#x20;Transforms value between -1 and +1
* Derivative ranges between 0 to 1
* It is a hyperbolic tangent function
* Zero centered
* For a medium sized NN it wont face any problem, but for very deep neural network we might still face vanishing gradient problem
* In binary classification, tanh is used in hidden layer and sigmoid is used in output layer
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

**Cons:**

* Vanishing gradient exists for deep NN
* Computations are more

Pros:

* Zero centered -> Weight updation effecient
