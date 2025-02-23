# Longer Sentences

* There is a limit to the lengths of the sequences we can pass the models. Most models handle sequences of up to 512 or 1024 tokens
* Solution:
  * Use a model with a longer supported sequence length.
  * Truncate your sequences.
* Longformer and LED are specialized in handling very long lengths

```python
# Truncating
sequence = sequence[:max_sequence_length]
```
