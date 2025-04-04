# BERT - Fine tuning

* Datacollator?&#x20;

```python
from transformers import TrainingArguments, Trainer
import evaluate
metric = evaluate.load("seqeval")

#these are hyperparameter
args=TrainingArguments(
    "test-ner",
    evaluation_strategy = "epoch",
    learning_rate=2e-5,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=16,
    num_train_epochs=1,
    weight_decay=0.01,
    report_to="none"  # Disable wandb logging
)

data_collator=DataCollatorForTokenClassification(tokenizer)

def compute_metrics(eval_preds):
    pred_logits, labels = eval_preds

    pred_logits = np.argmax(pred_logits, axis=2)
    # the logits and the probabilities are in the same order,
    # so we don’t need to apply the softmax

    # We remove all the values where the label is -100
    predictions = [
        [label_list[eval_preds] for (eval_preds, l) in zip(prediction, label) if l != -100]
        for prediction, label in zip(pred_logits, labels)
    ]

    true_labels = [
      [label_list[l] for (eval_preds, l) in zip(prediction, label) if l != -100]
       for prediction, label in zip(pred_logits, labels)
   ]
    results = metric.compute(predictions=predictions, references=true_labels)

    return {
          "precision": results["overall_precision"],
          "recall": results["overall_recall"],
          "f1": results["overall_f1"],
          "accuracy": results["overall_accuracy"],
  }

trainer=Trainer(
   model,
   args,
   train_dataset=tokenized_datasets["train"],
   eval_dataset=tokenized_datasets["validation"],
   data_collator=data_collator,
   tokenizer=tokenizer,
   compute_metrics=compute_metrics
)

trainer.train()
# [878/878 03:46, Epoch 1/1]
# Epoch	Training Loss	Validation Loss	Precision	Recall	F1	Accuracy
# 1	0.234900	0.066412	0.905907	0.923034	0.914390	0.981000

```



