# Different Architectures - Adaptive Pooling

```python
import torch
import torch.nn as nn

class CNN(nn.Module):
    def __init__(self):
        super(CNN, self).__init__()
        self.conv_layers = nn.Sequential(
            nn.Conv2d(1, 32, kernel_size=3, stride=1, padding=1),  # Output: 32x28x28
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=2, stride=2),                 # Output: 32x14x14
            nn.Conv2d(32, 64, kernel_size=3, stride=1, padding=1), # Output: 64x14x14
            nn.ReLU(),
            nn.MaxPool2d(kernel_size=2, stride=2)                  # Output: 64x7x7
        )

        # Adaptive pooling to ensure fixed output size (e.g., 64x1x1)
        self.global_pool = nn.AdaptiveAvgPool2d((1, 1))  # Output: 64x1x1

        # Fully connected layers
        self.fc_layers = nn.Sequential(
            nn.Flatten(),                # Flatten for linear layers
            nn.Linear(64, 128),          # Map pooled features to 128 nodes
            nn.ReLU(),
            nn.Linear(128, 10)           # Output 10 classes
        )

    def forward(self, x):
        x = self.conv_layers(x)          # Pass through convolutional layers
        x = self.global_pool(x)          # Adaptive pooling
        x = self.fc_layers(x)            # Pass through fully connected layers
        return x

```
