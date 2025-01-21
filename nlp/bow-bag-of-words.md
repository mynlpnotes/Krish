# BOW - Bag of words

* Was effective till 2018, 2019
* Frequency based method

|    | People | Watch | Cricket | Give | Comments |
| -- | ------ | ----- | ------- | ---- | -------- |
| D1 | 1      | 1     | 1       | 0    | 0        |
| D2 | 0      | 1     | 2       | 0    | 0        |
| D3 | 1      | 0     | 0       | 1    | 1        |
| D4 | 0      | 0     | 1       | 1    | 1        |

* D1 ⇒ \[ 1 1 1 0 0]

**Pros:**

* Simple

**Cons:**

* Sparsity
* Not capturing semantic info
* OOV

```python
from sklearn.feature_extraction.text import CountVectorizer

BOW=CountVectorizer()
document_matrix=BOW.fit_transform(data["text"])
BOW.vocabulary_
#{'people': 3, 'watch': 4, 'cricket': 1, 'give': 2, 'comment': 0}

document_matrix[0].toarray()
# array([[0, 1, 0, 1, 1]])
```
