# ✈️ Bidirectional RNN

* It can be Bi-directional RNN/LSTM/GRU
* &#x20;Example:
* KRISH EATS \_\_\_\_ IN BANGALORE
* Here we need to do prediction for 3rd word
* <mark style="color:purple;background-color:purple;">**For this if we use simple RNN/LSTM/GRU then the prediction will be based on 1st 2 words**</mark>
* <mark style="color:purple;background-color:purple;">**But here we should also need context of upcoming words**</mark>
* If we have 2nd sentence: KRISH EATS \_\_\_ IN PARIS
* When the place changes, the specific word can also change
*   So bidirectional RNN fixes this

    <figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Here if y3 needs context of the upcoming words, then we will have 1 more RNN which will have words coming in the reverse direction**</mark>
* <mark style="color:purple;background-color:purple;">**Outputs of both RNN will be combined to get the final output**</mark>
* We will be passing data L to R in the 1st RNN
* We will pass data R to L in the 2nd RNN
* So for prediction of y3, we will have context of X11 X12 and also X14 X15 available&#x20;
*

    <figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
