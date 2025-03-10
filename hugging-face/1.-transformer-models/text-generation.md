# 🟢 Text Generation

* <mark style="color:purple;background-color:purple;">**Provide a prompt and the model will auto-complete it by generating the remaining text**</mark>
* <mark style="color:purple;background-color:purple;">**You can control how many different sequences are generated with the argument**</mark><mark style="color:purple;background-color:purple;">**&#x20;**</mark><mark style="color:purple;background-color:purple;">**`num_return_sequences`**</mark><mark style="color:purple;background-color:purple;">**&#x20;**</mark><mark style="color:purple;background-color:purple;">**and the total length of the output text with the argument**</mark><mark style="color:purple;background-color:purple;">**&#x20;**</mark><mark style="color:purple;background-color:purple;">**`max_length`**</mark>

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
