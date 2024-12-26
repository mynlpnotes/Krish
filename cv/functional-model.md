# Functional Model

* Flexible but requires more code.
* Allows any custom computation logic

```python
class FunctionalModel(nn.Module):
  def __init__(self):
    super(FunctionalModel, self).__init__()
    self.fc1 = nn.Linear(20, 64)
    self.fc2 = nn.Linear(64, 32)
    self.fc3 = nn.Linear(32, 5)
    self.relu = nn.ReLU()

  def forward(self, X):
    x = self.relu(self.fc1(X))
    x = self.relu(self.fc2(x))
    x = self.fc3(x)
    return x

functional_model = FunctionalModel()

print(functional_model)

input_data = torch.randn(10, 20) # 10 rows, 20 is my feature size in each row
print(input_data)
output = functional_model(input_data)
print(output)
```
