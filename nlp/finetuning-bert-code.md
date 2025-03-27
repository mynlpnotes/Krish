# Finetuning - BERT - Code

* &#x20;

```python
import datasets
import numpy as np
from transformers import BertTokenizerFast
from transformers import DataCollatorForTokenClassification
from transformers import AutoModelForTokenClassification

import os
os.environ["WANDB_DISABLED"] = "true"

conll2003 = datasets.load_dataset("conll2003")
#CoNLL-2003 ek NER (Named Entity Recognition) dataset hai, jo 2003 ke 
#CoNLL (Conference on Computational Natural Language Learning) me introduce
# kiya gaya tha. Yeh dataset news articles ka collection hai aur 4 entity 
#types detect karne ke liye use hota hai:
#PER → Person (e.g., "Elon Musk")
#LOC → Location (e.g., "India", "New York")
#ORG → Organization (e.g., "Google", "NASA")
#MISC → Miscellaneous (e.g., "Olympics", "iPhone")

conll2003
#DatasetDict({
#    train: Dataset({
#        features: ['id', 'tokens', 'pos_tags', 'chunk_tags', 'ner_tags'],
#        num_rows: 14041
#    })
#    validation: Dataset({
#        features: ['id', 'tokens', 'pos_tags', 'chunk_tags', 'ner_tags'],
#        num_rows: 3250
#    })
#    test: Dataset({
#        features: ['id', 'tokens', 'pos_tags', 'chunk_tags', 'ner_tags'],
#        num_rows: 3453
#    })
#})

conll2003["train"]. features['ner_tags']
# Sequence(feature=ClassLabel(names=['O', 'B-PER', 'I-PER', 'B-ORG',
# 'I-ORG', 'B-LOC', 'I-LOC', 'B-MISC', 'I-MISC'], id=None), length=-1, id=None)

conll2003["train"][0]
#{'id': '0',
# 'tokens': ['EU',
#  'rejects',
#  'German',
#  'call',
#  'to',
#  'boycott',
#  'British',
#  'lamb',
#  '.'],
# 'pos_tags': [22, 42, 16, 21, 35, 37, 16, 21, 7],
# 'chunk_tags': [11, 21, 11, 12, 21, 22, 11, 12, 0],
# 'ner_tags': [3, 0, 7, 0, 0, 0, 7, 0, 0]}

example_text=conll2003['train'][0]

example_text["tokens"]
# ['EU', 'rejects', 'German', 'call', 'to', 'boycott', 'British', 'lamb', '.']

from transformers import pipeline
model_name="sunny199/NER-Model-Fine-Tuned"
tokenizer = BertTokenizerFast.from_pretrained("/content/tokenizer")


```
