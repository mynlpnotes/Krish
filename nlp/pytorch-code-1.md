# PyTorch Code - 1

```python
# It generates matrix of 2X3 which will be filled with random value from RAM
a = torch.empty(2,3)
# tensor([[0., 0., 0.],
#        [0., 0., 0.]])

type(a)
# torch.Tensor

# Fill with given value
a.fill_(0)
# tensor([[0., 0., 0.],
#        [0., 0., 0.]])

# Create a matrix of 2X3 having 0
torch.zeros(2,3)
# tensor([[0., 0., 0.],
#        [0., 0., 0.]])

# Create a matrix of 2X3 having 1
torch.ones(2,3)
# tensor([[1., 1., 1.],
#        [1., 1., 1.]])

# Random values
torch.rand(3,4)
# tensor([[0.8288, 0.7899, 0.7800, 0.8160],
#         [0.8974, 0.7732, 0.9998, 0.4527],
#         [0.1629, 0.1569, 0.0052, 0.1169]])

# Set seed to get same random values everytime
torch.manual_seed(10)
torch.rand(3,4)

# Manually creating a tensor
torch.tensor([[1,2,3],[3,4,5]])
# tensor([[1, 2, 3],
#         [3, 4, 5]])

# Range 0 to 9
torch.arange(10)
# tensor([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

torch.arange(1,10,2)
# tensor([1, 3, 5, 7, 9])

torch.linspace(0,1,30)
#tensor([0.0000, 0.0345, 0.0690, 0.1034, 0.1379, 0.1724, 0.2069, 0.2414, 0.2759,
#        0.3103, 0.3448, 0.3793, 0.4138, 0.4483, 0.4828, 0.5172, 0.5517, 0.5862,
#        0.6207, 0.6552, 0.6897, 0.7241, 0.7586, 0.7931, 0.8276, 0.8621, 0.8966,
#        0.9310, 0.9655, 1.0000])

# To create identitiy matrix
torch.eye(5)
#tensor([[1., 0., 0., 0., 0.],
#        [0., 1., 0., 0., 0.],
#        [0., 0., 1., 0., 0.],
#        [0., 0., 0., 1., 0.],
#        [0., 0., 0., 0., 1.]])

torch.full((3,3),5)
#tensor([[5, 5, 5],
#        [5, 5, 5],
#        [5, 5, 5]])

x = torch.tensor([[1,2,3],[3,4,5]])
torch.empty_like(x)
# This will have garbage values but will have size 2X3

torch.zeros_like(x)
# This will have 0 with size 2X3

torch.rand_like(x,dtype=torch.float32)
# 2X3 with type float32

x+2
# Will be added to each element

x-2
x*3
x/3

torch.abs(c)
# It will give absolute value of each element

torch.neg(c)
torch.round(d)
torch.floor(d)
torch.ceil(d)

e=torch.randint(size=(3,4),low=0,high=10,dtype=torch.float32)

torch.sum(e) # tensor(63.)

# Column wise Addition
torch.sum(e, dim=0)
# tensor([20., 16., 12., 15.])

# Row wise addition
torch.sum(e, dim=1)
# tensor([32., 13., 18.])

torch.mean(e, dim=1)
torch.mean(e)
torch.min(e)
torch.max(e)

# argmax it is giving me index of highest value in matrix
torch.argmax(e)
# tensor(2)

torch.argmin(e)

f = torch.randint(size=(2,3), low=0, high=10)
g = torch.randint(size=(3,2), low=0, high=10)

torch.matmul(f,g)
# tensor([[53, 56],
#        [22, 14]])

vector1 = torch.tensor([1, 2])
vector2 = torch.tensor([3, 4])

torch.dot(vector1,vector2)
# tensor(11)

torch.transpose(f,0,1)
# tensor([[1, 4],
#        [5, 0],
#        [3, 2]])

h
#tensor([[6., 1., 9.],
#        [9., 0., 9.],
#        [2., 5., 9.]])

torch.inverse(h)
#tensor([[-0.6250,  0.5000,  0.1250],
#        [-0.8750,  0.5000,  0.3750],
#        [ 0.6250, -0.3889, -0.1250]])

torch.log(h)
torch.exp(h)
torch.softmax(h,0)
```
