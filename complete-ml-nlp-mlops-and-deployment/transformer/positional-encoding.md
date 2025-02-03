# 🟠 Positional Encoding

* Representing order of sequence
* <mark style="color:purple;background-color:purple;">**Major advantage of using transformer is that it can process all the word tokens parallelly but it lacks the sequential structure of the words**</mark>
* Example:
  * Lion kills tiger
  * Tiger kills lion
  * If we don't pass order, both sentence will return same vector
* To resolve this we use, positional encoding
*

    <figure><img src="../../.gitbook/assets/{09D0E7FB-7D54-4B60-898D-7E82093AD3F0}.png" alt=""><figcaption></figcaption></figure>
* As per the paper - Attention is all you need - Along with embedding vector, we will create positional encoded vector
* This positional encoded vector will be added with encoded vector ⇒ This vector will be responsible for telling which word is at which position
* For large text, the number of words will be very large
* <mark style="color:purple;background-color:purple;">**Added only to encoder 1, output of encoder 1 will be propagated to subsequent encoders**</mark>

Types of Position encoding&#x20;

1. Sinusoidal Position Encoding:

* <mark style="color:purple;background-color:purple;">**It uses sine and cosine function of different frequencies to create positional encodings**</mark>
*

    <figure><img src="../../.gitbook/assets/{FBF9A4E3-7E52-4916-82E9-03130052DDF6}.png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/{77B53AD4-1081-42DC-98DC-A4E23D4E514D}.png" alt=""><figcaption></figcaption></figure>

2. Learned Position Encoding: Learned during training
