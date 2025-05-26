# 🟢 Loading and Understanding Dataset and Feature Engineering

```python
import numpy as np
import tensorflow as tf
from tensorflow.keras.datasets import imdb
from tensorflow.keras.preprocessing import sequence
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Embedding,SimpleRNN,Dense

## Load the imdb dataset
max_features=10000 ##vocabulary size
(X_train,y_train),(X_test,y_test)=imdb.load_data(num_words=max_features)

# Print the shape of the data
print(f'Training data shape: {X_train.shape}, Training labels shape: {y_train.shape}')
print(f'Testing data shape: {X_train.shape}, Testing labels shape: {y_test.shape}')

X_train[0],y_train[0]
# X_train will already have OHE of every word

## Inspect a sample review and its label
sample_review=X_train[0]
sample_label=y_train[0]


### Mapping of words index back to words(for understanding)
word_index=imdb.get_word_index()
#word_index
reverse_word_index = {value: key for key, value in word_index.items()}
reverse_word_index
#{34701: 'fawn',   52006: 'tsukino',   52007: 'nunnery',
# 16816: 'sonja',  63951: 'vani',      1408: 'woods',
# 16115: 'spiders',  2345: 'hanging',  2289: 'woody', .....}

decoded_review = ' '.join([reverse_word_index.get(i - 3, '?') for i in sample_review])

from tensorflow.keras.preprocessing import sequence

max_len=500

X_train=sequence.pad_sequences(X_train,maxlen=max_len)
X_test = sequence.pad_sequences(X_test, maxlen=max_len)

```
