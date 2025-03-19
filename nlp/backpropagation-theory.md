# Backpropagation theory

* y = $$x^2$$
* z = sin(y)
* $$dz/ dx = (dz/dy * dy/dx)$$
* cos(y) \* 2x
* $$2x * cos(x^2)$$
* This is known as chain rule
* We can calculate this very easily using pytorch

```python
def dy_dx(x):
    return 2*x
    
dy_dx(4) # 8

import torch
x=torch.tensor(3.0,requires_grad=True)

y=x**2
# tensor(9., grad_fn=<PowBackward0>)

y.backward()

x.grad
# tensor(6.)

import math
def dz_dx(x):
    return 2*x*math.cos(x**2)
    
dz_dx(3)
# -5.466781571308061

dz_dz(5)
# 9.912028118634735

x=torch.tensor(3.0,requires_grad=True)
# tensor(3., requires_grad=True)

y=x**2
z=torch.sin(y)

z.backward()
x.grad
# tensor(-5.4668)
```
