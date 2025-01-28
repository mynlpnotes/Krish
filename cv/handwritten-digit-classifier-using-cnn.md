# Handwritten Digit Classifier using CNN

```python
class CNN(nn.Module):
    def __init__(self):
        super(CNN, self).__init__()
        self.conv1 = nn.Conv2d(1, 32, kernel_size=3, stride=1, padding=1)  # Output: 32x28x28
        self.relu = nn.ReLU()
        self.pool = nn.MaxPool2d(kernel_size=2, stride=2)                 # Output: 32x14x14
        self.conv2 = nn.Conv2d(32, 64, kernel_size=3, stride=1, padding=1) # Output: 64x14x14
        self.fc1 = nn.Linear(64 * 7 * 7, 128)                            # Fully connected layer
        self.fc2 = nn.Linear(128, 10)                                    # 10 classes for digits (0-9)

    def forward(self, x):
        # 1x28x28
        x = self.conv1(x) # 32×28×28
        x = self.relu(x)


        x = self.pool(x) # 32×14×14
        x = self.conv2(x) # 64×14×14
        x = self.relu(x)
        x = self.pool(x) # MaxPool2
        x = x.view(x.size(0), -1)  # Flatten the tensor # 3136
        x = self.fc1(x) # 128
        x = self.relu(x)
        x = self.fc2(x) # 10
        return x

# Model, loss function, and optimizer
model = CNN()
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.001)

# Training loop
num_epochs = 10
for epoch in range(num_epochs):
    model.train()
    running_loss = 0.0
    for images, labels in train_loader:
        # Forward pass
        outputs = model(images)
        loss = criterion(outputs, labels)

        # Backward pass and optimization
        optimizer.zero_grad()
        loss.backward()
        optimizer.step()

        running_loss += loss.item()

    print(f"Epoch [{epoch + 1}/{num_epochs}], Loss: {running_loss / len(train_loader):.4f}")

# Save the model
torch.save(model.state_dict(), "mnist_digit_classifier_cnn.pth")
print("Model saved as mnist_digit_classifier_cnn.pth")

# Load the model
loaded_model = CNN().to(device)
loaded_model.load_state_dict(torch.load("mnist_digit_classifier_cnn.pth"))
loaded_model.eval()
print("Model loaded for inference.")

from PIL import Image

# Preprocessing function for a single image
def preprocess_image(image_path):


    transform = transforms.Compose([
        transforms.ToPILImage(),
        transforms.Grayscale(num_output_channels=1),  # Ensure image has one channel
        transforms.Resize((28, 28)),                 # Resize to 28x28 (same as MNIST images)
        transforms.ToTensor(),
        transforms.Normalize((0.5,), (0.5,))         # Normalize with the same mean and std as training
    ])

    image = cv2.imread(image_path)
    image = cv2.bitwise_not(image)

    return transform(image).unsqueeze(0)  # Add batch dimension
    
# Perform inference
def predict_image(image_path):
    # Preprocess the image
    image_tensor = preprocess_image(image_path)

    # Perform forward pass
    with torch.no_grad():
        outputs = model(image_tensor)
        _, predicted = torch.max(outputs, 1)

    return predicted.item()

import cv2

predicted_label = predict_image("/content/four.png")
print(f"Predicted Label: {predicted_label}")
```
