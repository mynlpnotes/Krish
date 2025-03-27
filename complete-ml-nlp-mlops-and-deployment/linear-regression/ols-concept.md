# 🟢 OLS Concept

* Ordinary Least Squares (OLS) is a method used to <mark style="color:purple;background-color:purple;">**find the best-fit line by minimizing the sum of squared differences between the actual and predicted values.**</mark>
* OLS estimates the coefficients (β) for all features simultaneously <mark style="color:purple;background-color:purple;">**using the closed-form equation**</mark>: β = (XᵀX)⁻¹ Xᵀy.
* OLS assumes each feature may or may not have a significant effect on the target variable.
* For each feature, we perform hypothesis testing to evaluate the significance of its coefficient.
* <mark style="color:purple;background-color:purple;">**The null hypothesis (H₀): β = 0, meaning the feature has no impact on the dependent variable.**</mark>
* <mark style="color:purple;background-color:purple;">**The alternative hypothesis (H₁): β ≠ 0, meaning the feature does impact the dependent variable.**</mark>
* The p-value measures the probability of observing the estimated coefficient (or something more extreme) if the null hypothesis is true.
* <mark style="color:purple;background-color:purple;">**If p-value < 0.05, we reject the null hypothesis and conclude the feature is statistically significant, so we keep it.**</mark>
* <mark style="color:purple;background-color:purple;">**If p-value > 0.05, we fail to reject the null hypothesis and consider removing the feature because it is not statistically significant.**</mark>
* OLS uses a closed-form solution that requires matrix inversion (XᵀX)⁻¹, which becomes computationally expensive and slow for large datasets.
* When dealing with large datasets or many features, regularization techniques can be used instead of relying solely on OLS p-values for feature selection.

