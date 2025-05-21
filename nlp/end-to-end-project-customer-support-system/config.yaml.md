# config.yaml

* There will be a config loader which read the yaml and return the dictionary

```yaml
astra_db:
      collection_name: "ecommercedata"
      
embedding_model:
      provider: "google"
      model_name: "models/text-embedding-004"
      
retriever:
      top_k: 10
llm:
      provider: "google"
      model_name: "deepseek-r1-distill-llama-70b"
```
