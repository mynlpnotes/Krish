# ResNet - Code

```python
import torch
import torch.nn as nn
import torch.nn.functional as F
from torchvision import datasets, transforms
from torch.utils.data import DataLoader

# Define the basic block
class BasicBlock(nn.Module):
    def __init__(self, in_channels, out_channels, stride=1, downsample=None):
        super(BasicBlock, self).__init__()
        self.conv1 = nn.Conv2d(in_channels, out_channels, kernel_size=3, stride=stride, padding=1, bias=False)
        self.bn1 = nn.BatchNorm2d(out_channels)
        self.conv2 = nn.Conv2d(out_channels, out_channels, kernel_size=3, stride=1, padding=1, bias=False)
        self.bn2 = nn.BatchNorm2d(out_channels)
        self.downsample = downsample  # Used for dimension matching in residual connections

    def forward(self, x):
        identity = x
        if self.downsample:
            identity = self.downsample(x)
        out = self.conv1(x)
        out = self.bn1(out)
        out = F.relu(out)
        out = self.conv2(out)
        out = self.bn2(out)
        out += identity
        out = F.relu(out)
        return out

# Define the ResNet-34 model
class ResNet34(nn.Module):
    def __init__(self, num_classes=1000):
        super(ResNet34, self).__init__()
        self.in_channels = 64

        # Initial convolution and max-pooling
        self.conv1 = nn.Conv2d(3, 64, kernel_size=7, stride=2, padding=3, bias=False)
        self.bn1 = nn.BatchNorm2d(64)
        self.relu = nn.ReLU(inplace=True)
        self.maxpool = nn.MaxPool2d(kernel_size=3, stride=2, padding=1)

        # Residual blocks
        self.layer1 = self._make_layer(64, 3, stride=1)
        self.layer2 = self._make_layer(128, 4, stride=2)
        self.layer3 = self._make_layer(256, 6, stride=2)
        self.layer4 = self._make_layer(512, 3, stride=2)

        # Global Average Pooling and Fully Connected Layer
        self.avgpool = nn.AdaptiveAvgPool2d((1, 1))
        self.fc = nn.Linear(512, num_classes)

    def _make_layer(self, out_channels, blocks, stride):
        """Create a residual block."""
        downsample = None
        if stride != 1 or self.in_channels != out_channels:
            downsample = nn.Sequential(
                nn.Conv2d(self.in_channels, out_channels, kernel_size=1, stride=stride, bias=False),
                nn.BatchNorm2d(out_channels),
            )
        layers = [BasicBlock(self.in_channels, out_channels, stride, downsample)]
        self.in_channels = out_channels
        for _ in range(1, blocks):
            layers.append(BasicBlock(self.in_channels, out_channels))
        return nn.Sequential(*layers)

    def forward(self, x):
        x = self.conv1(x)
        x = self.bn1(x)
        x = self.relu(x)
        x = self.maxpool(x)
        x = self.layer1(x)
        x = self.layer2(x)
        x = self.layer3(x)
        x = self.layer4(x)
        x = self.avgpool(x)
        x = torch.flatten(x, 1)
        x = self.fc(x)
        return x
    
# Data preprocessing
transform = transforms.Compose([
    transforms.Resize((224, 224)),  # ResNet expects 224x224 images
    transforms.ToTensor(),
    transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5)),
])

# Load CIFAR-10 dataset
train_dataset = datasets.CIFAR10(root="./data", train=True, transform=transform, download=True)
test_dataset = datasets.CIFAR10(root="./data", train=False, transform=transform, download=True)

train_loader = DataLoader(train_dataset, batch_size=64, shuffle=True)
test_loader = DataLoader(test_dataset, batch_size=64, shuffle=False)

for i in train_loader:
  batch_index = 0
  print(i[0][batch_index].shape)
  print(i[1][batch_index])
  break

def train(model, dataloader, criterion, optimizer, device):
    model.train()
    running_loss = 0.0
    correct = 0
    total = 0

    for images, labels in dataloader:
        images, labels = images.to(device), labels.to(device)

        # Forward pass
        outputs = model(images)
        loss = criterion(outputs, labels)

        # Backward pass and optimization
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

        # Metrics
        running_loss += loss.item()
        _, predicted = outputs.max(1)
        total += labels.size(0)
        correct += predicted.eq(labels).sum().item()

    epoch_loss = running_loss / len(dataloader)
    accuracy = 100.0 * correct / total
    return epoch_loss, accuracy


def evaluate(model, dataloader, criterion, device):
    model.eval()
    running_loss = 0.0
    correct = 0
    total = 0

    with torch.no_grad():
        for images, labels in dataloader:
            images, labels = images.to(device), labels.to(device)
            outputs = model(images)
            loss = criterion(outputs, labels)

            running_loss += loss.item()
            _, predicted = outputs.max(1)
            total += labels.size(0)
            correct += predicted.eq(labels).sum().item()

    epoch_loss = running_loss / len(dataloader)
    accuracy = 100.0 * correct / total
    return epoch_loss, accuracy

# Hyperparameters
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model = ResNet34(num_classes=10).to(device)
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

from torchsummary import summary

summary(model, (3, 224, 224))
#----------------------------------------------------------------
#        Layer (type)               Output Shape         Param #
#================================================================
#            Conv2d-1         [-1, 64, 112, 112]           9,408
#       BatchNorm2d-2         [-1, 64, 112, 112]             128
#              ReLU-3         [-1, 64, 112, 112]               0
#         MaxPool2d-4           [-1, 64, 56, 56]               0
#            Conv2d-5           [-1, 64, 56, 56]          36,864
#       BatchNorm2d-6           [-1, 64, 56, 56]             128
#            Conv2d-7           [-1, 64, 56, 56]          36,864
#       BatchNorm2d-8           [-1, 64, 56, 56]             128
#        BasicBlock-9           [-1, 64, 56, 56]               0
#           Conv2d-10           [-1, 64, 56, 56]          36,864
#      BatchNorm2d-11           [-1, 64, 56, 56]             128
#           Conv2d-12           [-1, 64, 56, 56]          36,864
#      BatchNorm2d-13           [-1, 64, 56, 56]             128
#       BasicBlock-14           [-1, 64, 56, 56]               0
#           Conv2d-15           [-1, 64, 56, 56]          36,864
#      BatchNorm2d-16           [-1, 64, 56, 56]             128
#           Conv2d-17           [-1, 64, 56, 56]          36,864
#      BatchNorm2d-18           [-1, 64, 56, 56]             128
#       BasicBlock-19           [-1, 64, 56, 56]               0
#           Conv2d-20          [-1, 128, 28, 28]           8,192
#      BatchNorm2d-21          [-1, 128, 28, 28]             256
#           Conv2d-22          [-1, 128, 28, 28]          73,728
#      BatchNorm2d-23          [-1, 128, 28, 28]             256
#           Conv2d-24          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-25          [-1, 128, 28, 28]             256
#       BasicBlock-26          [-1, 128, 28, 28]               0
#           Conv2d-27          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-28          [-1, 128, 28, 28]             256
#           Conv2d-29          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-30          [-1, 128, 28, 28]             256
#       BasicBlock-31          [-1, 128, 28, 28]               0
#           Conv2d-32          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-33          [-1, 128, 28, 28]             256
#           Conv2d-34          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-35          [-1, 128, 28, 28]             256
#       BasicBlock-36          [-1, 128, 28, 28]               0
#           Conv2d-37          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-38          [-1, 128, 28, 28]             256
#           Conv2d-39          [-1, 128, 28, 28]         147,456
#      BatchNorm2d-40          [-1, 128, 28, 28]             256
#       BasicBlock-41          [-1, 128, 28, 28]               0
#           Conv2d-42          [-1, 256, 14, 14]          32,768
#      BatchNorm2d-43          [-1, 256, 14, 14]             512
#           Conv2d-44          [-1, 256, 14, 14]         294,912
#      BatchNorm2d-45          [-1, 256, 14, 14]             512
#           Conv2d-46          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-47          [-1, 256, 14, 14]             512
#       BasicBlock-48          [-1, 256, 14, 14]               0
#           Conv2d-49          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-50          [-1, 256, 14, 14]             512
#           Conv2d-51          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-52          [-1, 256, 14, 14]             512
#       BasicBlock-53          [-1, 256, 14, 14]               0
#           Conv2d-54          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-55          [-1, 256, 14, 14]             512
#           Conv2d-56          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-57          [-1, 256, 14, 14]             512
#       BasicBlock-58          [-1, 256, 14, 14]               0
#           Conv2d-59          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-60          [-1, 256, 14, 14]             512
#           Conv2d-61          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-62          [-1, 256, 14, 14]             512
#       BasicBlock-63          [-1, 256, 14, 14]               0
#           Conv2d-64          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-65          [-1, 256, 14, 14]             512
#           Conv2d-66          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-67          [-1, 256, 14, 14]             512
#       BasicBlock-68          [-1, 256, 14, 14]               0
#           Conv2d-69          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-70          [-1, 256, 14, 14]             512
#           Conv2d-71          [-1, 256, 14, 14]         589,824
#      BatchNorm2d-72          [-1, 256, 14, 14]             512
#       BasicBlock-73          [-1, 256, 14, 14]               0
#           Conv2d-74            [-1, 512, 7, 7]         131,072
#      BatchNorm2d-75            [-1, 512, 7, 7]           1,024
#           Conv2d-76            [-1, 512, 7, 7]       1,179,648
#      BatchNorm2d-77            [-1, 512, 7, 7]           1,024
#           Conv2d-78            [-1, 512, 7, 7]       2,359,296
#      BatchNorm2d-79            [-1, 512, 7, 7]           1,024
#       BasicBlock-80            [-1, 512, 7, 7]               0
#           Conv2d-81            [-1, 512, 7, 7]       2,359,296
#      BatchNorm2d-82            [-1, 512, 7, 7]           1,024
#           Conv2d-83            [-1, 512, 7, 7]       2,359,296
#      BatchNorm2d-84            [-1, 512, 7, 7]           1,024
#       BasicBlock-85            [-1, 512, 7, 7]               0
#           Conv2d-86            [-1, 512, 7, 7]       2,359,296
#      BatchNorm2d-87            [-1, 512, 7, 7]           1,024
#           Conv2d-88            [-1, 512, 7, 7]       2,359,296
#      BatchNorm2d-89            [-1, 512, 7, 7]           1,024
#       BasicBlock-90            [-1, 512, 7, 7]               0
#AdaptiveAvgPool2d-91            [-1, 512, 1, 1]               0
#           Linear-92                   [-1, 10]           5,130
#================================================================
#Total params: 21,289,802
#Trainable params: 21,289,802
#Non-trainable params: 0
#----------------------------------------------------------------
#Input size (MB): 0.57
#Forward/backward pass size (MB): 75.23
#Params size (MB): 81.21
#Estimated Total Size (MB): 157.02
#----------------------------------------------------------------

num_epochs = 5

for epoch in range(num_epochs):
    train_loss, train_accuracy = train(model, train_loader, criterion, optimizer, device)
    test_loss, test_accuracy = evaluate(model, test_loader, criterion, device)

    print(f"Epoch {epoch+1}/{num_epochs}")
    print(f"Train Loss: {train_loss:.4f}, Train Accuracy: {train_accuracy:.2f}%")
    print(f"Test Loss: {test_loss:.4f}, Test Accuracy: {test_accuracy:.2f}%")

```
