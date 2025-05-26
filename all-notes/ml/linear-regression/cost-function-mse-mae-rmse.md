# Cost Function - MSE, MAE, RMSE

<mark style="color:purple;background-color:purple;">**Metrics for error w.r.t each and every point**</mark>

*

    <figure><img src="../../../.gitbook/assets/image (418).png" alt=""><figcaption></figcaption></figure>

**MSE:**

*

    <figure><img src="../../../.gitbook/assets/image (420).png" alt="" width="368"><figcaption></figcaption></figure>
* <mark style="color:purple;background-color:purple;">**Its a quadratic equation**</mark>
*

    <figure><img src="../../../.gitbook/assets/image (419).png" alt="" width="375"><figcaption></figcaption></figure>
* If we see the image of graph of a quadratic equation, then it will help us to reach minima

| Advantage                                                                                              | Disadvantage                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| It is differentiable at all points                                                                     | <mark style="color:purple;background-color:purple;">**Not robust to outliers**</mark> - If we add an outlier, then the best fit line will shift more towards the outlier |
| <mark style="color:purple;background-color:purple;">**It has only local and one global minima**</mark> | y will be in some unit, so when we calculate MSE, then we are changing the units as we are squaring the error                                                            |
| <mark style="color:purple;background-color:purple;">**Its a convex function**</mark>                   |                                                                                                                                                                          |
| Converges faster                                                                                       |                                                                                                                                                                          |



**MAE:**

* &#x20;![](<../../../.gitbook/assets/image (435).png>)
*

    <figure><img src="../../../.gitbook/assets/image (436).png" alt="" width="199"><figcaption></figcaption></figure>
* If we check the plot of MAE, then it will be passing through 0
* And at 0 it wont be differentiable
* So we create sub gradients, we will be taking a part of plot and get gradient

| Advantage                                                                                                                 | Disadvantage                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <mark style="color:purple;background-color:purple;">**Robust to outliers**</mark> - Since we are not penalizing the error | Convergence takes more time. Optimization is a complex task - As subgradients have to be calculated |
| It will be in same unit                                                                                                   |                                                                                                     |
|                                                                                                                           |                                                                                                     |



**RMSE:**

* &#x20;Square root of MSE

| Advantage           | Disadvntage                                                                           |
| ------------------- | ------------------------------------------------------------------------------------- |
| Same unit as output | <mark style="color:purple;background-color:purple;">**Not robust to outliers**</mark> |
| Differentiable      |                                                                                       |
|                     |                                                                                       |



* We will be calculating all 3 metrics and check for model metrics r2 and adj. r2
* All this combine will form our performance matrix

When to use MSE vs MAE vs RMSE



When to use r2 vs adj. r2
