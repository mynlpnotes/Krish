# Handwritten Digit Classifier

```python
import torch
import torch.nn as nn
import torch.nn.functional as F
from torch.utils.data import DataLoader, random_split
from torchvision import datasets, transforms
import matplotlib.pyplot as plt

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5,))  # Normalize to [-1, 1]
])

# https://pytorch.org/vision/main/generated/torchvision.datasets.MNIST.html
train_dataset = datasets.MNIST(root='data', train=True, transform=transform, download=True)
test_dataset = datasets.MNIST(root='data', train=False, transform=transform, download=True)

print(len(train_dataset.__getitem__(0))) # 2 - Image and label
print(len(train_dataset.__getitem__(0)[0].shape)) # 3
print(train_dataset.__getitem__(0)[0].shape) # 1X28X28
print(f"Image label is : {train_dataset.__getitem__(0)[1]}") # 5 
plt.imshow(train_dataset.__getitem__(0)[0].squeeze(), cmap="grey") # Display the image

batch_size = 64

# Split train dataset into train and validation
train_size = int(0.8 * len(train_dataset))
val_size = len(train_dataset) - train_size
train_dataset, val_dataset = random_split(train_dataset, [train_size, val_size])

train_loader = DataLoader(train_dataset, batch_size=batch_size, shuffle=True)
val_loader = DataLoader(val_dataset, batch_size=batch_size, shuffle=False)
test_loader = DataLoader(test_dataset, batch_size=batch_size, shuffle=False)

class DigitClassifier(nn.Module):
    def __init__(self):
        super(DigitClassifier, self).__init__()
        self.fc1 = nn.Linear(28 * 28, 128)
        self.fc2 = nn.Linear(128, 64)
        self.fc3 = nn.Linear(64, 10)
        # self.lrn = nn.LocalResponseNorm(size=5, alpha=1e-4, beta=0.75, k=2)

    def forward(self, x):
        x = x.reshape(-1, 28 * 28)  # Flatten the image
        # x = x.view(-1, 28 * 28)  # Flatten the image
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x
        
learning_rate = 0.001

model = DigitClassifier().to(device)
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=learning_rate)

# Training function
def train(model, loader, criterion, optimizer):
    model.train()
    running_loss = 0.0
    correct = 0
    total = 0
    for images, labels in loader:
        images, labels = images.to(device), labels.to(device)

        # Forward pass
        outputs = model(images)
        loss = criterion(outputs, labels)

        # Backward pass
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

        # Statistics
        running_loss += loss.item() * images.size(0)
        _, predicted = outputs.max(1)
        total += labels.size(0)
        correct += predicted.eq(labels).sum().item()

    epoch_loss = running_loss / total
    accuracy = correct / total
    return epoch_loss, accuracy

# Validation function
def evaluate(model, loader, criterion):
    model.eval()
    running_loss = 0.0
    correct = 0
    total = 0
    with torch.no_grad():
        batch = 1
        for images, labels in loader:
            print(f"Current batch : {batch}")
            images, labels = images.to(device), labels.to(device)

            outputs = model(images)
            loss = criterion(outputs, labels)

            running_loss += loss.item()
            print(f"Running loss : {running_loss}")
            _, predicted = outputs.max(1)
            total += labels.size(0)
            correct += predicted.eq(labels).sum().item()
            batch += 1

    epoch_loss = running_loss / batch
    accuracy = correct / total
    return epoch_loss, accuracy

num_epochs = 2

for epoch in range(num_epochs):
    train_loss, train_acc = train(model, train_loader, criterion, optimizer)
    val_loss, val_acc = evaluate(model, val_loader, criterion)

    print(f"Epoch [{epoch+1}/{num_epochs}], "
          f"Train Loss: {train_loss:.4f}, Train Acc: {train_acc:.4f}, "
          f"Val Loss: {val_loss:.4f}, Val Acc: {val_acc:.4f}")
 
 # Testing
test_loss, test_acc = evaluate(model, test_loader, criterion)
print(f"Test Loss: {test_loss:.4f}, Test Accuracy: {test_acc:.4f}")

# Save the model
torch.save(model.state_dict(), "mnist_digit_classifier.pth")
print("Model saved as mnist_digit_classifier.pth")

# Inference
# Load the model
loaded_model = DigitClassifier().to(device)
loaded_model.load_state_dict(torch.load("mnist_digit_classifier.pth"))
loaded_model.eval()
print("Model loaded for inference.")

# Inference
def predict(model, image):
    model.eval()
    with torch.no_grad():
        image = image.to(device)
        output = model(image)
        _, predicted = output.max(1)
    return predicted.item()
    
# Function to preprocess the image
# In training we have used images in which we had black background and number was white
# so here also we doing bitwise not so that to reverse the colours
def preprocess_image(image):

    image = cv2.bitwise_not(image)

    transform = transforms.Compose([
        transforms.ToPILImage(),             # Convert to PIL image
        # https://pytorch.org/vision/0.8/transforms.html

        transforms.Grayscale(num_output_channels=1),  # Convert to grayscale
        transforms.Resize((28, 28)),        # Resize to match MNIST input size
        transforms.ToTensor(),              # Convert to tensor
        transforms.Normalize((0.5,), (0.5,))  # Normalize
    ])
    image = transform(image)  # Apply transforms
    # image = image.unsqueeze(0)  # Add batch dimension (1, 1, 28, 28)
    return image



```
