# Spam Ham using Tf-Idf

```python
from sklearn.feature_extraction.text import TfidfVectorizer
tv=TfidfVectorizer(max_features=2500,ngram_range=(1,2))
X_train=tv.fit_transform(X_train).toarray()
X_test=tv.transform(X_test).toarray()
```
