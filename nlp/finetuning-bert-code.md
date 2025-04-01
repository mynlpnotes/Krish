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

# We can use the pretrained model which is trained on internet data for inferencing to 
# check the results
# We can fine tune this model
from transformers import pipeline

model_name = "bert-base-uncased"

nlp_pipeline=pipeline("ner",model=model_name,tokenizer=tokenizer)

example="Sunny is Data Scientist and Generative AI Engineer"
nlp_pipeline(example)
# [{'entity': 'B-PER',
#   'score': 0.9791179,
#   'index': 1,
#   'word': 'sunny',
#   'start': 0,
#   'end': 5}]

# We can use the below function to align tokens and labels
def tokenize_and_align_labels(examples, label_all_tokens=True):

    #tokeinze ids
    tokenized_inputs = tokenizer(examples["tokens"], truncation=True, is_split_into_words=True)
    labels = []


    for i, label in enumerate(examples["ner_tags"]):
        word_ids = tokenized_inputs.word_ids(batch_index=i)
        # word_ids() => Return a list mapping the tokens
        # to their actual word in the initial sentence.
        # It Returns a list indicating the word corresponding to each token.

        previous_word_idx = None
        label_ids = []
        # Special tokens like `` and `<\s>` are originally mapped to None
        # We need to set the label to -100 so they are automatically ignored in the loss function.
        for word_idx in word_ids:
            if word_idx is None:
                # set –100 as the label for these special tokens
                label_ids.append(-100)

            # For the other tokens in a word, we set the label to either the current label or -100, depending on
            # the label_all_tokens flag.
            elif word_idx != previous_word_idx:
                # if current word_idx is != prev then its the most regular case
                # and add the corresponding token
                label_ids.append(label[word_idx])
            else:
                # to take care of sub-words which have the same word_idx
                # set -100 as well for them, but only if label_all_tokens == False
                label_ids.append(label[word_idx] if label_all_tokens else -100)
                # mask the subword representations after the first subword

            previous_word_idx = word_idx
        labels.append(label_ids)
    tokenized_inputs["labels"] = labels
    return tokenized_inputs

q=tokenize_and_align_labels(conll2003["train"][0:1])
for token, label in zip(tokenizer.convert_ids_to_tokens(q["input_ids"][0]),q["labels"][0]):
    print(f"{token:_<40} {label}")
# [CLS]___________________________________ -100
# eu______________________________________ 3
# rejects_________________________________ 0
# german__________________________________ 7
# call____________________________________ 0
# to______________________________________ 0
# boycott_________________________________ 0
# british_________________________________ 7
# lamb____________________________________ 0
# ._______________________________________ 0
# [SEP]___________________________________ -100
    



```
