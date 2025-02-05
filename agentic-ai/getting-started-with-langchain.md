# Getting started with LangChain

* Entire traceability is happening in langsmith
* We will be able to see which model was called, temperature, chain, etc
*

```python
import os
from dotenv import load_dotenv
load_dotenv()

os.environ["OPENAI_API_KEY"]=os.getenv("OPENAI_API_KEY")

## Langsmith Tracking and tracing

os.environ["LANGCHAIN_API_KEY"]=os.getenv("LANGCHAIN_API_KEY")
os.environ["LANGCHAIN_TRACING_V2"]="true"
os.environ["LANGCHAIN_PROJECT"]=os.getenv("LANGCHAIN_PROJECT")

from langchain_openai import ChatOpenAI

llm=ChatOpenAI(model="o1-mini")
print(llm)

result=llm.invoke("What is agentic AI")
print(result)
print(result.content) # To see the response
```

```python
from langchain_core.prompts import ChatPromptTemplate

prompt=ChatPromptTemplate.from_messages(
    [
        ("system","You are an expert AI Engineer. Provide me answer based on the question"),
        ("user","{input}")

    ]
)
prompt
# ChatPromptTemplate(input_variables=['input'], input_types={}, 
# partial_variables={}, messages=[SystemMessagePromptTemplate(
# prompt=PromptTemplate(input_variables=[], input_types={}, partial_variables={},
# template='You are an expert AI Engineer. Provide me answer based on the question'), 
# additional_kwargs={}), HumanMessagePromptTemplate(prompt=PromptTemplate(
# input_variables=['input'], input_types={}, partial_variables={}, template='{input}'), 
# additional_kwargs={})])

llm=ChatOpenAI(model="gpt-4o")
chain=prompt|llm 
response=chain.invoke({"input":"Can you tell me about Langsmith"})
print(response)

```

```python
from langchain_core.output_parsers import StrOutputParser
output_parser=StrOutputParser()

chain=prompt|llm|output_parser

response=chain.invoke({"input":"Can you tell me about Langsmith?"})
print(response)
```

```python
from langchain_core.prompts import PromptTemplate
from langchain_core.output_parsers import JsonOutputParser


output_parser=JsonOutputParser()
prompt = PromptTemplate(
    template="Answer the user query.\n{format_instructions}\n{query}\n",
    input_variables=["query"],
    partial_variables={"format_instructions": output_parser.get_format_instructions()},
)

chain=prompt|llm|output_parser

response=chain.invoke({"query":"Can you tell me about Langsmith?"})
print(response)
# {'name': 'Langsmith', 'description': 'Langsmith is a platform 
# designed to streamline customer communication by offering tools for 
# managing and automating messaging dialogues. It utilizes artificial 
# intelligence to provide smart and efficient handling of customer interactions, 
# ensuring more personalized and effective responses.', 
# 'features': ['Automated messaging', 'AI-driven responses', 
# 'Integration with various communication channels', 
# 'Metrics and analytics for performance tracking', 
# 'Customizable messaging workflows'], 'use_cases': 
# ['Customer support', 'Sales and marketing', 'Feedback collection', 
# 'User engagement and retention'], 'benefits': 
# ['Increased efficiency in handling customer queries', 
# 'Improved customer satisfaction', 'Scalable communication solutions',
# 'Ability to handle high volumes of interactions']}

```
