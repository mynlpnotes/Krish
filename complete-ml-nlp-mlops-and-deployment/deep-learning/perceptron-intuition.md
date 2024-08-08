# Perceptron Intuition

* It is a simple neural network unit
* We also call it as single layered NN
* Perceptron is a basic unit of ANN
* Used in solving binary classifier
* Dataset: Input: IQ, No. of study hours. Output: Pass/Fail
* We need to train weights&#x20;
* Insde a neuron 2 process happen:&#x20;
* Step 1: Summation of weights and inputs + bias
* Step 2: Apply activation function
* Weights are initially randomly processed, if all weights are 0 and there is no bias then there will be no output of neuron, so we add bias as noise
* Activation function is to transform the output between some values(0 to 1, -1 to +1)
*

    <figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>
* In step function, threshold will be 0
* In sigmoid function, threshold will be 0.5
* For linear classification, with the help of perceptron we are able to create a line which can separate  classes
* That means perceptron is a linear classfier
