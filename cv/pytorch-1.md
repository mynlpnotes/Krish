# Pytorch code

```python
import torch

print(torch.__version__)

# TO store scalar
scalar = torch.tensor(2)
print(scalar) # tensor(2)

# Dimension
scalar.ndim # 0 - Dimension of tensor

# To check what is present in the tensor
scalar.item()  # 2

# Vector : Single dimesnion vector, just like 1D array. Can contain many numbers.
vector = torch.tensor([0, 1])
vector.ndim # 1
vecotor.shape # torch.Size([2])
vector[0].item() # 0

# Matrix, same as vector but has 2D
Matrix = torch.tensor([[0, 1],
                       [3, 4]])
Matrix.ndim # 2
Matrix.shape # torch.Size([2,2])

# Tensor, n-Dimension
Tensor = torch.tensor([[0, 1],
                       [3, 4],
                       [5,6]])
print(Tensor.ndim) # 2
print(Tensor.shape) # torch.Size([3,2])

# Tensor, n-Dimension
Tensor = torch.tensor([[[0, 1],
                       [3, 4],
                       [5,6]]])

print(Tensor.ndim) # 3
print(Tensor.shape) # 1,3,2 means 1 dimension of shape 3,2

print(Tensor[0]) # First Square Bracket 
print(Tensor[0][0]) # Second Square Bracket -- tensor([0, 1])
print(Tensor[0][0][0]) # Third Square Bracket -- tensor(0)

print(Tensor[:, 0])  # tensor([[0, 1]])
print(Tensor[:,:,1]) # tensor([[1, 4, 6]])
print(Tensor[:,2,1]) # tensor([6])

## Random Numbers
random_tensor = torch.rand(size=(3, 4))
# Generate random image noise
random_image_tensor = torch.rand(size=(150, 150, 3))

# Convert tensor to numpy and then display using cv2
from google.colab.patches import cv2_imshow
random_image_np = random_image_tensor.numpy()
cv2_imshow(random_image_np)

# Tensor of Zeros and Ones
zeros = torch.zeros(size=(3, 4))
ones = torch.ones(size=(3, 4))

# Range of values
range = torch.arange(start=0, end=20)
range = torch.arange(start=0, end=20, step=2)
range.to_list # to convert it into list

# Default datatype for tensors is float32
tensor_example = torch.tensor([0, 1, 2],
                          dtype=None, # defaults to None, which is torch.int64 or whatever datatype is passed
                          device=None, # defaults to None, which uses the default tensor type
                          requires_grad=False) # if True, operations performed on the tensor are recorded

print(tensor_example)
print(tensor_example.dtype) # torch.int64
print(tensor_example.device) # cpu

# Tensor Manipulation
tensor_t = torch.tensor([1,2,3,4])
# Adition
print(tensor_t + 10) # tensor([11, 12, 13, 14])
print(torch.add(tensor_t, 10)) # tensor([11, 12, 13, 14])
# Subtraction
print(tensor_t - 10) # tensor([-9, -8, -7, -6])
print(torch.subtract(tensor_t, 10)) # tensor([-9, -8, -7, -6])
# Multiplication
print(tensor_t * 10)
print(torch.mul(tensor_t, 10))
# Division
print(tensor_t / 10)
print(torch.div(tensor_t, 10))

# Element wise multiplication
print(tensor_t * tensor_t)

# Matrix Multiplication or DOT Product
print(torch.matmul(tensor_t, tensor_t))
# [1*1 + 2*2 + 3*3 + 4*4]
# [1 + 4 + 9 + 16]
# [10 + 20] = [30]

# Matrix Aggregation
tensor_agg.min()
tensor_agg.max()
tensor_agg.mean()
tensor_agg.argmax() # Index where max value occurs
tensor_agg[tensor_agg.argmax()].item()




```
