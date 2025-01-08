# 🟢 Data Ingestion with Document Loaders

* [https://python.langchain.com/v0.2/docs/integrations/document\_loaders/](https://python.langchain.com/v0.2/docs/integrations/document_loaders/)

```python
## Reading from .txt file
from langchain_community.document_loaders import TextLoader
loader=TextLoader('speech.txt')
text_documents=loader.load()
text_documents # This will have all the text

## Reading a PDf File
from langchain_community.document_loaders import PyPDFLoader
loader=PyPDFLoader('attention.pdf')
docs=loader.load()
docs

## Web based loader
# We pass class_ if we want only specific info from page
from langchain_community.document_loaders import WebBaseLoader
import bs4
loader=WebBaseLoader(web_paths=("https://lilianweng.github.io/posts/2023-06-23-agent/",),
                     bs_kwargs=dict(parse_only=bs4.SoupStrainer(
                         class_=("post-title","post-content","post-header")
                     ))
                     )
loader.load()

## To get research paper from Arxiv
from langchain_community.document_loaders import ArxivLoader
docs = ArxivLoader(query="1706.03762", load_max_docs=2).load()
len(docs)

## Wikipedia
from langchain_community.document_loaders import WikipediaLoader
docs = WikipediaLoader(query="Generative AI", load_max_docs=2).load()
len(docs)
print(docs)

```
