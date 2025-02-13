# 🟢 Why LSTM RNN

* <mark style="color:purple;background-color:purple;">**RNN suffered from Long term dependencies and Vanishing Gradient Problem ⇒ So LSTM was required**</mark>
* [https://colah.github.io/posts/2015-08-Understanding-LSTMs/](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)

Problems with RNN:

* We want to predict next work in sentence
* Sentence: The colour of the sky is \_\_\_\_ (Lets say answer is blue)
* For prediction there is dependency 'sky' and no further context is required
* Since sentence is small here, there wont be vanishing gradient problem
* Example: In grew up in india...... i speak fluent \_\_\_\_\_ (Hindi)
* Here further context required is name of the country
* So there is a long term dependency as there is huge gap here
* In the 1st sentence gap is less and there no dependence on context
* In the 2nd there is huge gap, so there is long term dependency
* RNN cannot solve this as it suffers from vanishing gradient problem
