# Normalization

* Removing needless whitespace, lowercasing, and/or removing accents

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
print(type(tokenizer.backend_tokenizer))

print(tokenizer.backend_tokenizer.normalizer.normalize_str("Héllò hôw are ü?"))
# 'hello how are u?'
```
