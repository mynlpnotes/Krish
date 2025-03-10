# 🟢 Zero Shot Classification

* <mark style="color:purple;background-color:purple;">**To classify text that has not been labelled**</mark>
* <mark style="color:purple;background-color:purple;">**You don't need to fine tune the model**</mark>
* <mark style="color:purple;background-color:purple;">**We have to pass the candidate\_labels**</mark>

```python
from transformers import pipeline

classifier = pipeline("zero-shot-classification")
classifier(
    "This is a course about the Transformers library",
    candidate_labels=["education", "politics", "business"],
)
#{'sequence': 'This is a course about the Transformers library',
# 'labels': ['education', 'business', 'politics'],
# 'scores': [0.8445963859558105, 0.111976258456707, 0.043427448719739914]}
```
