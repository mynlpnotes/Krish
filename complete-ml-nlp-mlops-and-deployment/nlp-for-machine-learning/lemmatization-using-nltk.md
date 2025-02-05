# 🟠 Lemmatization using NLTK

* Lemmatization technique is like stemming.&#x20;
* The output we will get after lemmatization is called ‘lemma’, <mark style="color:purple;background-color:purple;">**which is a root word rather than root stem**</mark>, the output of stemming.&#x20;
* <mark style="color:purple;background-color:purple;">**After lemmatization, we will be getting a valid word that means the same thing.**</mark>
* <mark style="color:purple;background-color:purple;">**Used in Text summarization, language translation, chatbots**</mark>
* Here we also give pos tag
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
