# Adagrad

* Adaptive Gradient Descent
* It adjusts the learning rate for each parameter individually, which can help improve convergence and performance.

How AdaGrad Works:

1. **Initialization:**
   * Start with an initial learning rate η\etaη and initialize the gradient accumulator, typically set to zero for each parameter.
2. **Per-Parameter Learning Rate:**
   * Unlike traditional stochastic gradient descent (SGD), which uses a single learning rate for all parameters, AdaGrad maintains a different learning rate for each parameter. This is achieved by keeping a running sum of the squares of the gradients for each parameter.
3. **Accumulation of Squared Gradients:**
   * For each iteration ttt and parameter θi\theta\_iθi​, the squared gradient gt,i2g\_{t,i}^2gt,i2​ is accumulated: Gt,i=Gt−1,i+gt,i2G\_{t,i} = G\_{t-1,i} + g\_{t,i}^2Gt,i​=Gt−1,i​+gt,i2​ Here, Gt,iG\_{t,i}Gt,i​ is the accumulated sum of squared gradients for parameter θi\theta\_iθi​.
4. **Parameter Update:**
   * The parameters are updated using a scaled learning rate: θt+1,i=θt,i−ηGt,i+ϵ⋅gt,i\theta\_{t+1,i} = \theta\_{t,i} - \frac{\eta}{\sqrt{G\_{t,i\}} + \epsilon} \cdot g\_{t,i}θt+1,i​=θt,i​−Gt,i​​+ϵη​⋅gt,i​
     * η\etaη is the initial learning rate.
     * Gt,iG\_{t,i}Gt,i​ is the accumulated sum of squared gradients.
     * ϵ\epsilonϵ is a small constant added for numerical stability to avoid division by zero.

#### Key Features:

* **Adaptive Learning Rate:**
  * AdaGrad adapts the learning rate for each parameter based on the magnitude of its gradients. Parameters with large gradients receive smaller updates, and those with small gradients receive larger updates. This helps in converging faster and can be particularly useful for sparse data where some features are rarely updated.
* **Learning Rate Diminishing:**
  * A drawback of AdaGrad is that the learning rate diminishes over time because the accumulated sum of squared gradients Gt,iG\_{t,i}Gt,i​ only increases or remains the same. This can cause the learning rate to become very small, leading to slow convergence or even stopping the learning process.

#### Summary:

AdaGrad is effective in scenarios where the features of the data are sparse or vary in frequency. However, it can struggle with diminishing learning rates over time. Despite this, it laid the foundation for more advanced algorithms like RMSProp and Adam, which address this limitation.
