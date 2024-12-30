# Multiclass Classification

```python
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')

iris = load_iris()
X = iris.data  # Features (numerical data)
y = iris.target  # Labels (3 classes)

scaler = StandardScaler()
X = scaler.fit_transform(X)

X = torch.tensor(X, dtype=torch.float32).to(device)
y = torch.tensor(y, dtype=torch.long).to(device)  
# Multi-class requires LongTensor for target

X_train,X_test,y_train,y_test = train_test_split(X, y,test_size=0.2, random_state=42)

# Define the neural network model
class NeuralNetBasic(nn.Module):
    def __init__(self, input_size, hidden_size, num_classes):
        super(NeuralNetBasic, self).__init__()
        self.fc1 = nn.Linear(input_size, hidden_size)  # First fully connected layer
        self.relu = nn.ReLU()  # Activation function
        self.fc2 = nn.Linear(hidden_size, num_classes)  # Output layer for classification

    def forward(self, x):
        out = self.fc1(x)
        out = self.relu(out)
        out = self.fc2(out)
        return out

# Model parameters
input_size = X_train.shape[1]  # Number of features (4 for Iris)
hidden_size = 16  # Arbitrary hidden layer size
num_classes = 3  # Number of output classes (3 for Iris)

# Instantiate the model
model = NeuralNetBasic(input_size, hidden_size, num_classes).to(device)

criterion = nn.CrossEntropyLoss()  # Suitable for multi-class classification
optimizer = optim.Adam(model.parameters(), lr=0.001)  # Adam optimizer

num_epochs = 100  # Number of training iterations
batch_size = 16  # Batch size for training

def train_model(X_train, y_train):
    model.train()
    for epoch in range(num_epochs):
        # Forward pass
        outputs = model(X_train)
        loss = criterion(outputs, y_train)

        # Backward pass and optimization
        optimizer.zero_grad()  # Clear gradients
        loss.backward()  # Backpropagation
        optimizer.step()  # Update model parameters

        if (epoch + 1) % 10 == 0:
            print(f'Epoch [{epoch+1}/{num_epochs}], Loss: {loss.item():.4f}')

train_model(X_train, y_train)

model.eval()  # Set model to evaluation mode (no gradients)

with torch.no_grad():  # No need to compute gradients during testing
    test_outputs = model(X_test)
    _, predicted = torch.max(test_outputs, 1)  # Get the class with highest probability
    accuracy = (predicted == y_test).sum().item() / y_test.size(0)
    print(f'Accuracy on the test set: {accuracy * 100:.2f}%')
    
new_data = torch.tensor([[5.1, 3.5, 1.4, 0.2], [6.5, 3.0, 5.5, 1.8]], dtype=torch.float32).to(device)
new_data = torch.tensor(scaler.transform(new_data.cpu()), dtype=torch.float32).to(device)

with torch.no_grad():
    predictions = model(new_data)
    _, predicted_classes = torch.max(predictions, 1)
    print("Predicted classes for new data:", predicted_classes.cpu().numpy())
```
