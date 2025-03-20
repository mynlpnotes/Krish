# PyTorch NN Code - 2

<figure><img src="../.gitbook/assets/image (554).png" alt=""><figcaption></figcaption></figure>

```python
class Model(nn.Module):
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
        
data=torch.rand(10,5)

model=Model(data.shape[1])
model(data)

model.linear1.weight
#Parameter containing:
#tensor([[ 0.4089, -0.3888, -0.2924,  0.2196, -0.4404],
#        [-0.0017,  0.0951, -0.3202,  0.4281,  0.0178],
#        [-0.0839, -0.2110,  0.2407, -0.0181, -0.2688]], requires_grad=True)

model.linear1.bias
#Parameter containing:
#tensor([-0.2832,  0.1767,  0.3792], requires_grad=True)

model.linear2.weight
model.linear2.bias
```
