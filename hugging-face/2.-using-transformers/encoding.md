# Encoding

* Translating text to numbers
* 2 step process:
  * Tokenization
  * Conversion to input ids
* We need to instantiate the tokenizer using the name of the model, to make sure we use the same rules that were used when the model was pretrained.

```python
# Subword tokenizer is used here

from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("bert-base-cased")

sequence = "Using a Transformer network is simple"
tokens = tokenizer.tokenize(sequence)

print(tokens)
# ['Using', 'a', 'transform', '##er', 'network', 'is', 'simple']

ids = tokenizer.convert_tokens_to_ids(tokens)
print(ids)
# [7993, 170, 11303, 1200, 2443, 1110, 3014]
```

Decoder:

* Vocabulary indices, we want to get a string

```python
decoded_string = tokenizer.decode([7993, 170, 11303, 1200, 2443, 1110, 3014])
print(decoded_string)
# 'Using a Transformer network is simple'
```
