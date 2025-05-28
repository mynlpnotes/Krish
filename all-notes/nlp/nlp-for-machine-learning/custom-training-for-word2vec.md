# Custom training for word2vec

```python
nltk.download("all")

from nltk import sent_tokenize
from gensim.utils import simple_preprocess

story=[]

folder_path=r"C:\\Complete_Content\\GENERATIVEAI\\genai_bootcamp\\gotbooks"

story=[]
for filename in os.listdir(folder_path):
  file_path=os.path.join(folder_path,filename)
  with open(file_path,encoding='unicode_escape') as f:
    corpus=f.read()
  raw_sent=sent_tokenize(corpus)
  for sent in raw_sent:
    story.append(simple_preprocess(sent))

story
[['game',  'of',  'thrones',  'book',....],
 ['','',.....]

custom_model=gensim.models.Word2Vec(window=10,min_count=5,vector_size=150)
custom_model.build_vocab(story)
custom_model.train(story,total_examples=model.corpus_count, epochs=5)
custom_model.wv["king"]
```
