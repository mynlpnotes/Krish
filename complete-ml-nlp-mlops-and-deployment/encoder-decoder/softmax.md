# 🟢 Softmax

*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
* It will predict the probability of the word at each timestamp
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>
* Here one to one mapping source and target text is not possible
* Since machine does not understand text we will encode text into numbers
* Numbers are not appropriate representation of text
* So we embed them
* Which generate v1, v2, v3
* Encoder will take information v1 then v2 and then v3 and give embedded info
* Similarly decoder will take embedded info and embedded layer info of target and it will give output
* <mark style="color:purple;background-color:purple;">**Softmax layer will give probability at each instance**</mark>
* If softmax says that v1 is having the highest probability, then we will come to know that v1 is 1, so the 1st word is main
* <mark style="color:purple;background-color:purple;">**If softmax does not give correct prediction, then it will be an error and the error will be back propagated**</mark>

&#x20;

&#x20;

&#x20;
