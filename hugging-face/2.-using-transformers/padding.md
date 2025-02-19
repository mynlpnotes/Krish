# Padding

* We add padding token

```python
padding_id = 100

batched_ids = [
    [200, 200, 200],
    [200, 200, padding_id],
]

model = AutoModelForSequenceClassification.from_pretrained(checkpoint)

sequence1_ids = [[200, 200, 200]]
sequence2_ids = [[200, 200]]
batched_ids = [
    [200, 200, 200],
    [200, 200, tokenizer.pad_token_id],
]

print(model(torch.tensor(sequence1_ids)).logits)
print(model(torch.tensor(sequence2_ids)).logits)
print(model(torch.tensor(batched_ids)).logits)
# tensor([[ 1.5694, -1.3895]], grad_fn=<AddmmBackward>)
# tensor([[ 0.5803, -0.4125]], grad_fn=<AddmmBackward>)
# tensor([[ 1.5694, -1.3895],
#        [ 1.3373, -1.2163]], grad_fn=<AddmmBackward>)


```

* The second row should be the same as the logits for the second sentence, but we’ve got completely different values
* This is because the key feature of Transformer models is attention layers that _contextualize_ each token.&#x20;
* These will take into account the padding tokens since they attend to all of the tokens of a sequence.&#x20;
* To get the same result when passing individual sentences of different lengths through the model or when passing a batch with the same sentences and padding applied, we need to tell those attention layers to ignore the padding tokens.
