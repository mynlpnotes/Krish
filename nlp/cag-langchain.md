# CAG - LangChain

* [https://python.langchain.com/docs/integrations/llm\_caching/](https://python.langchain.com/docs/integrations/llm_caching/)
* Options to keep cache in lot of different DB like cassandra, mongo etc

```python
from langchain.cache import InMemoryCache
from langchain.globals import set_llm_cache
from typing import Any, Dict, Tuple
from langchain_groq import ChatGroq

class DebuggableCache(InMemoryCache):
    def __init__(self):
        super().__init__()
        self._cache: Dict[Tuple[str, str], Any] = {}

    def lookup(self, prompt: str, llm_string: str):
        return self._cache.get((prompt, llm_string))

    def update(self, prompt: str, llm_string: str, return_val: Any):
        self._cache[(prompt, llm_string)] = return_val

    def view_cache(self):  # 👈 this is our custom method
        return self._cache

dbg_cache = DebuggableCache()
set_llm_cache(dbg_cache)

response = llm.invoke("What is the capital of France?")

print("LLM Response:", response)
# LLM Response: content="That's an easy one! The capital of France is Paris!" 
# additional_kwargs={} response_metadata={'token_usage': {'completion_tokens': 14,
# 'prompt_tokens': 17, 'total_tokens': 31, 'completion_time': 0.046742411,
# 'prompt_time': 0.000270568, 'queue_time': 0.0547071, 'total_time': 0.047012979},
# 'model_name': 'llama3-70b-8192', 'system_fingerprint': 'fp_dd4ae1c591',
# 'finish_reason': 'stop', 'logprobs': None} id='run--4ee59569-b6b1-48b1-8ad5-ba
# 450cadda74-0' usage_metadata={'input_tokens': 17, 'output_tokens': 14, 
# 'total_tokens': 31}

print("\nCache Contents:")
for k, v in dbg_cache.view_cache().items():
    print(f"Prompt: {k[0]} | Cached Output: {v}")

response = llm.invoke("What is the capital of France?")


```
