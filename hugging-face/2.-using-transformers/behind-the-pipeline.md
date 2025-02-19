# Behind the pipeline

* Pipeline does 3 steps ⇒ Preprocessing, Passing inputs to the models and post processing
*

    <figure><img src="../../.gitbook/assets/{B8ED59A0-0546-4FAE-A267-28984920444F}.png" alt=""><figcaption></figcaption></figure>
* Tokenizer:
  * Splitting input into tokens
  * Mapping each token to an integer
  * All the preprocessing should be done the same way as done using pre training
  * So for this we use AutoTokenizer class and use the name of our model in it
  * Output of tokenizer can be directly given to the model
  * We need to specify the type of tensors which we want
* Going through the model:
  * Use AutoModel class
  * It outputs what we’ll call hidden states, also known as features. For each model input, we’ll retrieve a high-dimensional vector representing the contextual understanding of that input by the Transformer model.

```python
from transformers import AutoModel

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
model = AutoModel.from_pretrained(checkpoint)
```

* A high dimensional vector:
  * The vector output by the Transformer module is usually large. It generally has three dimensions:
    * **Batch size**: The number of sequences processed at a time (2 in our example).
    * **Sequence length**: The length of the numerical representation of the sequence (16 in our example).
    * **Hidden size**: The vector dimension of each model input.

```python
outputs = model(**inputs)
print(outputs.last_hidden_state.shape)
# torch.Size([2, 16, 768])
```

* Model heads:
  * The output of transformer model is sent to the model head to be processed
  *

      <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
