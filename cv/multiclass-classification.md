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

```
