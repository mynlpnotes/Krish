# Creating your own dataset

* Get the data
* Clean the data
* Augmenting the dataset
* Uploading the dataset to the hugging face
* Create a dataset card

```python
from huggingface_hub import notebook_login

notebook_login()

huggingface-cli login

issues_with_comments_dataset.push_to_hub("github-issues")
```
