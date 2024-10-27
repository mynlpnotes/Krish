# Multicollinearity

* Plot the variables against each other and see if there is a relationship – scatter matrix
*   Same can be achieved using pandas profiling – pearson graph

    OR
* Variance inflation factor
* VIF = 1 / ( 1 – R2)
* If VIF > 10 then it is to be considered that dataset is multicollinear, if R2 is 0.9 then VIF will become 10
* If we plot tv vs radio and if the line is able to explain 90% of the variance then it means they are multi collinear

```python
from statsmodels.stat.outliers_influence import variance_inflation_factor
[variance_inflation_factor(arr,i) for i in range(arr.shape[i])]
```

*

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

**Solution:**

* Remove 1 column or use dimension reduction like pca or LDS
