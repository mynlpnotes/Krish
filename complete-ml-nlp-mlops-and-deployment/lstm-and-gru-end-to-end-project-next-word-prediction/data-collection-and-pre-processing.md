# Data Collection and Pre Processing

```python
## Data Collection
import nltk
nltk.download('gutenberg')
from nltk.corpus import gutenberg
import  pandas as pd

## load the dataset
data=gutenberg.raw('shakespeare-hamlet.txt')
## save to a file
with open('hamlet.txt','w') as file:
    file.write(data)
    
## Data Preprocessing
import numpy as np
from tensorflow.keras.preprocessing.text import Tokenizer
from tensorflow.keras.preprocessing.sequence import pad_sequences
from sklearn.model_selection import train_test_split

##laod the dataset
with open('hamlet.txt','r') as file:
    text=file.read().lower()

## Tokenize the text-creating indexes for words
tokenizer=Tokenizer()
tokenizer.fit_on_texts([text])
total_words=len(tokenizer.word_index)+1
total_words

tokenizer.word_index
#{'the': 1 'and': 2, 'to': 3, 'of': 4, 'i': 5,.....}

## create inoput sequences
input_sequences=[]
for line in text.split('\n'):
    token_list=tokenizer.texts_to_sequences([line])[0]
    for i in range(1,len(token_list)):
        n_gram_sequence=token_list[:i+1]
        input_sequences.append(n_gram_sequence)
#[[1, 687],
# [1, 687, 4],
# [1, 687, 4, 45],
# [1, 687, 4, 45, 41],
# [1, 687, 4, 45, 41, 1886],
# [1, 687, 4, 45, 41, 1886, 1887],
# [1, 687, 4, 45, 41, 1886, 1887, 1888],.....]

## Pad Sequences
max_sequence_len=max([len(x) for x in input_sequences])
max_sequence_len

input_sequences=np.array(pad_sequences(input_sequences,maxlen=max_sequence_len,padding='pre'))
input_sequences

##create predicitors and label
# Last letter will go in y, remaining will go in x
import tensorflow as tf
x,y=input_sequences[:,:-1],input_sequences[:,-1]

y
# Index where there is value, others will be 0
#array([ 687,    4,   45, ..., 1047,    4,  193])
```
