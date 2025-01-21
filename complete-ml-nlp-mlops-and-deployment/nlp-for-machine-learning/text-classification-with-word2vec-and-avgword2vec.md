# Text Classification with Word2Vec and AvgWord2Vec

```python
# Spam/Ham classification
import gensim.downloader as api

wv = api.load('word2vec-google-news-300')

# lowercase
# lemmatize
# remove stopwords

# this convert a document into list of lowercase tokens, ignoring words that are too
# short or too long
from gensim.utils import simple_preprocess
words=[]
for sent in corpus:
    sent_token=sent_tokenize(sent)
    for sent in sent_token:
        words.append(simple_preprocess(sent))
#[['where', 'are','you'],['i','am','fine']]

## Lets train Word2vec from scratch
model=gensim.models.Word2Vec(words)
# Here we are taking default values of window, epoch etc
model.wv.index_to_key # [list of all the words]

def avg_word2vec(doc):    
    return np.mean([model.wv[word] for word in doc if word in model.wv.index_to_key],axis=0)

for i in tqdm(range(len(words))):
    X.append(avg_word2vec(words[i]))



# There is a difference of 3 records between messages and corpus
[[i,j,k] for i,j,k in zip(list(map(len,corpus)),corpus, messages
# [[0, '', '645'], [0, '', ':) '], [0, '', ':-) :-)']]
# So we also need to remove corresponding Y
y = messages[list(map(lambda x: len(x)>0 ,corpus))]
y=pd.get_dummies(y['label'])
y=y.iloc[:,0].values

df=pd.DataFrame()
for i in range(0,len(X)):
    df=df.append(pd.DataFrame(X[i].reshape(1,-1)),ignore_index=True)
# X[0].shape # 100,0
# We need to convert it into 1 row and 100 columns -> 1,100 so we reshape here

df['Output']=y
df.dropna(inplace=True)
df.isnull().sum()

## Independent Feature
X=df

# Do train test split
# We can apply any classification algo to this

```
