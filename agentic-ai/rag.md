# RAG

* Datasource: Webpage
* DataLoader: To read the data from source
  * There are different data loaders
* The data can be huge, so we divide into chunks (Splitting the data)
* We will convert this into vectors
* There are different embeddings
* We will store this vectors into vector store
* Whenever we give query the vector store, it should give us context based on similarity search
* This when given to LLM should get correct output
* RAG means we have different source and we are able to chat with it

```python
from langchain_community.document_loaders import WebBaseLoader

loader=WebBaseLoader("https://python.langchain.com/docs/tutorials/llm_chain/")

document=loader.load()
# This will have a single document

from langchain_text_splitters import RecursiveCharacterTextSplitter

text_splitter=RecursiveCharacterTextSplitter(chunk_size=1000,chunk_overlap=200)
documents=text_splitter.split_documents(document)
# After chunking, we will get multiple documents

from langchain_openai import OpenAIEmbeddings
embeddings=OpenAIEmbeddings()

from langchain_community.vectorstores import FAISS

vectorstore=FAISS.from_documents(documents,embeddings)

query="This is a relatively simple LLM application "

result=vectorstore.similarity_search(query)
result[0].page_content
# "In this quickstart we'll show you how to build a simple LLM application 
# with LangChain. This application will translate text from English into another
# language. This is a relatively simple LLM application - it's just a single
# LLM call plus some prompting. Still, this is a great way to get started
# with LangChain - a lot of features can be built with just some prompting
# and an LLM call!\nAfter reading this tutorial, you'll have a high level
# overview of:"

from langchain.chains.combine_documents import create_stuff_documents_chain
document_chain=create_stuff_documents_chain(llm,prompt)
document_chain

```
