# Text Generation

* Provide a prompt and the model will auto-complete it by generating the remaining text
* You can control how many different sequences are generated with the argument `num_return_sequences` and the total length of the output text with the argument `max_length`

```python
from transformers import pipeline

generator = pipeline("text-generation")
generator("In this course, we will teach you how to")
#[{'generated_text': 'In this course, we will teach you how to understand and use '
#                    'data flow and data interchange when handling user data. We '
#                    'will be working with one or more of the most commonly used '
#                    'data flows — data flows of various types, as seen by the '
#                    'HTTP'}]
```
