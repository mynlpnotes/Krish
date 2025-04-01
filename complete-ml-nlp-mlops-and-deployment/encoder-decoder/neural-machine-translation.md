# 🟢 Neural Machine Translation

**Language translation:**

* English -> Hindi or Kannada or any language
* In this case, English is also information, and hindi is also information
* But their meaning is same
* For this we need encoder and decoder architecture
* <mark style="color:purple;background-color:purple;">**Encode the English into some numbers/vectors**</mark>
* <mark style="color:purple;background-color:purple;">**And then decode it into some other language**</mark>
* <mark style="color:purple;background-color:purple;">**One to one mapping between the languages is not possible**</mark>
*

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
* In English it is 3 words, If we decode then this will be 4 words in French
* Similarly for hindi as well
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Embedding layer will convert numbers into vectors
* This word vectors we will feed to RNN
* <mark style="color:purple;background-color:purple;">**We have reversed the input sequence here**</mark>
* We are not using any output here, we will be using last value here and passing it to decoder
* We have embedding lookup for target language
* 1st character is \<sos> and at end we use \<eos>
* This target language embeddings are passed to decoder
* The outputs will be passed to softmax layer
* Softmax will give probability of sentence
* In the prediction there was 1 wrong value
* Encoding for English and hindi will be different
*

    <figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* At x(0) there is no previous input, its output will go as hidden state to x(1)
* Embedding of drink and hidden state will go to 2nd RNN
* Its hidden state will go to next RNN and so on
* This encoded information will be in the form of array and this will go to decoder
* We should decode the 1st value of the encoder so that it becomes the 1st decoded value, that’s why we have reversed the input
* In decoder, the encoded value of I will be passed and it will be decoded
* This decoded value will be passed to the next RNN along with the next information
* \<sos> and encoded value of I, will give decoded value as main
* Embedding lookup will be randomly generated
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
* (in this diagram it is not group of RNN, it is rolled over time)
* We compared target and predicted
* There are only 2 mistakes
* So <mark style="color:purple;background-color:purple;">**weights of this RNNs will be updated, and the embedding lookup will also be updated and it will backpropagate all the previous RNN and then weights and embedding lookup of encoder as well**</mark>
* <mark style="color:purple;background-color:purple;">**Embedding layer for English as well as hindi will be updated**</mark>
* RNNs of encoder and decoder will learn the sequence
* In encoder as well  \<eos> and \<sos> will be there
* This is used for model to understand when to start prediction and when to stop it
