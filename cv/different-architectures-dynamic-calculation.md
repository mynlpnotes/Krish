# Different Architectures - Dynamic Calculation

```python
class CNN(nn.Module):
    def __init__(self):
        super(CNN, self).__init__()
        self.conv1 = nn.Conv2d(1, 32, kernel_size=3, stride=1, padding=1)
        self.conv2 = nn.Conv2d(32, 64, kernel_size=3, stride=1, padding=1)
        self.pool = nn.MaxPool2d(kernel_size=2, stride=2)
        self.fc1 = None  # Placeholder for first fully connected layer
        self.fc2 = nn.Linear(128, 10)  # Fixed output size for 10 classes

    def forward(self, x):
        x = self.conv1(x)
        x = self.pool(x)
        x = self.conv2(x)
        x = self.pool(x)
        if self.fc1 is None:
            # Dynamically define fc1 based on input dimensions
            self.fc1 = nn.Linear(x.view(x.size(0), -1).size(1), 128)
        x = x.view(x.size(0), -1)
        x = self.fc1(x)
        x = self.fc2(x)
        return x

```
