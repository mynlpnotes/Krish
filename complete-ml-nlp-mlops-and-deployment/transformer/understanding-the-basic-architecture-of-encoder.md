# Understanding the basic architecture of Encoder

* Used for Seq2Seq task
* Encoder-Decoder Architecture
* There can be multiple encoder / decoder
* In the research paper its specified there will be 6 encoders / decoders
* We dont use LSTM RNN etc in the architecture
* Encoder will have 1 self attention layer and 1 feed forward NN
*   Decoder will have a self attention as well as feed forward, it also has additional layer called - Encoder Decoder attention

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
* &#x20;Vectors of the words will be passed
* This vectors will be passed to self attention layer, which will convert into different vector called as contextual layer
* Contextual vector will have context of different vectors
* This are sent to feedforward NN
*   <mark style="color:purple;background-color:purple;">**Since we are using self attention layer, so we can pass all the words parallelly**</mark>

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;The output of feed forward NN, will be sent to next encoder
*

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
