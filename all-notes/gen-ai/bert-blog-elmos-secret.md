# BERT Blog - ELMo's secret

* ELMo gained its language understanding from being trained to predict the next word in a sequence of words - a task called _Language Modeling_.
*

    <figure><img src="../../.gitbook/assets/image (574).png" alt=""><figcaption><p>A step in the pre-training process of ELMo: Given “Let’s stick to” as input, predict the next most likely word – a <em>language modeling</em> task</p></figcaption></figure>
* ELMo actually goes a step further and trains a bi-directional LSTM – so that its language model doesn’t only have a sense of the next word, but also the previous word.

Step 1:

*

    <figure><img src="../../.gitbook/assets/image (575).png" alt=""><figcaption></figcaption></figure>

Step 2:

*

    <figure><img src="../../.gitbook/assets/image (576).png" alt=""><figcaption></figcaption></figure>
