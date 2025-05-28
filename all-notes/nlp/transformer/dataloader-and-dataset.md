# Dataloader and Dataset

* When data is huge, data wont fit into RAM, we need to use dataloader there, so that we can process in batches
* Dataset it initalizing the data
* DataLoader is loading the data into batches

```python
from sklearn.datasets import make_classification
import torch

# Step 1: Create a synthetic classification dataset using sklearn
X, y = make_classification(
    n_samples=10,       # Number of samples
    n_features=2,       # Number of features
    n_informative=2,    # Number of informative features
    n_redundant=0,      # Number of redundant features
    n_classes=2,        # Number of classes
    random_state=42     # For reproducibility
)

# Convert the data to PyTorch tensors
X = torch.tensor(X, dtype=torch.float32)
y = torch.tensor(y, dtype=torch.long)

from torch.utils.data import Dataset, DataLoader

class CustomDataSet(Dataset):
    def __init__(self,features,labels):
        self.features=features
        self.labels=labels
        
    def __len__(self):
        return self.features.shape[0]
        
    def __getitem__(self,index):
        return self.features[index],self.labels[index]

dataset=CustomDataSet(X,y)

len(dataset) #2

dataset[2]
dataset[9]

dataloader=DataLoader(dataset,batch_size=2,shuffle=False)

for batch_features, batch_labels in dataloader:
  print(batch_features)
  print(batch_labels)
  print("-"*50)
```
