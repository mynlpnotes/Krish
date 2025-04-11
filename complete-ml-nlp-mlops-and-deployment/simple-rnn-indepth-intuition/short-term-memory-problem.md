---
hidden: true
---

# 🟢 Short term memory problem

**Simple RNN example:**

*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
* In Right, if we give sequential data, it will not remember the context
* In RNN, we have a feedback mechanism, to make it remember things



***

**Chatbot example:**

* What time is it?                Asking for time
* At t = 0, we pass what to the network
* At t = 1, we pass time and also previous information and so on
*

    <figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>
* There is only a single network, and at different times, we will pass input sequentially
* If this is a longer sentence:
*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>
* If we see the diagram, by t = 4, already the context of what is very little
* After the timestamp of 5, if we start putting the next words, then it will remember the last 5 words and start forgetting the previous input
* <mark style="color:purple;background-color:green;">**If the input is long, then it starts forgetting previous input, This is known as short term memory problem**</mark>
* RNN suffers from this issue



***

&#x20;**Time series:**

* Sales data
* &#x20;It is also sequential data
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
* This can also be solved using RNN or LSTM
