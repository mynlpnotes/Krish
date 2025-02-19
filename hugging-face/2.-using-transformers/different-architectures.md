# Different Architectures

* Different architectures for different tasks
  * `*Model` (retrieve the hidden states)
  * `*ForCausalLM`
  * `*ForMaskedLM`
  * `*ForMultipleChoice`
  * `*ForQuestionAnswering`
  * `*ForSequenceClassification`
  * `*ForTokenClassification`
  * and others 🤗
* Those are not probabilities but _logits_, the raw, unnormalized scores outputted by the last layer of the model. To be converted to probabilities, they need to go through a [SoftMax](https://en.wikipedia.org/wiki/Softmax_function) layer

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

**Post processing the outputs:**

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
