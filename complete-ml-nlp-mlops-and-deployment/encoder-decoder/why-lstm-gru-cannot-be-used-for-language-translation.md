# 🟢 Why LSTM/GRU cannot be used for Language Translation

* <mark style="color:purple;background-color:purple;">**Variable length in input and output**</mark>
* <mark style="color:purple;background-color:purple;">**Long term dependencies are not captured**</mark>
* <mark style="color:purple;background-color:purple;">**Only single hidden state so all the context cannot be captured**</mark>&#x20;



* Fixed length input/output mapping
* Translation requires capturing dependencies across long sequences.
* LSTMs/GRUs, despite mitigating vanishing gradients, struggle to retain long-term context effectively.
* Traditional LSTMs/GRUs rely on a **single final hidden state** to encode the entire input sequence.
* This leads to loss of information, especially for long or complex sentence
