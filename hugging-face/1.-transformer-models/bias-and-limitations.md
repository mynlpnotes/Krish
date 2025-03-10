# 🟢 Bias and Limitations

* <mark style="color:purple;background-color:purple;">**Original model you are using could very easily generate sexist, racist, or homophobic content.**</mark>&#x20;
* Fine-tuning the model on your data won’t make this intrinsic bias disappear

```python
from transformers import pipeline

unmasker = pipeline("fill-mask", model="bert-base-uncased")
result = unmasker("This man works as a [MASK].")
print([r["token_str"] for r in result])

result = unmasker("This woman works as a [MASK].")
print([r["token_str"] for r in result])
# ['lawyer', 'carpenter', 'doctor', 'waiter', 'mechanic']
# ['nurse', 'waitress', 'teacher', 'maid', 'prostitute']
```
