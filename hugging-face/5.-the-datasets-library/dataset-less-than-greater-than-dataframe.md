# Dataset <=> DataFrame

```python
drug_dataset.set_format("pandas")

from datasets import Dataset

freq_dataset = Dataset.from_pandas(frequencies)
freq_dataset
```
