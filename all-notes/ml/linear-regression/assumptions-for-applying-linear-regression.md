# 🟢 Assumptions for Applying Linear Regression

1. <mark style="color:purple;background-color:purple;">**Some relation between y and x, specially linear kind**</mark>

* We can plot scatterplot for each x vs y
* We can find coeffecient of correlation of each x with y
* Even if for some variable we find that it is low then also we wont remove it as it might be important i combination with some other variable
* The real decision making happens when we run the regression, check the value of p, calculate VIF

2. <mark style="color:purple;background-color:purple;">**Mean of residual should be 0**</mark>

* It means the model has systematic bias
* It should not happen that the model consistently overpredicts or under predicts
* We check this after fitting the model

3. <mark style="color:purple;background-color:purple;">**Error terms are not supposed to be correlated**</mark>

* We can check this using durbin watson test

4. <mark style="color:purple;background-color:purple;">**X and residual are not supposed to be correlated (also called as exogenity)**</mark>

* We check it by plotting scatterplots of each x with residual
* We can also check coefficient of correlation
* If its related then it means
  * We missed some variable which affects both X and Y
  * Or there is relation y and X
* If we find a relation, we can
  * Add the missing variable which could explain y better
  * Transform the values, x2, log(x), x1\*x2 — this can help to capture non linearities
  * Go for non linear model like polynomial regression, DT etc

5. <mark style="color:purple;background-color:purple;">**Error term must showcase constant variance (Homoscedasticity)**</mark>

* We can plot them
* We can use White's test

6. <mark style="color:purple;background-color:purple;">**There should be no multi collinearity**</mark>

* Otherwise the model will star learning relationship in between the training variables itself
* We can check this using VIF
* If found then&#x20;
  * We can remove one of them
  * Combine them
  * Use regulaization ⇒ So even if you don't drop them their coeffecients will be small

7. <mark style="color:purple;background-color:purple;">**Error terms are supposed to be normally distributed**</mark>

* We can check the same by plotting or by going for Anderson Darling Test
* If its not normally distributed
  * Try to remove outliers
  * Try to transform dependent variables
  * Try non linear models
