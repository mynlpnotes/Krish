# Word2Vec - Training

* **Pretrained:**
  * Google\_news\_300 - This will convert every word into 300 dimension
* **Train from scratch:**
  * If 75% of the words are there in the pretrained model, then use it otherwise better to train it
* [https://github.com/krishnaik06/NLP-Live/blob/main/Day%205-%20NLP%20Word2vec%20And%20AvgWord2vec.ipynb](https://github.com/krishnaik06/NLP-Live/blob/main/Day%205-%20NLP%20Word2vec%20And%20AvgWord2vec.ipynb)

```python
# Ham and spam classification
# 1. Do data cleaning
# 2. Convert into BOW
# 3. Apply one hot encoding to Y
# 4. Split the model
# 5. Apply on train
# 6. Check accuracy on test

from sklearn.naive_bayes import MultinomialNB
spam_detect_model = MultinomialNB().fit(X_train, y_train)
y_pred = spam_detect_model.predict(X_text)
from sklearn.metrics import accuracy_score, classification_report
score = accuracy_score(y_test, y_pred)
classification_report(y_pred, y_test) # this gives precison, recall, f1 for all the classes

# Same can also be done by applying TFIDF

## Word2Vec implementation
! pip install gensim

# for pre-trained version
import gension.downloader as api
wv = api.load('word2vec-google-news-300')
vec_king = wv['King'] # this will give the vector for king of 300 dimension

# Training from scratch
words #we will be preprocessing tokenizing and will put it all in words, words is list of list of sentences
model = gensim.model.Word2Vec(words, window = 5, min_count = 2)
model.wv.index_to_key # to see all the words
model.corpus_count
model,epochs
model.wv.similar_by_word('kid')

# Average word2vec
def avg_word2vec(doc):
    # remove out-of-vocabulary words
    #sent = [word for word in doc if word in model.wv.index_to_key]
    #print(sent)
    
    return np.mean([model.wv[word] for word in doc if word in model.wv.index_to_key],axis=0)
                #or [np.zeros(len(model.wv.index_to_key))], axis=0)



// Some code
import gensim
from gensim.model import Word2Vec, KeyedVectors
import gensim.downloader as api

wv = api.load('word2vec-google-news-300') --> This model is about 1.5GB
vec_king = wv['king'] --> this will return vector of 300 dimensions

wv.most_similar('man') --> will return list of tuples of word and cosine similarity

wv.similarity('man','king') --> will return cosine similarity

```
