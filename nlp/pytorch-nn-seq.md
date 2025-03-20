# PyTorch NN Seq

```python
# create model class
import torch
import torch.nn as nn
import numpy as np
import pandas as pd
import torch
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.preprocessing import LabelEncoder

class Model(nn.Module):
  def __init__(self, num_features):
    super().__init__()
    self.network = nn.Sequential(
        nn.Linear(num_features, 3),
        nn.ReLU(),
        nn.Linear(3, 1),
        nn.Sigmoid()
    )

  def forward(self, features):
    out = self.network(features)
    return out

model=Model(data.shape[1])
model.forward(data)

from torchinfo import summary
summary(model)
#=================================================================
#Layer (type:depth-idx)                   Param #
#=================================================================
#Model                                    --
#├─Sequential: 1-1                        --
#│    └─Linear: 2-1                       18
#│    └─ReLU: 2-2                         --
#│    └─Linear: 2-3                       4
#│    └─Sigmoid: 2-4                      --
#=================================================================
#Total params: 22
#Trainable params: 22
#Non-trainable params: 0
#=================================================================

data=pd.read_csv("https://raw.githubusercontent.com/gscdit/Breast-Cancer-Detection/refs/heads/master/data.csv")

data.drop(columns=['id','Unnamed: 32'],inplace=True)

data["diagnosis"].value_counts()
#diagnosis
#B    357
#M    212
#Name: count, dtype: int64

X_train, X_test, y_train, y_test = train_test_split(data.iloc[:, 1:], data.iloc[:, 0], test_size=0.2)

scaler=StandardScaler()
X_train=scaler.fit_transform(X_train)
X_test=scaler.transform(X_test)

encoder = LabelEncoder()
y_train = encoder.fit_transform(y_train)
y_test = encoder.transform(y_test)

X_train_tensor = torch.from_numpy(X_train.astype(np.float32))
X_test_tensor = torch.from_numpy(X_test.astype(np.float32))
y_train_tensor = torch.from_numpy(y_train.astype(np.float32))
y_test_tensor = torch.from_numpy(y_test.astype(np.float32))

class MySimpleNN(nn.Module):
    def __init__(self,new_features):
        super().__init__()
        self.linear1=nn.Linear(new_features,3)
        self.relu=nn.ReLU()
        self.linear2=nn.Linear(3,1)
        self.sigmoid=nn.Sigmoid()
    def forward(self,features):
        out=self.linear1(features)
        out=self.relu(out)
        out=self.linear2(out)
        out=self.sigmoid(out)
        return out

learning_rate=0.01
epochs=25

loss_function=nn.BCELoss()
model=MySimpleNN(X_train.shape[1])
optimizer=torch.optim.SGD(model.parameters(), lr=learning_rate)

for epoch in range(epochs):
    # forward pass
    y_pred = model(X_train_tensor)
    # loss calculate
    loss = loss_function(y_pred, y_train_tensor.view(-1,1))
    # clear gradients
    optimizer.zero_grad()
    # For computing backward graph
    loss.backward()
    # parameters update
    optimizer.step()
    
    # print loss in each epoch
    print(f'Epoch: {epoch + 1}, Loss: {loss.item()}')
#Epoch: 1, Loss: 0.668727457523346
#Epoch: 2, Loss: 0.6659935116767883.....

# We dont want gradient to be calculated on test data
with torch.no_grad():
    y_pred=model.forward(X_test_tensor)
    y_pred=(y_pred>0.5).float()
    accuracy = (y_pred == y_test_tensor).float().mean()
    print(f'Accuracy: {accuracy.item()}')


    
    


```
