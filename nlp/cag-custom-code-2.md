# CAG - Custom Code - 2

```python
from langchain_community.embeddings import HuggingFaceEmbeddings

embedding_model = HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-MiniLM-L6-v2"
)

from langchain_community.vectorstores import Chroma
from langchain_core.prompts import PromptTemplate
from langchain_core.runnables import RunnableMap, RunnablePassthrough
from langchain_core.output_parsers import StrOutputParser

from langchain.schema import Document

documents = [
    Document(page_content="The Earth is the third planet from the Sun and the only known planet to support life. It has a diverse climate, ranging from arctic to tropical zones, and supports ecosystems across seven continents and five oceans."),

    Document(page_content="The Industrial Revolution, beginning in the 18th century, drastically transformed human societies by shifting from manual labor to machine-based manufacturing, leading to urbanization and economic expansion globally."),

    Document(page_content="The United Nations, established in 1945 after World War II, is an international organization founded to promote peace, security, human rights, and cooperation among countries. It has 193 member states."),

    Document(page_content="The global economy is an interconnected system involving trade, investment, and financial flows across countries. Major players include the United States, China, the European Union, and emerging markets like India and Brazil."),

    Document(page_content="Climate change refers to long-term shifts in temperatures and weather patterns. It is largely driven by human activities like burning fossil fuels, deforestation, and industrial emissions, leading to global warming and sea level rise."),

    Document(page_content="Democracy is a political system in which citizens exercise power by voting. Modern democracies typically have institutions for free elections, rule of law, freedom of expression, and checks and balances."),

    Document(page_content="The Internet has revolutionized communication, commerce, and education worldwide. Originating from military research in the 1960s, it now connects over 5 billion people, enabling instant global information exchange."),

    Document(page_content="Renewable energy sources like solar, wind, hydro, and geothermal are critical for a sustainable future. They offer alternatives to fossil fuels, reducing carbon emissions and reliance on finite resources."),

    Document(page_content="The World Health Organization (WHO) is a UN agency focused on global health issues. It coordinates international efforts to monitor diseases, set health standards, and respond to pandemics like COVID-19."),

    Document(page_content="Globalization is the process of increasing interaction and integration among people, companies, and governments worldwide. It has led to greater economic growth but also raised concerns about inequality and cultural homogenization.")
]

# Chroma vector DB with persistent storage
vector_store = Chroma.from_documents(
    documents=documents,
    embedding=embedding_model,
    persist_directory="./chroma_db"  # Disk path for persistence
)
# Optional: Persist manually (though auto-persistence happens internally)
vector_store.persist()

retriever = vector_store.as_retriever()

prompt = PromptTemplate.from_template(
    """
    Use the following context to answer the question.
    If you don't know the answer, just say you don't know. Don't try to make up an answer.

    Context:
    {context}

    Question:
    {question}

    Answer:
    """
)

# LCEL RAG Chain step-by-step
rag_chain = (
    RunnableMap({
        "context": retriever | (lambda docs: "\n\n".join([doc.page_content for doc in docs])),
        "question": RunnablePassthrough()
    })
    | prompt
    | llm
    | StrOutputParser()
)

RAG_Cache = {}

import time
def cached_rag_chain(query):
    start_time = time.time()
    if RAG_Cache.get(query):
        print("***CACHE HIT***")
        end_time = time.time()
        elapsed = end_time - start_time
        print(f"EXECUTION TIME: {elapsed:.2f} seconds")
        return RAG_Cache.get(query)
    else:
        print("***CACHE MISS – EXECUTING MODEL***")
        start_time = time.time()
        response = llm.invoke(query)
        end_time = time.time()
        elapsed = end_time - start_time
        print(f"EXECUTION TIME: {elapsed:.2f} seconds")
        RAG_Cache[query] = response
        return response

query = "what is japan economy in 2024 and relation with north korea?"
response = cached_rag_chain(query)
print(response)


```
