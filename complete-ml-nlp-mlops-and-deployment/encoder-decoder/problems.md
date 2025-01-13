# 🟢 Problems

* &#x20;From encoder we will be getting context vector (long term memory and short term)
* Context vector represents the entire sentence
* Researchers used sentence of varying length, and evaluated BLEU score
* <mark style="color:purple;background-color:purple;">**It was observed as sentence was kept increasing, BLEU score started decreasing**</mark>
* Context vector will have more information about the timestamp at the end
* <mark style="color:purple;background-color:purple;">**The words which were at t = 1, t = 2 will have less info in context vector**</mark>
* For fixing this, we used attention mechanism (For longer sentences along with context vector we will pass additional context)
*

    <figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
