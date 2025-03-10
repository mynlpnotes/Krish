# 🟢 What can Transformers do

* <mark style="color:purple;background-color:purple;">**pipeline() helps connect a model with its necessary preprocessing and postprocessing steps, allowing to directly input any text and get answer**</mark>
  1. The text is preprocessed into a format the model can understand.
  2. The preprocessed inputs are passed to the model.
  3. The predictions of the model are post-processed, so you can make sense of them.

```python
from transformers import pipeline

classifier = pipeline("sentiment-analysis")
classifier("I've been waiting for a HuggingFace course my whole life.")
# [{'label': 'POSITIVE', 'score': 0.9598047137260437}]

# To pass several sentences
classifier(
    ["I've been waiting for a HuggingFace course my whole life.", "I hate this so much!"]
)
```
