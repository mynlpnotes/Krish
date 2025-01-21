# Sequential Model

* Simple and concise for linear architecture
* Limited to layer stacking

```python
sequential_model = nn.Sequential(
    nn.Linear(20,64), # Input layer (20 -> 64)
    nn.ReLU(),
    nn.Linear(64, 32),
    nn.ReLU(),
    nn.Linear(32, 5),
)

print(sequential_model)

input_data = torch.randn(10, 20) # 10 rows, 20 is my feature size in each row
print(input_data)
output = sequential_model(input_data)
print(output)

```
