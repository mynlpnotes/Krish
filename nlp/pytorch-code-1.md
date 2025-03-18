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





```
