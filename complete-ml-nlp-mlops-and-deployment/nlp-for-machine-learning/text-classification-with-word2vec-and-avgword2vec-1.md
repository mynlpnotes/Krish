# Text Classification with Word2Vec and AvgWord2Vec - 1

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

# Prepare Y  

```
