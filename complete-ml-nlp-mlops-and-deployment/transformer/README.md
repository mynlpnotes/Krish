# Transformer

* Type of DL model that uses self attention mechanism to analyze and process natural language data
* They are encoder decoder models that can be used for many applications including machine translation (Seq2Seq task)
* Problem with attention mechanism:
  * We send words to encoder decoder based on each timestamp
  * So we parallelly cannot send all the words ⇒ So model will not be scalable
  * If dataset is huge, encoder decoder will not be scalable w.r.t training
* Transformers does not use LSTM/RNN they use self attention modules ⇒ All the words will be parallelly sent for processing
* As we keep on increasing the dataset, we get amazing SOTA models
* Transformers are also used in multi modal tasks (NLP + Image ...)
* Transformers have changed the AI space&#x20;
* BERT, GPT ⇒ Trained with huge data ⇒ Can directly use transfer learning
* Based on this lot of LLM models for GenAI have been developed
* Contextual Embeddings:
  * &#x20;When we pass the data in embedding layer
  * So embedding layer will give vector for each word
  * We should always to try to get vector in relation with other words
  *

      <figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
