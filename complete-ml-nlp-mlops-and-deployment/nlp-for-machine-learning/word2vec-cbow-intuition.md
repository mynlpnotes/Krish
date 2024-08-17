# Word2Vec Cbow Intuition

* We can use Pre trained model or train a model from scratch
*   Continuous BOW

    <figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>
* We select a window size
* Using this window size, we create our input data and output data
* So we will take 5 words at a time, take the middle word as output and the remaining words will be input
* We are doing so that we know the forward and backward context
* Next we will move the window and take next 5 words
* Using this input and output we will train the model
* We will do OHE for all words
*

    <figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>
* CBOW means it is fully connected neural network
* This vectors we will be giving as inputs to the network
* In hidden layer we will be having 5 neurons
* Output layer will be of size 7
* We do forward and backward propagation till the loss is minimal
* Hidden layer size is our embedding dimension
* The bigger the window size, the better the model
* The weight of the hidden layer to the output layer will form our embedding
*

    <figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
