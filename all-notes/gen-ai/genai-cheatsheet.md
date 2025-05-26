---
hidden: true
---

# 🔴 GenAI Cheatsheet

DataLoader:

* Load data into standard langchain document format
* A Document object consists of two main attributes:
  1. page\_content: The main text or content of the document (usually unstructured data like text).
  2. metadata: A dictionary containing additional information about the document, such as its source, author, or other custom fields.
* Different DataLoaders
  * TextLoader
  * PdfLoader
  * Websiteloader
  * Arvix - Research paper
  * Wikipedia

Split:

* Every LLM model has limitation of the context size, so we divide the document into smaller chunks
*   We specify chunk size and chunk overlap&#x20;

    ```python
    text_splitter=RecursiveCharacterTextSplitter(chunk_size=500,chunk_overlap=50)
    final_documents=text_splitter.split_documents(docs)
    ```
* Other types:
  * Character splitter - Splits based on separator
  * HTML text splitter
  * json splitter

Embeddings:

*

    ```python
    #Using OpenAI
    from langchain_openai import OpenAIEmbeddings
    embeddings=OpenAIEmbeddings(model="text-embedding-3-large")

    query_result=embeddings.embed_query(text) # To embed a query

    from langchain_community.vectorstores import Chroma
    db=Chroma.from_documents(final_documents,embeddings_1024)

    # Using Ollama
    from langchain_community.embeddings import OllamaEmbeddings

    embeddings=(    OllamaEmbeddings(model="gemma:2b"))
    embeddings.embed_documents(documents) # To embed the documents

    # Using huggingface
    from langchain_huggingface import HuggingFaceEmbeddings
    embeddings=HuggingFaceEmbeddings(model_name="all-MiniLM-L6-v2")
    query_result=embeddings.embed_query(text)
    doc_result = embeddings.embed_documents([text, "This is a test document."])
    ```

Vector stores:

* FAISS, ChromaDB
* We can also store and load the vectors
* We can also convert the vectorstore into a retriever class
* This allows to easily use it in other LangChain methods, which largely work with retrievers
* similarity\_search\_with\_score - allows to return not only the documents but also the distance score of the query to them.
*

    ```python
    db=FAISS.from_documents(docs,embeddings)

    ### querying 
    query="How does the speaker describe the desired outcome of the war?"
    docs=db.similarity_search(query)
    docs[0].page_content

    retriever=db.as_retriever()
    docs=retriever.invoke(query)
    docs[0].page_content

    docs_and_score=db.similarity_search_with_score(query)
    docs_and_score

    ### Saving And Loading
    db.save_local("faiss_index")
    new_db=FAISS.load_local("faiss_index",embeddings,
                    allow_dangerous_deserialization=True)

    # Using chromaDB
    vectordb=Chroma.from_documents(documents=splits,embedding=embedding)
    ```



**Chain:**

* A series of interconnected prompts or tasks executed sequentially
*

    ```
    chain=prompt|llm
    response=chain.invoke({"input":"Can you tell me about Langsmith?"})

    chain=prompt|llm|output_parser
    ```

Prompt template:

* pre-defined structure or format for creating prompts, often with placeholders that can be dynamically filled with specific inputs
* Generate a job description for a {role} requiring {experience} years of experience in {skills}.
*   Here we are setting the persona for system

    ```
    prompt=ChatPromptTemplate.from_messages(
        [
            ("system","You are an expert AI Engineer. Provide me answers based on the questions"),
            ("user","{input}")
        ]
    )
    ```

StrOutputParser:

* To format the output

