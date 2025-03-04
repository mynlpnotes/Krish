# Word2Vec

* If any error comes in download, then it can be numpy version mismatch issue
* We should create a new environment and install gensim, numpy
* Its a dense matrix
* Model has been trained by google
* Model is around 1.6GB
* Encoding models are dependent on frequency ⇒ GIves sparse matrix
* Embedding do not use frequency, they are trained using NN ⇒ Dense matrix&#x20;

```python
from gensim.models import Word2Vec,KeyedVectors
import gensim.downloader as api

model = api.load('word2vec-google-news-300')

model["sunny"] # Will return array of 300

len(model["sunny"]) # 300

model.most_similar("man")
#[('woman', 0.7664012908935547),
# ('boy', 0.6824871301651001),
# ('teenager', 0.6586930155754089),
# ('teenage_girl', 0.6147903203964233),
# ('girl', 0.5921714305877686),
# ('suspected_purse_snatcher', 0.571636438369751),
# ('robber', 0.5585119128227234),
# ('Robbery_suspect', 0.5584409832954407),
# ('teen_ager', 0.5549196600914001),
# ('men', 0.5489763021469116)]

model.similarity('man','woman')
# 0.76640123

model.doesnt_match(["PHP","JAVA","DOG","C++"])
# DOG

vec=model['king'] - model['man'] + model['woman']
model.most_similar([vec])
#[('king', 0.8449392318725586),
# ('queen', 0.7300517559051514),
# ('monarch', 0.645466148853302),
# ('princess', 0.6156251430511475),
# ('crown_prince', 0.5818676352500916),
# ('prince', 0.5777117609977722),
# ('kings', 0.5613663792610168),
# ('sultan', 0.5376775860786438),
# ('Queen_Consort', 0.5344247817993164),
# ('queens', 0.5289887189865112)]



```
