# BERT - Fine tuned model - Model Upload

* Create write token on hugging face
* No need to push tokenizer, unless you have fine tuned tokenizer as well

```python
! pip install huggingface_hub

from huggingface_hub import notebook_login

notebook_login()

model_fine_tuned.push_to_hub("sunny199/NER-Model-Fine-Tuned")
```
