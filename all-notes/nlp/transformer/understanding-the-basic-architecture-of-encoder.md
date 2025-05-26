# 🟢 Understanding the basic architecture of Encoder

* Used for Seq2Seq task
* Encoder-Decoder Architecture
* <mark style="color:purple;background-color:purple;">**There can be multiple encoder / decoder**</mark>
* In the research paper its specified there will be <mark style="color:purple;background-color:purple;">**6**</mark> encoders / decoders
* We don't use LSTM RNN etc. in the architecture
* <mark style="color:purple;background-color:purple;">**Encoder will have 1 self attention layer and 1 feed forward NN**</mark>
*   <mark style="color:purple;background-color:purple;">**Decoder will have a self attention as well as feed forward, it also has additional layer called - Encoder Decoder attention**</mark>

    <figure><img src="../../../.gitbook/assets/image (18) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;Vectors of the words will be passed
* This vectors will be passed to <mark style="color:purple;background-color:purple;">**self attention layer, which will convert into different vector called as contextual layer**</mark>
* Contextual vector will have context of different vectors
* This are sent to feedforward NN
*   <mark style="color:purple;background-color:purple;">**Since we are using self attention layer, so we can pass all the words parallelly**</mark>

    <figure><img src="../../../.gitbook/assets/image (19) (1) (1).png" alt=""><figcaption></figcaption></figure>
* &#x20;<mark style="color:purple;background-color:purple;">**The output of feed forward NN, will be sent to next encoder**</mark>
*

    <figure><img src="../../../.gitbook/assets/image (20) (1) (1).png" alt=""><figcaption></figcaption></figure>
