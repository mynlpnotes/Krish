# Logit

**Definition:**

* <mark style="color:purple;background-color:purple;">**The logit function is defined as the natural logarithm of the odds of a probability**</mark>: \[ $$\text{logit}(p) = \log\left(\frac{p}{1 - p}\right)$$ ] where ( p ) is the probability of the event occurring.

**Purpose**

* The logit function transforms probabilities (which range from 0 to 1) into **log-odds**, which can range from (- $$\infty$$) to (+ $$\infty$$). This allows us to <mark style="color:purple;background-color:purple;">**model a linear relationship between predictors and the outcome.**</mark>

**Why Use Logit?**

* **Linear Relationship**: Logistic regression aims to <mark style="color:purple;background-color:purple;">**find a linear relationship between predictors (features) and the log-odds of the outcome.**</mark>
* **Easier Interpretation**: Log-odds <mark style="color:purple;background-color:purple;">**allow us to interpret the effect of predictors on the odds of the event occurring in a straightforward manner.**</mark>

**Steps in Logistic Regression**

1. **Data Preparation**:
   * Collect data with predictors (e.g., age, income) and binary outcomes (e.g., purchased: yes/no).
2. **Calculate Probabilities**:
   * Estimate probabilities of the outcome for different values of predictors.
3. **Calculate Odds**:
   * Use the formula: \[ $$\text{odds} = \frac{p}{1 - p}$$ ]
4. **Calculate Log-Odds**:
   * Transform the probabilities into log-odds using the logit function: \[ $$\text{logit}(p) = \log\left(\frac{p}{1 - p}\right)$$ ]
5. **Fit the Logistic Regression Model**:
   * Use statistical software to fit a model that estimates coefficients (intercept ( $$\beta_0$$) and slopes ( $$\beta_1$$)) for predictors.
6. **Predict Probabilities**:
   * Use the fitted model to predict probabilities for new data: \[ $$p = \frac{1}{1 + e^{-(\beta_0 + \beta_1 \times \text{Age})}}$$ ]

**Example**

* For an age of 30 with a predicted probability of purchasing of 0.6:
  * Odds: \[ $$\text{odds} = \frac{0.6}{0.4}$$ = 1.5 ]
  * Log-Odds: \[ $$\text{logit}(0.6) = \log(1.5) \approx 0.41$$ ]

**Important Concepts**

* **Odds**: The ratio of the probability of the event occurring to the probability of it not occurring.
* **Sigmoid Function**: The inverse of the logit function, used to convert log-odds back to probabilities: \[ $$p = \frac{1}{1 + e^{-\text{logit}}}$$ ]
