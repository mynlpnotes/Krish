# Encoder Models

* Only uses the encoder of a transformer model
* At each stage, the attention layers can access all the words in the initial sentence
* The pretraining of these models usually revolves around somehow corrupting a given sentence (for instance, by masking random words in it) and tasking the model with finding or reconstructing the initial sentence
* Encoder models are best suited for tasks requiring an understanding of the full sentence, such as sentence classification, named entity recognition (and more generally word classification), and extractive question answering.
* [ALBERT](https://huggingface.co/docs/transformers/model_doc/albert)
* [BERT](https://huggingface.co/docs/transformers/model_doc/bert)
* [DistilBERT](https://huggingface.co/docs/transformers/model_doc/distilbert)
* [ELECTRA](https://huggingface.co/docs/transformers/model_doc/electra)
*   [RoBERTa](https://huggingface.co/docs/transformers/model_doc/roberta)

    [\
    ](https://github.com/huggingface/course/blob/main/chapters/en/chapter1/5.mdx)
