# Sentence embedding using transformers

```python
import torch
from transformers import BertTokenizer, BertModel
import random

from sklearn.metrics.pairwise import cosine_similarity
random_seed=42
random.seed(random_seed)
torch.manual_seed(random_seed)

tokenizer=BertTokenizer.from_pretrained("bert-base-uncased")

model=BertModel.from_pretrained("bert-base-uncased")

text="follow sunny for genai learning"

encoding=tokenizer.batch_encode_plus([text],padding=True,truncation=True,return_tensors="pt",add_special_tokens=True)

input_ids=encoding["input_ids"]

attention_mask=encoding["attention_mask"]

with torch.no_grad():
  outputs=model(input_ids, attention_mask=attention_mask)
  word_embeddings=outputs.last_hidden_state

word_embeddings.shape
# torch.Size([1, 8, 768])

input_ids[0]
tensor([  101,  3582, 11559,  2005,  8991,  4886,  4083,   102])

decode=tokenizer.decode(input_ids[0],skip_special_tokens=True)
decode
# 'follow sunny for genai learning'
```
