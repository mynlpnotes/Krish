# 🟢 Gradient Descent

1. Take the derivative of the loss function for each parameter in it
   1. y = mx + c
2. Pick random values for the parameter
3. Plug parameter values into the derivative&#x20;
4. Calculate step size -> Step size = slope \* learning rate
5. Calculate new parameters
   1. $$m_{new} = m_{old} - step size$$
   2. $$c_{new} = c_{old} - step size$$
6. Repeat 3,4,5 till we get close to the global minima
