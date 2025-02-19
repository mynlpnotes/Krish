# Inference

* &#x20;The tokenizer converts these to vocabulary indices which are typically called _input IDs_.

```python
import torch

sequences = ["Hello!", "Cool.", "Nice!"]

encoded_sequences = [
    [101, 7592, 999, 102],
    [101, 4658, 1012, 102],
    [101, 3835, 999, 102],
]

model_inputs = torch.tensor(encoded_sequences)
output = model(model_inputs)
```
