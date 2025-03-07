# 🟢 Different Architectures

* Different architectures for different tasks
  * `*Model` (retrieve the hidden states)
  * `*ForCausalLM`
  * `*ForMaskedLM`
  * `*ForMultipleChoice`
  * `*ForQuestionAnswering`
  * `*ForSequenceClassification`
  * `*ForTokenClassification`
  * and others 🤗
* <mark style="color:purple;background-color:purple;">**Those are not probabilities but**</mark><mark style="color:purple;background-color:purple;">**&#x20;**</mark>_<mark style="color:purple;background-color:purple;">**logits**</mark>_<mark style="color:purple;background-color:purple;">**, the raw, unnormalized scores outputted by the last layer of the model. To be converted to probabilities, they need to go through a**</mark> [<mark style="color:purple;background-color:purple;">**SoftMax**</mark>](https://en.wikipedia.org/wiki/Softmax_function) <mark style="color:purple;background-color:purple;">**layer**</mark>

```python
from transformers import AutoModelForSequenceClassification

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
model = AutoModelForSequenceClassification.from_pretrained(checkpoint)
outputs = model(**inputs)
print(outputs.logits.shape)
# torch.Size([2, 2])

print(outputs.logits)
tensor([[-1.5607,  1.6123],
        [ 4.1692, -3.3464]], grad_fn=<AddmmBackward>)
```

<mark style="color:purple;background-color:purple;">**Post processing the outputs:**</mark>

```python
import torch

predictions = torch.nn.functional.softmax(outputs.logits, dim=-1)
print(predictions)
tensor([[4.0195e-02, 9.5980e-01],
        [9.9946e-01, 5.4418e-04]], grad_fn=<SoftmaxBackward>)
# the model predicted [0.0402, 0.9598] for the first sentence and
# [0.9995, 0.0005] for the second one        

model.config.id2label
# {0: 'NEGATIVE', 1: 'POSITIVE'}
```
