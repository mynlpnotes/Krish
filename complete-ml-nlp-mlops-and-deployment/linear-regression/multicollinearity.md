# Multicollinearity

* <mark style="color:purple;background-color:purple;">**Plot the variables against each other and see if there is a relationship – scatter matrix**</mark>
*   Same can be achieved using pandas profiling – pearson graph

    OR
* <mark style="color:purple;background-color:purple;">**Variance inflation factor**</mark>
* <mark style="color:purple;background-color:purple;">**VIF = 1 / ( 1 – R2)**</mark>
* <mark style="color:purple;background-color:purple;">**If VIF > 10 then it is to be considered that dataset is multicollinear, if R2 is 0.9 then VIF will become 10**</mark>
* <mark style="color:purple;background-color:purple;">**If we plot tv vs radio and if the line is able to explain 90% of the variance then it means they are multi collinear**</mark>

```python
from statsmodels.stat.outliers_influence import variance_inflation_factor
[variance_inflation_factor(arr,i) for i in range(arr.shape[i])]
```

*

    <figure><img src="../../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Solution:**

* Remove 1 column or use dimension reduction like PCA or LDS
