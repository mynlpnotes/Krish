# Attention Mask

* Tensors with the exact same shape as the input IDs tensor, filled with 0s and 1s
* 1s indicate the corresponding tokens should be attended to, and 0s indicate the corresponding tokens should not be attended to

```python
batched_ids = [
    [200, 200, 200],
    [200, 200, tokenizer.pad_token_id],
]

attention_mask = [
    [1, 1, 1],
    [1, 1, 0],
]

outputs = model(torch.tensor(batched_ids), attention_mask=torch.tensor(attention_mask))
print(outputs.logits)
# tensor([[ 1.5694, -1.3895],
#        [ 0.5803, -0.4125]], grad_fn=<AddmmBackward>)

```
