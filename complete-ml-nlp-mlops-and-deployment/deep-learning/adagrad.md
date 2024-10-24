# Adagrad

* Learning rate is generally a small value and it decides the speed of the convergence
* Till now in all the optimizers, learning rate used to be fixed
* We try to make this learning rate dynamic
* So initially for convergence it should take bigger steps and when it reaches minima, its speed should decrease
* Here instead of learning rate, we will be using learning rate dash here
* Epsilon is a small value which is added to ensure that learning rate does not become zero
* Alpha is given as the summation of square of derivate of loss w.r.t t&#x20;
* Here summation of t means, we first go with respect to 1st layer, then 2nd layer and so on
* As we do this alpha value will increase
* As alpha increases learning rate will decrease
* So as we go through each and every hidden layer w.r.t back propagation, the alpha will increase
*   That is how the new dynamic learning rate will decrease

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

**Disadvantage:**

* In a very deep neural network =, the alpha can be do big that learning rate will become very very small which might be approx to 0
