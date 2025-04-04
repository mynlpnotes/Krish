# Evaluate

* Check theory of evaluate and prepare notes

```python
import evaluate
metric = evaluate.load("seqeval")

input=['EU','rejects','German','call','to','boycott','British','lamb','.']
actual_lable=['B-ORG', 'O', 'B-MISC', 'O', 'O', 'O', 'B-MISC', 'O', 'O']
pred_lable=['B-ORG', 'O', 'I-PER', 'B-ORG', 'I-ORG', 'B-LOC', 'I-LOC', 'B-MISC', 'I-MISC']#(Bert Model)

results = metric.compute(predictions=[pred_lable],references=[actual_lable])
# {'LOC': {'precision': 0.0, 'recall': 0.0, 'f1': 0.0, 'number': 0},
# 'MISC': {'precision': 0.0, 'recall': 0.0, 'f1': 0.0, 'number': 2},
# 'ORG': {'precision': 0.5,'recall': 1.0, 'f1': 0.6666666666666666, 'number': 1},
# 'PER': {'precision': 0.0, 'recall': 0.0, 'f1': 0.0, 'number': 0},
# 'overall_precision': 0.2,
# 'overall_recall': 0.3333333333333333,
# 'overall_f1': 0.25,
# 'overall_accuracy': 0.2222222222222222}

print(results["overall_f1"]) # 1
```
