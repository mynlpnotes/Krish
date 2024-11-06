# Log loss -ve sign

* <mark style="color:purple;background-color:purple;">**When we use log loss function, we try to minimize the value, but if we don't use -ve sign then the value will be -ve**</mark>
* <mark style="color:purple;background-color:purple;">**And our optimization function will try to further minimize it, so it will become more -ve, so it won't converge**</mark>



1. &#x20;**Log-Likelihood (Without Negative Sign)**

* In logistic regression, we aim to **maximize** the likelihood of the data. The log-likelihood for ( n ) observations is:
* $$[ L = \sum_{i=1}^{n} \left[ y^{(i)} \log(h(x^{(i)})) + (1 - y^{(i)}) \log(1 - h(x^{(i)})) \right] ]$$
* Where:
* ( $$y^{(i)}$$) is the actual label (1 or 0),
* ( $$h(x^{(i)})$$ ) is the predicted probability.

2. **What Happens Without the Negative Sign?**

* If we don’t include the negative sign, we get the **log-likelihood**, which we want to **maximize**. However, most optimization algorithms like gradient descent minimize functions, so it’s not directly usable in standard algorithms.
* **Example:** For data with:
* Observation 1: ( $$y^{(1)} = 1, h(x^{(1)}$$) = 0.9 )
* Observation 2: ( $$y^{(2)} = 0, h(x^{(2)}$$) = 0.2 )
* Observation 3: ( $$y^{(3)} = 1, h(x^{(3)}$$) = 0.7 )
* Log-likelihood calculation:
* $$[ L = \log(0.9) + \log(0.8) + \log(0.7) \approx -0.1054 - 0.2231 - 0.3567 = -0.6852 ]$$
* Without the negative sign, we’re maximizing a negative value, which complicates optimization.

3. **With the Negative Sign:**

* To convert the maximization problem into a **minimization problem**, we take the **negative** of the log-likelihood. This is the **log loss** function:
* $$-[ \text{Log Loss} = -\sum_{i=1}^{n} \left[ y^{(i)} \log(h(x^{(i)})) + (1 - y^{(i)}) \log(1 - h(x^{(i)})) \right] ]$$
* For our example:
* $$[ \text{Log Loss} = -(-0.6852) = 0.6852 ]$$
* Now, the objective is to **minimize** this positive log loss, which aligns with the optimization algorithms used in machine learning.

4. **Why the Negative Sign is Important**

* **Maximization to Minimization**: The negative sign turns the log-likelihood maximization into a log loss minimization, which is compatible with optimization algorithms like gradient descent.
* **Easier Optimization**: Minimizing the log loss is a standard process, ensuring that the model parameters are adjusted to give predictions close to the actual labels.
