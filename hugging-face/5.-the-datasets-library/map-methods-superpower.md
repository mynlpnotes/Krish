# map() methods superpower

* &#x20;if set to `True`, causes it to send a batch of examples to the map function at once (the batch size is configurable but defaults to 1,000)

```python
new_drug_dataset = drug_dataset.map(
    lambda x: {"review": [html.unescape(o) for o in x["review"]]}, batched=True
)
```
