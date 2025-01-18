# 🟢 Intuiton

* If we have a sentence in English and want to convert it into French, this is a many to many RNN
* This is a seq2seq NN (Input as well as output are sequence)
* Chat is also seq2seq use case
* For such cases we cannot use LSTM RNN etc
* Embedding will convert words to vectors
* <mark style="color:purple;background-color:purple;">**Encoder will take this vector and generate hidden state / context vector which will be passed to the decoder**</mark>
*   <mark style="color:purple;background-color:purple;">**The decoder generates the output word-by-word and keeps feeding the previous word into the decoder again**</mark>

    <figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**We can select LSTM/GRU inside the encoder/decoder**</mark>
* LSTM will have long term memory and hidden state
* Thank you ⇒ Gracias
* In LSTM <mark style="color:purple;background-color:purple;">**we will pass entire sentence along with <\<sos>> (start of statement) and <\<eos>> (end of sentence) in encoder and decoder**</mark>
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In Encoder we give every word one by one to LSTM, so we will be passing embedding of <\<sos>> will be used
* At next time stamp, next word 'thank' will be passed and so on
* **Long term and short term memory combined is known as context vectors**
* In Decoder, our french training set is gracias ⇒ <\<sos>> Gracias <\<eos>>
* Here also we will have LSTM
* <mark style="color:purple;background-color:purple;">**1st we will pass <\<sos>> to decoder, then we pass it to a FCNN with softmax activation function**</mark>
* <mark style="color:purple;background-color:purple;">**The output of NN (Gracias) will be passed to LSTM**</mark>
* <mark style="color:purple;background-color:purple;">**Then again output of LSTM will be passed to FCNN and so on**</mark>
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* We will be having ypred and y
* After forward propagation we will calculate loss
* To reduce the loss, we will use optimizer
* This will update the weights using back propagation
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
