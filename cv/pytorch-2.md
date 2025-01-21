# Pytorch - 2

Stack means 1 matrix over another

```python
tensor_random = torch.randn(4, 4)

# View
tensor_random_view_1 = tensor_random.view(16) 
tensor_random_view_2 = tensor_random.view(-1, 8)

# Reshape
tensor_random_reshape = torch.reshape(tensor_random, (4, 4))
tensor_random_flatten =  torch.reshape(tensor_random_reshape, (-1,))
# When we specify -1 shape is calculated automatically to flatten it to a single 
#     vector

# Stack
random_stack = torch.randn(2, 3)
random_stack_dim_default = torch.stack((random_stack, random_stack))
'''
[        ⬅ New dimension (dim=0, outer)
  [ [0.5174, -1.6801, -1.7602],      ⬅ Original tensor 1
    [1.2056, -0.1794,  0.9064] ],

  [ [0.5174, -1.6801, -1.7602],      ⬅ Original tensor 2
    [1.2056, -0.1794,  0.9064] ]
]
Dimension after stacking => 2,2,3
The new dimension is added before the rows
'''

random_stack_dim_1 = torch.stack((random_stack, random_stack), dim=1)
'''
[
  [ [0.5174, -1.6801, -1.7602], [0.5174, -1.6801, -1.7602] ],  ⬅ Rows are stacked (dim=1)
  [ [1.2056, -0.1794,  0.9064], [1.2056, -0.1794,  0.9064] ]
]

The new dimension is added between the rows and columns
'''
# Results in Tensor Transpose
random_stack_dim_2 = torch.stack((random_stack, random_stack), dim=2)



```
