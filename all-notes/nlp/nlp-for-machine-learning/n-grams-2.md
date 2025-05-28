# N Grams - 2

* We make pairs ⇒ Context of the data was captured
* N = 1 ⇒ Single word (Unigram) ⇒ Output will be same as BOW
* N = 2 ⇒ Pair of 2 words (Bi gram)
* N = 3 ⇒ Pair of 3 words (Tri gram)
* We make pairs as per N to form the vocabulary and follow the same procedure after that as used in BOW

**Pros:**

* Simple to use
* Context is captured

**Cons:**

* Sparse matrix
* OOV issue

```python
from sklearn.feature_extraction.text import CountVectorizer

bigram=CountVectorizer(ngram_range=(2,2))
bigramvocab=bigram.fit_transform(data["text"])

bigram.vocabulary_
#{'people watch': 4, 'watch cricket': 5, 'cricket watch': 1, 'people give': 3,
# 'give comment': 2, 'cricket give': 0}

mix=CountVectorizer(ngram_range=(1,3))
mix_vocab=mix.fit_transform(data["text"])
```
