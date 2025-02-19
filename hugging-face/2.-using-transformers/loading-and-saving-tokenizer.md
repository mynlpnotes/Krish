# Loading and Saving Tokenizer

```python
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-cased")

tokenizer("Using a Transformer network is simple")
#{'input_ids': [101, 7993, 170, 11303, 1200, 2443, 1110, 3014, 102],
# 'token_type_ids': [0, 0, 0, 0, 0, 0, 0, 0, 0],
# 'attention_mask': [1, 1, 1, 1, 1, 1, 1, 1, 1]}

tokenizer.save_pretrained("directory_on_my_computer")
```
