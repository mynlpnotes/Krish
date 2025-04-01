# Training the Transformer

**Data Preparation:**

* Data cleaning ⇒ Deduplication
* Tokenization ⇒ Using byte pair encoding and unigram tokenization
* Split into train and test

**Training and Loss Function:**

* Batch of input is taken
* In unsupervised pre-training, the target is derived from input
* loss is calculated
* Gradients are calculated and weights are updated



**Decoder only:**

* Pre-trained on language modelling task
* The target sequence for the decoder is simply a shifted version of the input  &#x20;sequence

**Encoder only:**

* BERT
* pre-trained by corrupting the input sequence  &#x20;in some way and having the model try to reconstruct it
* Masked language modelling

**Encoder-decoder:**

* Trained on seq2seq tasks like translation, question answering, summarization
*
