# Word2Vec

* If any error comes in download, then it can be numpy version mismatch issue
* We should create a new environment and install gensim, numpy
* Its a dense matrix

```python
from gensim.models import Word2Vec,KeyedVectors
import gensim.downloader as api

model = api.load('word2vec-google-news-300')

model["sunny"] # Will return array of 300


```
