# push to hub API

* Generate authentication token
* Ensure you are in the correct environment
* Terminal ⇒ huggingface-cli login ⇒ this will save the token in cache
* Using the trainer API add in training arguments

```python
from transformers import TrainingArguments

training_args = TrainingArguments(
    "bert-finetuned-mrpc", save_strategy="epoch", push_to_hub=True
)
```

* Once your training is finished, you should do a final `trainer.push_to_hub()` to upload the last version of your model. It will also generate a model card with all the relevant metadata, reporting the hyperparameters used and the evaluation results
* We can also push the tokenizer to the hub
* We can also explicity specify auth token while pushing if we want
