# Tokenizer

* Each token has id
* Sentence ⇒ Tokens ⇒ ID
* Tokenizer also add SOS and EOS tokens - Start of sentence, End of sentence
* This will be passed to Model for embedding, attention etc
* Every model has its own tokenizer

```python
from transformers import BertTokenizerFast
tokenizer = BertTokenizerFast.from_pretrained("bert-base-uncased")

sequence1 = "Using a Transformer network is simple"
sequence2 = "It is very powerful"

res = tokenizer(sequence1,sequence2)
print(res)

# {'input_ids': [101, 2478, 1037, 10938, 2121, 2897, 2003, 3722, 102, 
# 2009, 2003, 2200, 3928, 102], 'token_type_ids': [0, 0, 0, 0, 0, 0, 0, 0, 0,
# 1, 1, 1, 1, 1], 'attention_mask': [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]}

sequence = "Using a Transformer network is simple"
tokens = tokenizer.tokenize(sequence)
print(tokens)
# ['using', 'a', 'transform', '##er', 'network', 'is', 'simple']

ids = tokenizer.convert_tokens_to_ids(tokens)
print(ids)
# [2478, 1037, 10938, 2121, 2897, 2003, 3722]

decoded_string = tokenizer.decode(ids)
print(decoded_string)
# using a transformer network is simple
```
