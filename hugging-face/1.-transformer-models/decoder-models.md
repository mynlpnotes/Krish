# Decoder Models

* Only the decoder of a Transformer model.
* At each stage, for a given word the attention layers can only access the words positioned before it in the sentence.&#x20;
* These models are often called _auto-regressive models_
* The pretraining of decoder models usually revolves around predicting the next word in the sentence.
* These models are best suited for tasks involving text generation.
* [CTRL](https://huggingface.co/transformers/model_doc/ctrl)
* [GPT](https://huggingface.co/docs/transformers/model_doc/openai-gpt)
* [GPT-2](https://huggingface.co/transformers/model_doc/gpt2)
* [Transformer XL](https://huggingface.co/transformers/model_doc/transfo-xl)
