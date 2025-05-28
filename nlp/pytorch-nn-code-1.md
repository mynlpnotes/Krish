# PyTorch NN Code - 1

**In NN:**

1. FP
2. Loss calculation
3. BP
4. Weight updation

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```python
import torch.nn as nn


# This will create input and hidden layer
# There will be 1 unit in hidden layer
# On top of the calculation we will apply sigmoid 
class Model(nn.Module):
    def __init__(self,new_features):
        super().__init__()
        self.linear=nn.Linear(new_features,1) 
        self.sigmoid=nn.Sigmoid()
    def forward(self,features):
        out=self.linear(features)
        out=self.sigmoid(out)
        return out

data=torch.rand(10,5)
#tensor([[0.9362, 0.8712, 0.2160, 0.4761, 0.0445],
#        [0.8966, 0.6267, 0.6745, 0.2108, 0.1460],
#        [0.9658, 0.2175, 0.3805, 0.9085, 0.4873],
#        [0.0772, 0.4220, 0.3601, 0.0319, 0.0323],
#        [0.5513, 0.0164, 0.7468, 0.5560, 0.7707],
#        [0.7749, 0.9950, 0.7933, 0.3880, 0.3180],
#        [0.3236, 0.9064, 0.7137, 0.8370, 0.7591],
#        [0.0312, 0.9517, 0.8162, 0.0240, 0.6799],
#        [0.6275, 0.7951, 0.8659, 0.3556, 0.3848],
#        [0.7894, 0.2636, 0.3880, 0.9244, 0.2391]])

model=Model(data.shape[1]) # shape[1] is 5 -- number of neurons in input layer

model(data)
model.forward(data)
# Both will give the same output
#tensor([[0.4047],
#        [0.4580],
#        [0.4253],
#        [0.4305],
#        [0.4759],
#        [0.4282],
#        [0.3897],
#        [0.4525],
#        [0.4396],
#        [0.3974]], grad_fn=<SigmoidBackward0>)


model.linear.weight
# tensor([[ 0.2097, -0.2031,  0.0857, -0.4179,  0.2535]], requires_grad=True)

model.linear.bias
# tensor([-0.2360], requires_grad=True)
```
