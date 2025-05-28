# 🟢 Durbin Watson Test

* <mark style="color:purple;background-color:purple;">**The Durbin-Watson (DW) test checks for autocorrelation in the residuals of a regression model.**</mark>
* Autocorrelation means **error terms are correlated** with each other across observations.
* Autocorrelation violates **OLS regression assumptions**, leading to **incorrect standard errors** and **misleading p-values**.
* <mark style="color:purple;background-color:purple;">**DW is typically used for time series data or ordered data after running a regression.**</mark>
* The DW statistic ranges from **0 to 4**.

***

#### ✅ **Durbin-Watson Statistic Interpretation**

| DW Value   | Interpretation                        |
| ---------- | ------------------------------------- |
| 0 to 1     | Strong **positive autocorrelation**   |
| 1 to 1.5   | Moderate **positive autocorrelation** |
| 1.5 to 2.5 | **No autocorrelation** (ideal range)  |
| 2.5 to 3   | Moderate **negative autocorrelation** |
| 3 to 4     | Strong **negative autocorrelation**   |

***

* Formula: ![](<../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)



* <mark style="color:purple;background-color:purple;">**DW ≈ 2 means no autocorrelation.**</mark>
* <mark style="color:purple;background-color:purple;">**DW < 2 suggests positive autocorrelation.**</mark>
* <mark style="color:purple;background-color:purple;">**DW > 2 suggests negative autocorrelation.**</mark>
* Positive autocorrelation is common in **time series models** where residuals follow patterns over time.

```python
from statsmodels.stats.stattools import durbin_watson
dw = durbin_watson(residuals)
print(f'Durbin-Watson statistic: {dw}')
```
