# 🟠 Batch Normalization - ChatGPT

* Batch Normalization (BN) is a technique to <mark style="color:purple;background-color:purple;">**normalize the intermediate outputs (activations) of a neural network layer**</mark>.&#x20;
* <mark style="color:purple;background-color:purple;">**It helps stabilize training, reduce dependency on initialization, and improve convergence speed.**</mark>&#x20;
* BN is especially useful in deep networks like CNNs.
* <mark style="color:purple;background-color:purple;">**Calculate separately for each batch**</mark>

#### **Key Steps in Batch Normalization**

1. **Input Normalization**: For a given batch, compute the mean (μ) and variance (σ²) of the activations.
2. **Normalize**: Subtract the mean and divide by the standard deviation to center the data around 0 with unit variance: $$\hat{x} = \frac{x - \mu}{\sqrt{\sigma^2 + \epsilon}}$$ (ε is a small constant to prevent division by zero.)
3. **Scale and Shift**: Transform the normalized values with learnable parameters $$γ (scale) and β (shift): y=γx^+β]y = \gamma \hat{x} + \beta \\$$

***

#### **Why Are γ and β Needed?**

1. **Flexibility in Representation**: Without γ and β, the normalized values would remain constrained with fixed mean (0) and variance (1). This could limit the model's ability to represent certain functions. γ and β provide the flexibility to adjust these values.
2. **Trainable Scaling and Shifting**:
   * **γ**: Controls the scale of the normalized values.
   * **β**: Shifts the normalized values.
3. These parameters are learned during training through **backpropagation** and are initialized as:
   * γ = 1 (default scale).
   * β = 0 (default shift).

***

#### **Where BN is Applied**

* <mark style="color:purple;background-color:purple;">**Typically after the convolution or fully connected layer and before the activation function.**</mark>
* In CNNs, normalization is applied at the channel level.

***

#### **Code Example with Learnable Parameters**

```python
import torch
import torch.nn as nn

# Define BatchNorm for 1D data
batch_norm = nn.BatchNorm1d(3)  # 3 channels

# Print the initial values of gamma (weight) and beta (bias)
print("Initial gamma (scale):", batch_norm.weight)
print("Initial beta (shift):", batch_norm.bias)

# Forward pass through BatchNorm
x = torch.randn(5, 3)  # 5 samples, 3 features
output = batch_norm(x)

print("Output after BatchNorm:", output)
```

***

#### **Detailed Calculation Example**

**Assume:**

* Batch size: 2
* Channels: 1 (grayscale image)
* Image size: 2 × 2

**Input Tensor (xx):**

x=\[12345678]x = \begin{bmatrix} 1 & 2 \\\ 3 & 4 \\\ 5 & 6 \\\ 7 & 8 \end{bmatrix}

1. **Compute Mean (μ) and Variance (σ²) for the Batch:**
   * μ = 1+2+3+...+88=4.5\frac{1+2+3+...+8}{8} = 4.5
   * σ² = (1−4.5)2+(2−4.5)2+...+(8−4.5)28=5.25\frac{(1-4.5)^2 + (2-4.5)^2 + ... + (8-4.5)^2}{8} = 5.25
2.  **Normalize Each Element (x^\hat{x}):**

    *

    \hat{x}_{ij} = \frac{x_{ij} - 4.5}{\sqrt{5.25 + \epsilon\}} ]
3. **Scale and Shift with Learnable Parameters (γ = 1, β = 0):**
   * Output: y=x^y = \hat{x}.

***

#### **Summary Table**

| **Step**              | **Operation**                | **Formula**                                                          |
| --------------------- | ---------------------------- | -------------------------------------------------------------------- |
| Compute Mean          | Average of batch activations | μ=1N∑i=1Nxi\mu = \frac{1}{N} \sum\_{i=1}^N x\_i                      |
| Compute Variance      | Spread of batch activations  | σ2=1N∑i=1N(xi−μ)2\sigma^2 = \frac{1}{N} \sum\_{i=1}^N (x\_i - \mu)^2 |
| Normalize Activations | Center and scale             | x^=x−μσ2+ϵ\hat{x} = \frac{x - \mu}{\sqrt{\sigma^2 + \epsilon\}}      |
| Scale and Shift       | Learnable adjustment         | y=γx^+βy = \gamma \hat{x} + \beta                                    |

***

#### **Takeaway**

* **γ** and **β** are learnable parameters that adapt normalization to improve model performance.
* They provide the necessary flexibility for the network to learn better representations of data.
