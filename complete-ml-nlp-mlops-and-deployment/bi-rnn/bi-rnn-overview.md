# 🟢 Bi RNN - Overview

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt="" width="210"><figcaption></figcaption></figure>

* Above is a unidirectional RNN or vanilla RNN

**Issues:**

1. <mark style="color:purple;background-color:purple;">**A regular RNN only looks at past and present input before generating output. This is called as casual network. It cannot look into the future**</mark>
2. ![](<../../.gitbook/assets/image (2) (1) (1) (1).png>)

* Here without knowing the next word, it wont be able to understand that queen is used in which context
* <mark style="color:purple;background-color:purple;">**A regular RNN will go only L to R, so it wont be able to understand the context and may not predict correct output, this will happen in cases where word can have multiple meanings (e.g., queen)**</mark>
* <mark style="color:purple;background-color:purple;">**If we are able to feed the reverse, then we will be knowing the next sequence also**</mark>
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1).png" alt=""><figcaption></figcaption></figure>
* We will be having forward and backward layer
* We are getting the feed in both the direction
* <mark style="color:purple;background-color:purple;">**Once we have the output of forward and backward layers, we will be concatenating the output at each time stamp**</mark>
* For neural machine translation task it is preferable to look ahead at next word before encoding a given word
* So all the queens will be having different embeddings
* Run 2 RNNs on the same input, one is reading from L to R and another is reading from R to L
* Combine the output at each time step by concatenating them
* <mark style="color:purple;background-color:purple;">**Tf.keras.layers.BiDirectional(tf.keras.layer.GRU(Units))**</mark>&#x20;
*

    <figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
* Can be used inside encoder-decoder architecture
* And also for NMT
* Encoder -> Embeddings -> LSTM -> Dense
* Masking means adding passing like EOS, BOS etc
* Libraries to explore:

1. Ktrain
2. Pytorch lighning
3. Hugging face
