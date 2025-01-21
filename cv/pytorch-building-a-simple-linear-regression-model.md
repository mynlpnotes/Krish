# Pytorch - Building a simple linear regression model

Steps:

* Declare a class with superclass as nn.module
* In constructor we will define the layers
* In method forward we will apply the transformation
* Create instance of model
* Define loss function
* Define optimizer
* For the n epochs do the following
  * take the y pred
  * Calculate loss
  * Zero gradients ⇒ Clear old gradients before&#x20;
  * Compute gradients ⇒ loss.backward()
  * Update parameters  ⇒ optimizer.step()
  * Print the progress
* torch.nograd() ⇒ we dont want to calculate gradients
* Predict using the model
* torch.squeeze() removes dimensions of size 1 from a tensor, effectively "squeezing" it into a shape with fewer dimensions. This is useful for simplifying the shape of tensors when such dimensions are unnecessary

```python
import torch.nn as nn

X = torch.tensor([[1.0], [2.0], [3.0], [4.0]]) # Input
y = torch.tensor([[2.0], [4.0], [6.0], [8.0]]) # Output

class LinearRegressionModel(nn.Module):
    def __init__(self):
        # Here the class name should be passed
        # We are initializing the bass class here
        super(LinearRegressionModel, self).__init__() 
        # Define the model's parameters
        # nn.linear is a linear layer that applies a linear transformation
        self.linear = nn.Linear(in_features=1, out_features=1)

    def forward(self, x):
        # Define the forward pass
        out = self.linear(x)
        return out

model = LinearRegressionModel()
criterion = nn.MSELoss()# Loss function
optimizer = torch.optim.SGD(model.parameters(), lr=0.01) # Optimizer

num_epochs = 4

for epoch in range(num_epochs):

    y_pred = model(X)              # Forward pass: Compute predicted y
    loss = criterion(y_pred, y)    # Compute loss
    optimizer.zero_grad()          # Zero gradients
    loss.backward()                # Backward pass: Compute gradients
    optimizer.step()               # Update parameters

    # Print progress
    if (epoch+1) % 2 == 0:
        print(f'Epoch [{epoch + 1}/{num_epochs}], Loss: {loss.item():.4f}')

print(f"Model weights {model.linear.weight.data}")
print(f"Model bias {model.linear.bias.data}")

# Test the model
with torch.no_grad():  # Disables gradient calculation
    predicted = model(X)
    print(X.ndim)
    print(X.shape)
    print(X.squeeze().shape)
    print('='*20)
    print('Input values: ', X[:,0])
    print('Input values: ', X.squeeze().numpy())
    print('='*20)
    print('Predicted values:', predicted.squeeze().numpy())
    print('='*20)
    print('Actual values:', y.squeeze().numpy())

# torch.squeeze removes dimensions of size 1 from a tensor

a = torch.tensor([[[3]]])
print(a)
a_new = a.squeeze()
print(a_new)
```
