# BOW implementation using NLTK

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
