# Model Limitations

Hallucination:

* Makes statement that sound plausible but are not true - Coz model has not perfectly memorized the model it has seen and it might not know the boundary of its knowledge
* Ask the model to first find the relevant information and then answer the question based on the relevant information

```python
prompt = f"""
Tell me about AeroGlide UltraSlim Smart Toothbrush by Boie
"""
response = get_completion(prompt)
print(response)
```

