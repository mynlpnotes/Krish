# 🟢 Word2Vec practical implementation - Gensim

* <mark style="color:purple;background-color:purple;">**We can use gensim to download pre trained word2vec models**</mark>

```python
import gensim
from gensim.models import Word2Vec, KeyedVectors
import gensim.downloader as api

wv = api.load('word2vec-google-news-300')
vec_king = wv['king']

wv.most_similar('cricket')
wv.most_similar('happy')
#[('cricketing', 0.8372225165367126),
# ('cricketers', 0.8165745735168457),
# ('Test_cricket', 0.8094818592071533),
# ('Twenty##_cricket', 0.8068488240242004),
# ('Twenty##', 0.7624266147613525),
# ('Cricket', 0.7541396617889404),
# ('cricketer', 0.7372579574584961),
# ('twenty##', 0.7316356897354126),
# ('T##_cricket', 0.7304614782333374),
# ('West_Indies_cricket', 0.698798656463623)]

wv.similarity("hockey","sports") # 0.53541523

vec=wv['king']-wv['man']+wv['woman']
wv.most_similar([vec])
#[('king', 0.8449392318725586),
# ('queen', 0.7300517559051514),
# ('monarch', 0.6454660892486572),
# ('princess', 0.6156251430511475),
# ('crown_prince', 0.5818676948547363),
# ('prince', 0.5777117609977722),
# ('kings', 0.5613663792610168),
# ('sultan', 0.5376776456832886),
# ('Queen_Consort', 0.5344247817993164),
# ('queens', 0.5289887189865112)]

```
