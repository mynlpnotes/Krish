# 🟢 Stopwords

* <mark style="color:purple;background-color:purple;">**Remove the common language words which are not important for the model**</mark>

```python
from nltk.corpus import stopwords
nltk.download('stopwords')

stopwords.words('english') # set of all english stopwords
stopwords.words('arabic')

## Apply Stopwords And Filter And then Apply Stemming
# Same way we can apply snowball stemmer or lematization
for i in range(len(sentences)):
    words=nltk.word_tokenize(sentences[i])
    wd=[stemmer.stem(w) for w in words if w not in set(stopwords.words('english'))]
    sentences[i]=' '.join(wd)# converting all the list of words into sentences
```
