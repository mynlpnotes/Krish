# Sentence embedding using sentence transformer

* all-mpnet-base-v2 is transformer based model

```python
from sentence_transformers import  SentenceTransformer

model = SentenceTransformer('all-mpnet-base-v2')

sentences[0] #'I ate dinner.'

model.encode(sentences[0])
#array([-1.58597678e-02,  4.59826551e-02, -1.46349585e-02, -4.85908687e-02,
#       -3.60319996e-03,  3.17664109e-02, -3.27771641e-02,  2.11895313e-02,
#        1.07366042e-02,  2.50182096e-02,  1.58237889e-02,  1.24069359e-02,
#        1.62089840e-02, -1.30434325e-02,  4.58446629e-02,  4.40269858e-02,....]
```
