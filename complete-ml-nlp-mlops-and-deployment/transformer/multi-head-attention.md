# Multi head attention

* X is having the embedding of words
* We do dot operation of X and W to get Q, K and V
* We do dot product of Q and Key then scaling then softmax and then multiply by value
* This is how we get self attention
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
* We can also create multiple attention heads for the same words
* Initially we initialize some different words and then calculated contextual vector&#x20;
* Similarly we can initialize some other vector which may capture importance of some other important words and we may get another contextual vector
*   Multi head attention attends models ability to focus on different positions of tokens

    <figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>
