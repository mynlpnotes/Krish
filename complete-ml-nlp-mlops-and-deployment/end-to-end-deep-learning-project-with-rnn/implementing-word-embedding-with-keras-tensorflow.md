# 🟢 Implementing Word Embedding with Keras Tensorflow

* <mark style="color:purple;background-color:purple;">**We need all the sentences to be of equal size, so that's why we use padding**</mark>
* <mark style="color:purple;background-color:purple;">**We 1st do OHE, then add padding to make them equal lenght and then we do embedding**</mark>
* We can use pre padding - 0 will be added in front
* Post padding - 0 will be added at the end

```python
from tensorflow.keras.preprocessing.text import one_hot

### sentences
sent=[  'the glass of milk',
     'the glass of juice',
     'the cup of tea',
    'I am a good boy',
     'I am a good developer',
     'understand the meaning of words',
     'your videos are good',]

voc_size=10000

one_hot_repr=[one_hot(words,voc_size)for words in sent]
# Here we will be getting index which will be 1 for each, remaining all will be 0
#[[6186, 6775, 637, 4895],
# [6186, 6775, 637, 5462],
# [6186, 7872, 637, 7943],
# [7793, 3440, 840, 9701, 4879],
# [7793, 3440, 840, 9701, 1294],
# [932, 6186, 733, 637, 1731],
# [2258, 439, 5397, 9701]]

## word Embedding Representation

from tensorflow.keras.layers import Embedding
from tensorflow.keras.utils import pad_sequences
from tensorflow.keras.models import Sequential

import numpy as np

sent_length=8
embedded_docs=pad_sequences(one_hot_repr,padding='pre',maxlen=sent_length)
print(embedded_docs)
#[[   0    0    0    0 6186 6775  637 4895]
# [   0    0    0    0 6186 6775  637 5462]
# [   0    0    0    0 6186 7872  637 7943]
# [   0    0    0 7793 3440  840 9701 4879]
# [   0    0    0 7793 3440  840 9701 1294]
# [   0    0    0  932 6186  733  637 1731]
# [   0    0    0    0 2258  439 5397 9701]]

dim=10

model=Sequential()
model.add(Embedding(voc_size,dim,input_length=sent_length))
model.compile('adam','mse')

model.summary()
model.predict(embedded_docs)

embedded_docs[0]
array([   0,    0,    0,    0, 6186, 6775,  637, 4895])
model.predict(embedded_docs[0])
#array([[ 0.01453609,  0.03697893,  0.02267558,  0.01149287, -0.03695335,
#         0.01416664,  0.03655917,  0.00734384,  0.03028754,  0.00339943],
#       [ 0.01453609,  0.03697893,  0.02267558,  0.01149287, -0.03695335,
#         0.01416664,  0.03655917,  0.00734384,  0.03028754,  0.00339943],
#       [ 0.01453609,  0.03697893,  0.02267558,  0.01149287, -0.03695335,
#         0.01416664,  0.03655917,  0.00734384,  0.03028754,  0.00339943],
#       [ 0.01453609,  0.03697893,  0.02267558,  0.01149287, -0.03695335,
#         0.01416664,  0.03655917,  0.00734384,  0.03028754,  0.00339943],
#       [-0.03792738,  0.01958679, -0.04232483, -0.03475742,  0.02182527,
#         0.01143194, -0.03125288,  0.02584182,  0.0050171 ,  0.04725457],
#       [-0.02213118,  0.00730393,  0.02797868, -0.02386508, -0.0024281 ,
#         0.04419583, -0.02011771, -0.00502002, -0.03373672, -0.04126013],
#       [-0.02629154,  0.02487988, -0.02824695,  0.0302802 , -0.01835672,
#        -0.00683415,  0.01606056, -0.04426531, -0.03801771, -0.04581957],
#       [-0.01679759,  0.04462079,  0.02781102, -0.04639838,  0.0059711 ,
#         0.00940369, -0.01027383,  0.01697389, -0.01460341,  0.02758609]],
#      dtype=float32)
```
