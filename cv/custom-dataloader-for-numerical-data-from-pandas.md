# Custom DataLoader for Numerical Data (from Pandas)

To load numerical data (e.g., from a CSV file or a Pandas DataFrame), we create a custom dataset class that extends torch.utils.data.Dataset. This class should implement three key methods:

* **init**: Initializes the dataset.
* **len**: Returns the size of the dataset.
* **getitem**: Retrieves a sample from the dataset

```python
import torch
from torch.utils.data import Dataset, DataLoader
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

df = pd.read_csv(csv_file)  # Replace with your CSV file
X = df.drop('target', axis=1)  # Features
y = df['target']  # Labels

# Split the data
X_train, X_temp, y_train, y_temp = train_test_split(X, y, test_size=0.4, random_state=42)
X_val, X_test, y_val, y_test = train_test_split(X_temp, y_temp, test_size=0.5, random_state=42)

# Normalize features using StandardScaler (optional)
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_val = scaler.transform(X_val)
X_test = scaler.transform(X_test)

print(X_train[0, :])
print(type(X_train))
print(y_train.values)
print(type(y_train))
# Create Dataset objects
train_dataset = NumericalDataset(X_train, y_train)
val_dataset = NumericalDataset(X_val, y_val)
test_dataset = NumericalDataset(X_test, y_test)

# Create DataLoader objects
train_loader = DataLoader(dataset=train_dataset, batch_size=32, shuffle=True)
val_loader = DataLoader(dataset=val_dataset, batch_size=32, shuffle=False)
test_loader = DataLoader(dataset=test_dataset, batch_size=32, shuffle=False)

# Example: Iterating through batches of the train_loader
for data_batch, labels_batch in train_loader:
    print(data_batch.shape, labels_batch.shape)


```
