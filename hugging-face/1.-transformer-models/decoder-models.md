# 🟢 Decoder Models

* Only the decoder of a Transformer model.
* <mark style="color:purple;background-color:purple;">**At each stage, for a given word the attention layers can only access the words positioned before it in the sentence.**</mark>&#x20;
* These models are often called _auto-regressive models_
* <mark style="color:purple;background-color:purple;">**The pretraining of decoder models usually revolves around predicting the next word in the sentence.**</mark>
* <mark style="color:purple;background-color:purple;">**These models are best suited for tasks involving text generation.**</mark>
* [CTRL](https://huggingface.co/transformers/model_doc/ctrl)
* [GPT](https://huggingface.co/docs/transformers/model_doc/openai-gpt)
* [GPT-2](https://huggingface.co/transformers/model_doc/gpt2)
* [Transformer XL](https://huggingface.co/transformers/model_doc/transfo-xl)
