# 🟢 What and Why to use Transformers

* Type of <mark style="color:purple;background-color:purple;">**DL model that uses self attention mechanism**</mark> to analyze and process natural language data
* They are <mark style="color:purple;background-color:purple;">**encoder decoder models**</mark> that can be used for many applications including machine translation (Seq2Seq task)
* <mark style="color:purple;background-color:purple;">**Problem with attention mechanism: Cannot send words parallely, so no scalability**</mark>
  * We send words to encoder decoder based on each timestamp
  * So we parallelly cannot send all the words ⇒ So model will not be scalable
  * If dataset is huge, encoder decoder will not be scalable w.r.t training
* Transformers does not use LSTM/RNN <mark style="color:purple;background-color:purple;">**they use self attention modules ⇒ All the words will be parallelly sent for processing**</mark>
* As we keep on increasing the dataset, we get amazing SOTA models
* Transformers are <mark style="color:purple;background-color:purple;">**also used in multi modal tasks**</mark> (NLP + Image ...)
* Transformers have changed the AI space&#x20;
* BERT, GPT ⇒ Trained with huge data ⇒ Can directly use transfer learning
* Based on this lot of LLM models for GenAI have been developed
* <mark style="color:purple;background-color:purple;">**Contextual Embeddings: get vector in relation with other words**</mark>
  * &#x20;When we pass the data in embedding layer
  * So embedding layer will give vector for each word
  * We should always to try to get vector in relation with other words
  *

      <figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>
