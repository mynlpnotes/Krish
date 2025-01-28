# 🟢 Kindle review sentiment analysis

<mark style="color:purple;background-color:purple;">**Steps:**</mark>

* <mark style="color:purple;background-color:purple;">**Remove null records from the dataset**</mark>
* <mark style="color:purple;background-color:purple;">**Check the unique value for y (0 to 5) ⇒ Convert it into 0 to 1**</mark>
* <mark style="color:purple;background-color:purple;">**Remove special characters, URL, stopwords, html tags, additional spaces**</mark>
* <mark style="color:purple;background-color:purple;">**Lemmatize the data**</mark>
* <mark style="color:purple;background-color:purple;">**On train using fit\_transform encode using tfidf/bow**</mark>
* <mark style="color:purple;background-color:purple;">**On test use transform**</mark>
* <mark style="color:purple;background-color:purple;">**Apply the algorithm**</mark>



* Dataset:
  * asin - ID of the product, like B000FA64PK
  * helpful - helpfulness rating of the review - example: 2/3.
  * overall - rating of the product.
  * reviewText - text of the review (heading).
  * reviewTime - time of the review (raw).
  * reviewerID - ID of the reviewer, like A3SPTOKDG7WBLN
  * reviewerName - name of the reviewer.
  * summary - summary of the review (description).
  * unixReviewTime - unix timestamp

```python
df=data[['reviewText','rating']]

## Missing Values
df.isnull().sum()
# No missing values

df['rating'].unique() # array([3, 5, 4, 2, 1], dtype=int64)

df['rating'].value_counts() # Check if class imbalance

## postive review is 1 and negative review is 0
df['rating']=df['rating'].apply(lambda x:0 if x<3 else 1)

df['rating'].value_counts()

# lower call the reviews
## Removing special characters
df['reviewText']=df['reviewText'].apply(lambda x:re.sub('[^a-z A-z 0-9-]+', '',x))
## Remove the stopswords
df['reviewText']=df['reviewText'].apply(lambda x:" ".join([y for y in x.split() if y not in stopwords.words('english')]))
## Remove url 
df['reviewText']=df['reviewText'].apply(lambda x: re.sub(r'(http|https|ftp|ssh)://([\w_-]+(?:(?:\.[\w_-]+)+))([\w.,@?^=%&:/~+#-]*[\w@?^=%&/~+#-])?', '' , str(x)))
## Remove html tags
df['reviewText']=df['reviewText'].apply(lambda x: BeautifulSoup(x, 'lxml').get_text())
## Remove any additional spaces
df['reviewText']=df['reviewText'].apply(lambda x: " ".join(x.split()))

# Lemmatize
df['reviewText']=df['reviewText'].apply(lambda x:lemmatize_words(x))

# Train test split

# BOW
from sklearn.feature_extraction.text import CountVectorizer
bow=CountVectorizer()
X_train_bow=bow.fit_transform(X_train).toarray()
X_test_bow=bow.transform(X_test).toarray()

from sklearn.feature_extraction.text import TfidfVectorizer
tfidf=TfidfVectorizer()
X_train_tfidf=tfidf.fit_transform(X_train).toarray()
X_test_tfidf=tfidf.transform(X_test).toarray()

# Apply Naive Bayes and check the resuls

```
