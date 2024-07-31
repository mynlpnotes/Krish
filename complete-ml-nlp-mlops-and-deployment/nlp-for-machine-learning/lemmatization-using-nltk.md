# Lemmatization using NLTK

* Lemmatization technique is like stemming.&#x20;
* The output we will get after lemmatization is called ‘lemma’, which is a root word rather than root stem, the output of stemming.&#x20;
* After lemmatization, we will be getting a valid word that means the same thing.
* Here we also give pos tag&#x20;
* If we give as 'n' then the word will be treated as noun
* v - verb
* a - adjective
* r - adverb
* This takes more time than stemming

```python
from nltk.stem import WordNetLemmatizer
lemmatizer=WordNetLemmatizer()
lemmatizer.lemmatize(word,pos='v')
# history ----> history
# finalized ----> finalize
# goes ----> go
# fairly ---> fairly
# sportingly ----> sportingly
```
