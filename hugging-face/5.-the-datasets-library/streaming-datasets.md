# Streaming Datasets

* To enable dataset streaming you just need to pass the `streaming=True` argument to the `load_dataset()` function

```python
pubmed_dataset_streamed = load_dataset(
    "json", data_files=data_files, split="train", streaming=True
)
```

* It returns an itterable dataset

```python
next(iter(pubmed_dataset_streamed))
```
