# TF-IDF

* Refer Krish Notes

```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf=TfidfVectorizer()
tfidf.fit_transform(data["text"]).toarray()
#array([[0.        , 0.49681612, 0.        , 0.61366674, 0.61366674],
#       [0.        , 0.8508161 , 0.        , 0.        , 0.52546357],
#       [0.57735027, 0.        , 0.57735027, 0.57735027, 0.        ],
#       [0.61366674, 0.49681612, 0.61366674, 0.        , 0.        ]])

feature_names = tfidf.get_feature_names_out()
#Feature Names: ['comment' 'cricket' 'give' 'people' 'watch']
```
