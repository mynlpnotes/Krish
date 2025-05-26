# 🟠 White's Test

1. **To check constant variance**
2. **Run your regression model** and get the residuals (errors).
3. **Square the residuals**, because we are interested in the **variance**.
4. <mark style="color:purple;background-color:purple;">**Regress these squared residuals on:**</mark>
   * <mark style="color:purple;background-color:purple;">**The original independent variables**</mark>
   * <mark style="color:purple;background-color:purple;">**Their squares**</mark>
   * <mark style="color:purple;background-color:purple;">**Their cross products (interaction terms)**</mark>
5. <mark style="color:purple;background-color:purple;">**Perform a chi-squared test on the R-squared value from this auxiliary regression.**</mark>
   * <mark style="color:purple;background-color:purple;">**Null hypothesis (H₀): Homoskedasticity (errors have constant variance).**</mark>
   * <mark style="color:purple;background-color:purple;">**Alternative hypothesis (H₁): Heteroskedasticity (errors have non-constant variance).**</mark>

***

#### **Interpreting White’s Test:**

* If the **p-value** is **low** (typically less than 0.05), you **reject** the null hypothesis.
* That means heteroskedasticity **is present**.
* If the p-value is **high**, there’s **no evidence** of heteroskedasticity.
