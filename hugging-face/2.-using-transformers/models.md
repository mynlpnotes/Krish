# 🟢 Models

* <mark style="color:purple;background-color:purple;">**The AutoModel class - simple wrappers over the wide variety of models available in the library**</mark>
* It can automatically guess the appropriate model architecture for your checkpoint, and then instantiates a model with this architecture.
* <mark style="color:purple;background-color:purple;">**If we know the model we can directly use the model class also**</mark>

```python
from transformers import BertConfig, BertModel

# Building the config
config = BertConfig()

# Building the model from the config
model = BertModel(config)
#print(config)
# BertConfig {
#  [...]
#  "hidden_size": 768,
#  "intermediate_size": 3072,
#  "max_position_embeddings": 512,
#  "num_attention_heads": 12,
#  "num_hidden_layers": 12,
#  [...]
#}
```

* Above is untrained model, we can use pretrained model also

```python
from transformers import BertModel

model = BertModel.from_pretrained("bert-base-cased")
```

* <mark style="color:purple;background-color:purple;">**We could replace BertModel with the equivalent AutoModel class**</mark>
* If your code works for one checkpoint, it should work seamlessly with another. This applies even if the architecture is different, as long as the checkpoint was trained for a similar task
* This model is now initialized with all the weights of the checkpoint.
* We can also fine tune it, by training on pre trained weights
* Model gets cached in cache folder, we can also change it by changing HF\_HOME environment variable
