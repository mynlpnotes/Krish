# Sentence embedding using Huggingface

```python
from langchain.embeddings import HuggingFaceEmbeddings

embedding_model_name = "sentence-transformers/all-mpnet-base-v2"

model_kwargs = {"device": "cpu"}
embeddings = HuggingFaceEmbeddings(model_name=embedding_model_name,model_kwargs=model_kwargs)

embedding_vector = embeddings.embed_query(sentences[0])
embedding_vector
[-0.01585976779460907,
 0.04598265513777733,
 -0.01463495846837759,.....]

len(embedding_vector) # 768
```
