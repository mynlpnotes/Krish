# BERT Blog - OpenAI Transformer

* It turns out we don’t need an entire Transformer to adopt transfer learning and a fine-tunable language model for NLP tasks.&#x20;
* We can do with just the decoder of the transformer. The decoder is a good choice because it’s a natural choice for language modeling (predicting the next word) since it’s built to mask future tokens – a valuable feature when it’s generating a translation word by word.
*
