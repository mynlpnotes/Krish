# Letter Embedding

* Dataset -> Million headlines which contains headlines of news
* We will predict what is going to be the next letter
* Today is a beautiful \_   -- it will prediction d and then a and then y
* We will be having an embedding layer
* We will be passing letters to it and it will give vectors of all the letters
* This will be passed into dense layer and then we apply softmax at the end and you will tell what will the probability for the next word
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* If we given t and it gives o then it means it is correct
* But if it gives d then it means there is error/loss then there will be backpropagation
* It will update weights of the dense layer and it will also update the vector for t
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>
* This way we will train embedding layer
* It’s same as ANN but here we also pass embedding layer
* Embedding layer initially gives random number as it gets train it will update its embeddings
