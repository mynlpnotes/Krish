# NER without tokenizer

* We get logits here
* We use a softmax function to convert those logits to probabilities, and we take the argmax to get predictions

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification

model_checkpoint = "dbmdz/bert-large-cased-finetuned-conll03-english"
tokenizer = AutoTokenizer.from_pretrained(model_checkpoint)
model = AutoModelForTokenClassification.from_pretrained(model_checkpoint)

example = "My name is Sylvain and I work at Hugging Face in Brooklyn."
inputs = tokenizer(example, return_tensors="pt")
outputs = model(**inputs)

print(inputs["input_ids"].shape)
print(outputs.logits.shape)
# torch.Size([1, 19])
# torch.Size([1, 19, 9])
# We have a batch with 1 sequence of 19 tokens and the model has 9 different labels,
# so the output of the model has a shape of 1 x 19 x 9

import torch

probabilities = torch.nn.functional.softmax(outputs.logits, dim=-1)[0].tolist()
predictions = outputs.logits.argmax(dim=-1)[0].tolist()
print(predictions)
# [0, 0, 0, 0, 4, 4, 4, 4, 0, 0, 0, 0, 6, 6, 6, 0, 8, 0, 0]

model.config.id2label

results = []
tokens = inputs.tokens()

for idx, pred in enumerate(predictions):
    label = model.config.id2label[pred]
    if label != "O":
        results.append(
            {"entity": label, "score": probabilities[idx][pred], "word": tokens[idx]}
        )

print(results)
# [{'entity': 'I-PER', 'score': 0.9993828, 'index': 4, 'word': 'S'},
#  {'entity': 'I-PER', 'score': 0.99815476, 'index': 5, 'word': '##yl'},
#  {'entity': 'I-PER', 'score': 0.99590725, 'index': 6, 'word': '##va'},
#  {'entity': 'I-PER', 'score': 0.9992327, 'index': 7, 'word': '##in'},
#  {'entity': 'I-ORG', 'score': 0.97389334, 'index': 12, 'word': 'Hu'},
#  {'entity': 'I-ORG', 'score': 0.976115, 'index': 13, 'word': '##gging'},
#  {'entity': 'I-ORG', 'score': 0.98879766, 'index': 14, 'word': 'Face'},
#  {'entity': 'I-LOC', 'score': 0.99321055, 'index': 16, 'word': 'Brooklyn'}]

# We can also group the entities
# [{'entity_group': 'PER', 'score': 0.9981694, 'word': 'Sylvain', 'start': 11, 'end': 18},
#  {'entity_group': 'ORG', 'score': 0.97960204, 'word': 'Hugging Face', 'start': 33, 'end': 45},
#  {'entity_group': 'LOC', 'score': 0.99321055, 'word': 'Brooklyn', 'start': 49, 'end': 57}]

```
