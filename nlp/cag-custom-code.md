# CAG - Custom Code

```python
import os
os.environ["GROQ_API_KEY"] = os.getenv("GROQ_API_KEY")

from langchain_groq import ChatGroq
llm = ChatGroq(model="llama3-70b-8192",api_key="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")

Model_Cache = {}

import time
def cached_model(query):
    start_time = time.time()
    if Model_Cache.get(query):
        print("***CACHE HIT***")
        end_time = time.time()
        elapsed = end_time - start_time
        print(f"EXECUTION TIME: {elapsed:.2f} seconds")
        return Model_Cache.get(query)
    else:
        print("***CACHE MISS – EXECUTING MODEL***")
        start_time = time.time()
        response = llm.invoke(query)
        end_time = time.time()
        elapsed = end_time - start_time
        print(f"EXECUTION TIME: {elapsed:.2f} seconds")
        Model_Cache[query] = response
        return response

query="hi"
response = cached_model(query)
print(response)
#***CACHE MISS – EXECUTING MODEL***
#EXECUTION TIME: 0.42 seconds
#content="Hi! It's nice to meet you......'

query="can you give me 1000 words essay on independence?"
response = cached_model(query)
print(response)
#***CACHE MISS – EXECUTING MODEL***
#EXECUTION TIME: 4.18 seconds
#content="Here is a 1000-word essay on independence:\n\nIndependence: The Backbone of..'

  

```
