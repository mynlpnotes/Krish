# Retriever

* An interface to ask vector store anything
* create retrieval chain will combine retriever chain and document chain together
* We need to convert vector store into runnable binding using retriever
* Retriever can be added to any chain
* Retriever chain is to get context from vector DD, converting it into document and passing it to LLM is donr using document chain
