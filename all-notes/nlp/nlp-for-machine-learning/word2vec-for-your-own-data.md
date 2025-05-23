---
hidden: true
---

# 🟢 Word2Vec - For your own data

```python
from gensim.models import Word2Vec

# Example corpus
sentences = [
    ["the", "cat", "sat", "on", "the", "mat"],
    ["the", "dog", "barked", "at", "the", "cat"],
    ["cats", "are", "better", "than", "dogs"],
    ["dogs", "are", "loyal", "animals"]
]

# Train Word2Vec model
model = Word2Vec(sentences, vector_size=50, window=3, min_count=1, workers=4, sg=0)

# Save the model
model.save("word2vec_model")
```
