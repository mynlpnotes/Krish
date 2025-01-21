# 🟢 BOW implementation using NLTK

<mark style="color:purple;background-color:purple;">**Algo explained:**</mark>

* <mark style="color:purple;background-color:purple;">Remove non alphabetic words using regular expression</mark>
* <mark style="color:purple;background-color:purple;">Lowercase and split</mark>
* <mark style="color:purple;background-color:purple;">Remove stopwords</mark>
* <mark style="color:purple;background-color:purple;">Get the stem word</mark>
* <mark style="color:purple;background-color:purple;">Combine and form the corpus</mark>
* <mark style="color:purple;background-color:purple;">From nltk use count vectorizer.fit\_transform</mark>

```python
# Spam and Ham example

# Data cleaning and Pre processing
# remove if not alphabets
review=re.sub('[^a-zA-z]',' ',messages['message'][i])
# lowercase
# remove stopwords
# apply stemming
corpus=[]
for i in range(0,len(messages)):
    review=re.sub('[^a-zA-z]',' ',messages['message'][i])
    review=review.lower()
    review=review.split()
    review=[ps.stem(word) for word in review if not word in stopwords.words('english')]
    review=' '.join(review)
    corpus.append(review)

## Create the Bag OF Words model
from sklearn.feature_extraction.text import CountVectorizer
## for Binary BOW enable binary=True
cv=CountVectorizer(max_features=100,binary=True)
X=cv.fit_transform(corpus).toarray()

cv.vocabulary_
# {'go': 22, 'great': 25, 'got': 24, ......}

```
